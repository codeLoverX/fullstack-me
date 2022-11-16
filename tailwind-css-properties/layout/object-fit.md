<h1> Object-fit </h1>

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

