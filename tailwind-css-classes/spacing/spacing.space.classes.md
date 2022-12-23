<h1> Themes and classes </h1>

* to learn moore about theme and classeses, go to spacing.margin.classes.md

btw. classes are: 
1) 1 pixel: means 1px space-x-px space-y-px 
2) rem: space-x-[0...96 ] space-y-[0...96 ]  

Tailwind always suggests left 
* space-x is for margin-left; space-y is for margin-top  
    
Reversing children order
space-y-reverse > * + *	--tw-space-y-reverse: 1;
space-x-reverse > * + *	--tw-space-x-reverse: 1;
If your elements are in reverse order (using say flex-row-reverse or flex-col-reverse), use the space-x-reverse or space-y-reverse utilities to ensure the space is added to the correct side of each element.

<h1> LImitations </h1>

Cannot be paired with divide utilities
The space-* utilities are not designed to work together with the divide utilities. For those situations, consider adding margin/padding utilities to the children instead.


