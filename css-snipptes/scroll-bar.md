scrollbar

/* width */

::-webkit-scrollbar {
  width: 5px;
}
/* Track */
::-webkit-scrollbar-track {

  background: blue; 

}
/* Handle */

::-webkit-scrollbar-thumb {

  background: green; 

}
/* Handle on hover */

::-webkit-scrollbar-thumb:hover {

  background: #555; 

}

scrollbar?

For webkit browsers, you can use the following pseudo elements to customize the browser's scrollbar:
::-webkit-scrollbar the scrollbar.
::-webkit-scrollbar-button the buttons on the scrollbar (arrows pointing upwards and downwards).
::-webkit-scrollbar-thumb the draggable scrolling handle.
::-webkit-scrollbar-track the track (progress bar) of the scrollbar.
::-webkit-scrollbar-track-piece the track (progress bar) NOT covered by the handle.
::-webkit-scrollbar-corner the bottom corner of the scrollbar, where both horizontal and vertical scrollbars meet.
::-webkit-resizer the draggable resizing handle that appears at the bottom corner of some elements.

image size, how to fill, but not stretch?

.cover {
  object-fit: cover;
  width: 50px;
  height: 100px;
}
<img src="http://i.stack.imgur.com/2OrtT.jpg" class="cover" width="242" height="363"/>

.container{
    position: relative;
}
.cover {
  object-fit: cover;
  width: 50px;
  height: 100px;
}
<div class="container">
    <img src="http://i.stack.imgur.com/2OrtT.jpg" class="cover" width="242" height="363"/>
</div>

