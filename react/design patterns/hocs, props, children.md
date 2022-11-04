Advanced composition in React: cloneElement, HOCs and renderProps

Photo by Mikhail Vasilyev on Unsplash
In this story we’ll have a look at some advanced ways to compose React components, how they work and when to use them.

cloneElement
As you might know, you can pass rendered components through props (that’s what you are doing whenever you use children, anyway 🙂). You can even use that as a neat trick to optimize your components.

Once you get a rendered component, you can pass it new props using React.cloneElement. This way, while it is up to whoever is using your component to decide what to render, you still get to customize the received component.

const SecretNote = ({ pen }) => (
  <span>🕵️‍♀️{React.cloneElement(pen, { text: "this is a secret" })}🕵️‍♀️</span>
);
const RedPen = ({ text }) => <span style={{ color: "red" }}>{text}</span>;
const App = () => <SecretNote pen={<RedPen />} />;
ReactDOM.render(<App />, document.getElementById("app"));

In the example above, SecretNote uses cloneElement to inject a value into an element. SecretNote doesn’t know which component will be used to render its value. It gets a React element via props, it injects its value into that element, and finally it renders it.

The App component renders SecretNote and passes it a <RedPen /> element. This is a way of delegating the rendering of part of a component to its owner (SecretNote delegates to App how to render its “secret” text).

Prop name contract
This method needs a contract to exist between the component that provides the value and the one that will use it. In the example above, both SecretNote and RedPen use a prop named text. Sometimes this can be a problem, as the component you are cloning might use a different prop name, or use a prop with the same name for a totally different purpose. This means that you’ll need to adapt some components to use this pattern:

import LibraryPen from "some-library";

const SecretNote = ({ pen }) => (
  <span>🕵️‍♀️{React.cloneElement(pen, { text: "this is a secret" })}🕵️‍♀️</span>
);

const AdaptedPen = ({ text }) => <LibraryPen write={text} />;

const App = () => <SecretNote pen={<AdaptedPen />} />;

ReactDOM.render(<App />, document.getElementById("app"));


Higher Order Component
You can use a Higher Order Component to inject values into components. HOCs can be seen as component decorators: you give the HOC a component and it returns a new decorated component, that will render the original component with some additional props injected:

const withSecret = Comp => {
  const WrappedComponent = props => <Comp {...props} text="this is a secret" />;
  return WrappedComponent;
};

const RedPen = ({ text }) => <span style={{ color: "red" }}>{text}</span>;

const AppWithoutSecret = ({ text }) => (
  <span>
    🕵️‍♀️<RedPen text={text} />🕵️‍♀️
  </span>
);

const App = withSecret(AppWithoutSecret);

ReactDOM.render(<App />, document.getElementById("app"));

withSecret is a HOC that, given a component Comp, returns a new component WrappedComponent. This new component renders Comp passing the “secret” text.

Prop name contract
The HOC solution, like the cloneElement one, also needs both the HOC function and the component it wraps to share a common prop name (text in the example). The same problems may arise when using “incompatible” components, and the same fix can be used:

import LibraryPen from "some-library";

const withSecret = Comp => {
  const WrappedComponent = props => <Comp {...props} text="this is a secret" />;
  return WrappedComponent;
};

const AdaptedPen = ({ text }) => <LibraryPen write={text} />;

const AppWithoutSecret = ({ text }) => (
  <span>
    🕵️‍♀️<AdaptedPen text={text} />🕵️‍♀️
  </span>
);

const App = withSecret(AppWithoutSecret);

ReactDOM.render(<App />, document.getElementById("app"))

Render props
A render prop is a function that your component invokes to get a React element, delegating part of its rendering. It’s similar to using cloneElement, but you give the component passing the render prop the ability to dynamically determine how to render:

const SecretNote = ({ renderSecret }) => (
  <span>🕵️‍♀️{renderSecret("this is a secret")}🕵️‍♀️</span>
);

const App = () => (
  <SecretNote
    renderSecret={text => <span style={{ color: "red" }}>{text}</span>}
  />
);

ReactDOM.render(<App />, document.getElementById("app"));

More flexibility
This solution is more flexible than the previous ones. Using a render prop, you don’t have to worry about the “compatibility” between the component accepting the render prop and the component you want to render, because you will be rendering “on demand” when the render prop gets called:

import LibraryPen from "some-library";

const SecretNote = ({ renderSecret }) => (
  <span>🕵️‍♀️{renderSecret("this is a secret")}🕵️‍♀️</span>
);

const App = () => (
  <SecretNote renderSecret={text => <LibraryPen write={text} />} />
);

ReactDOM.render(<App />, document.getElementById("app"));

When to use each solution
As you can see from the previous examples, all three solutions are very similar. In the end, what you can do using a render prop, you also can do using a HOC or cloning an element. For me, which method you use is a matter of API and taste :)

cloneElement
I prefer cloneElement when I am defining a component with a specific UI element which I want to let the user customize. Buttons are a common use case:

const DoubleSidedPanel = ({
  frontPanel,
  backPanel,
  button = <Button size="small" />,
}) => {
  const [frontVisible, setFrontVisible] = useState(true);
  const toggleButton = cloneElement(button, {
    onClick: () => setFrontVisible(!frontVisible),
    children: "Toggle",
  });
  return (
    <div className={frontVisible ? "front" : "back"}>
      {frontVisible ? frontPanel : backPanel}
      {toggleButton}
    </div>
  );
};

const App = () => (
  <DoubleSidedPanel
    frontPanel="Front"
    backPanel="Back"
    button={<Button size="large" />}
  />
);

ReactDOM.render(<App />, document.getElementById("app"));

You can also use cloneElement to inject values into your child components when the parent-child relationship implies a shared API. Libraries like Reach Router do just that.

HOC
Higher Order Components are very useful when you want to provide access to some data or some common behavior in a way that you can compose statically. Or, they were very useful. Nowadays, I’d only create HOCs in applications using React < 16.8.0 🤷‍♂️. Also, they have some caveats.

Before Hooks, a typical usage of HOCs was sharing some complex behavior, usually involving some local state handling and/or lifecycle methods:


const injectWindowSize = Comp =>
  class extends React.Component {
    state = { width: undefined, height: undefined };
    handleResize = () =>
      this.setState({
        width: window.outerWidth,
        height: window.outerHeight,
      });
    componentDidMount() {
      window.addEventListener("resize", this.handleResize);
      this.handleResize();
    }
    componentWillUnmount() {
      window.removeEventListener("resize", this.handleResize);
    }
    render() {
      const { width, height } = this.state;
      return <Comp {...this.props} size={{ width, height }} />;
    }
  };

const Box = ({ size }) => (
  <div>
    {size.width} x {size.height}
  </div>
);

const BoxWithWindowSize = injectWindowSize(Box);

ReactDOM.render(<BoxWithWindowSize />, document.getElementById("app"));

(If you want to learn more about Hooks, and how they can replace HOCs, check 
Ceci García García
’s latest stories).

render props
Render props give the user of your component total freedom when it comes to decide the way a part of your component is rendered. You could achieve the same effect using cloneElement, but cloneElement forces you to define and use a “fully fledged” component. What if you just want to add a simple wrapper around other component, or show two components side by side, without extracting any of that UI elements to its own component?

A render prop is almost like an anonymous React component… but it’s still not a component, as React just sees the result of calling it: a bunch of elements. Take the example we used when we talked about cloneElement:

const SecretNote = ({ pen }) => (
  <span>🕵️‍♀️{React.cloneElement(pen, { text: "this is a secret" })}🕵️‍♀️</span>
);

const RedPen = ({ text }) => <span style={{ color: "red" }}>{text}</span>;

const App = () => <SecretNote pen={<RedPen />} />;

ReactDOM.render(<App />, document.getElementById("app"));

Here React sees the following tree (notice the RedPen component):

![Alt text](file:///1_D6ady3OS3rSMSccouuGY5w.png)

Component tree when using cloneElement
But when you use the render prop:

const SecretNote = ({ renderSecret }) => (
  <span>🕵️‍♀️{renderSecret("this is a secret")}🕵️‍♀️</span>
);

const App = () => (
  <SecretNote
    renderSecret={text => <span style={{ color: "red" }}>{text}</span>}
  />
);

ReactDOM.render(<App />, document.getElementById("app"));

React sees the following tree (no RedPen here):
![Alt text](file:///1_lFfkCPkA2Wid-aX4VjaNiQ.png)

Component tree when using a render prop
When using cloneElement, you have to wrap everything you want to render in a component (RedPen in the example), while the render prop pattern lets you just render what you want, without the need to define additional components. That’s why you should prefer render props when you want to give the developer using your components more freedom and ease of use.

Let’s revisit the DoubleSidedPanel example. Suppose you don’t want to force the usage of something clickable to toggle the panel. You could use a render prop to inject the toggle callback and let the user decide how to use it:

const { useState, cloneElement } = React;

const DoubleSidedPanel = ({ frontPanel, backPanel, renderToggle }) => {
  const [frontVisible, setFrontVisible] = useState(true);
  const toggle = renderToggle(() => setFrontVisible(!frontVisible));

  return (
    <div className={frontVisible ? "front" : "back"}>
      {frontVisible ? frontPanel : backPanel}
      {toggle}
    </div>
  );
};

const App = () => (
  <DoubleSidedPanel
    frontPanel="Front"
    backPanel="Back"
    renderToggle={toggle => (
      <div onMouseEnter={toggle} onMouseLeave={toggle}>
        Move the mouse here to show the back panel
      </div>
    )}
  />
);

ReactDOM.render(<App />, document.getElementById("app"));

Do you use any of this methods? Which one do you prefer? Why?