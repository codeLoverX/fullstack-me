<h1> This supports 4 types of class </h1>

1) in pixels 
px means 1px
m-px m[ x/y/t/b/r/l ]-px 

2) in rem
2^X * 2^Y; X= -1, Y=3
SNIPPETIFY THE BELOW LINES
0, 0.5, 1, 1.5, 2 ... 4 (ALL STEPS OF 0.5 FROM 0 UP TO 4; 0.5*0 TO 0.5*8/ 2^-1* 2^3)
0, 1, 2, 3, 4 ... 12    (ALL STEPS OF 1 FROM 0 UP TO 12; 1*0 TO 1*12)
0, 2, 4, 6, 8 ... 16    (ALL STEPS OF 2 FROM 0 UP TO 16; 2*0 TO 2*8)
0, 4, 8, 12, 16... 64   (ALL STEPS OF 4 FROM 0 UP TO 64; 4*0 TO 4*16)
0, 8, 16, 24, 32... 96   (ALL STEPS OF 4 FROM 0 UP TO 96; 0.5* 0 TO 0.5* 8)
m-0 m[ x/y/t/b/r/l ]-0
<---> summary
SNIPPETIFY THE BELOW LINES
ALL STEPS OF X FROM 0 UP TO 64; 4*0 TO 4*16
STEPS ...UP TO
0.5...4 1...12 2...16 4...64 9...96

3) in auto
m-auto m[ x/y/t/b/r/l ]-auto

4) Using negative values
To use a negative space value, prefix the class name with a dash to convert it to a negative value.
-m-auto -m[ x/y/t/b/r/l ]-auto ;-m-px -m[ x/y/t/b/r/l ]-px ; -m-0 -m[ x/y/t/b/r/l ]-0

<h1> Theme customization </h1>

1) By default, Tailwind’s margin/ padding/ spacing scale uses the default spacing scale. You can customize your spacing scale by editing theme.spacing or theme.extend.spacing in your tailwind.config.js file.

tailwind.config.js
module.exports = {
  theme: {
    extend: {
      spacing: {
        '5px': '5px',
      }
    }
  }
}

2) Alternatively, you can customize just the margin scale by editing theme.margin or theme.extend.margin in your tailwind.config.js file.
For spacing and padding, editing theme.space or theme.extend.space

ailwind.config.js
module.exports = {
  theme: {
    extend: {
      margin/space/padding: {
        '5px': '5px',
      }
    }
  }
}

3) Arbitrary values
If you need to use a one-off margin value that doesn’t make sense to include in your theme, use square brackets to generate a property on the fly using any arbitrary value.

<div class="m-[5px]">
  <!-- ... -->
</div>

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

