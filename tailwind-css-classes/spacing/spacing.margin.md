
<h1> LImitations </h1>

These utilities are really just a shortcut for adding margin to all-but-the-first-item in a group, and aren’t designed to handle complex cases like grids, layouts that wrap, or situations where the children are rendered in a complex custom order rather than their natural DOM order.

For those situations, it’s better to use the gap utilities when possible, or add margin to every element with a matching negative margin on the parent:

<div class="flow-root">
  <div class="-m-2 flex flex-wrap">
    <div class="m-2 ..."></div>
    <div class="m-2 ..."></div>
    <div class="m-2 ..."></div>
  </div>
</div>
​

