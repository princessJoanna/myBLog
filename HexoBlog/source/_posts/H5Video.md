---
title: h5video
date: 2017-07-08 14:09:17
tags: 
---
临近放假遇到一个活动页面，需求简洁明确：1、视频播放 2、播放到某时间出现按钮点击点转

貌似很简单的功能，用的h5的video，很快做完了。就是，发布到测试，自己手机上测完没毛病。

然后在微信中，发现被禁止自动播放，于是乎加了一段微信的代码
、、、sctript
document.addEventListener("WeixinJSBridgeReady", function onBridgeReady() {
    myPlayer.play();
}
、、、
在自己手机上测试看起来很好的样子，播放到某一进度，加个浮层，点击跳转页面.

然而，在安卓机上，却有两个顽固不化的问题。
第一，自动播放被禁止
第二，点击播放后安卓手机视频自动全屏了。也就是浮层没有办法盖在视频上面。

网上看了很多人遇到同类的问题，但是并没有看到比较好的解决方案。折腾了很久，又请教了比较资深的大牛，说是这个功能实现不了。但是东西要交付，只能硬着头皮做。因为需要比较急，然后我决定不用视频，用动画来做视频效果，做了一个简单的demo，发现累的够呛，毕竟视频时间比较长。然后又采用了帧动画，简单来说就是用定时器切换图片。再加音频，这个时候又遇到音频不能自动播放的问题…
于是又加了一段代码
```javascript
function audioAutoPlay(id) {

    audio = document.getElementById(id),
        play = function () {
            audio.play();
            document.removeEventListener("touchstart", play, false);
        };
    audio.play();
    document.addEventListener("WeixinJSBridgeReady", function () {
        play();
    }, false);

     document.addEventListener("touchstart", play, false);

}
```javascript

音频的问题解决了，但是又发现掉帧的问题，想了下应该是图片加载需要时间，然后所以导致图片没加载出来已经切换到下一帧，所以出现掉帧。
于是加了一段图片预加载的代码
```javascript
```javascript
function getImg() {
var arr = [];
for (var i = 0; i < 2334; i++) {
var img = ‘http://…..’ + i + ‘.jpg’;
arr.push(img);
}
return arr
}
function preloadImg(srcArr) {
if (srcArr instanceof Array) {
for (var i = 1; i < srcArr.length; i++) {
var oImg = new Image();
oImg.src = srcArr[i];
}

    }

}
```javascript
看起来好像已经解决了掉帧的问题，拿自己的手机测试下，貌似没有问题。
然后拿安卓机一看，居然会出现卡顿，甚至跳到某一帧卡住不动。时而好时而卡…
突然间有点绝望…经历了N多次修改，最后还是改回了用video,最终解决了安卓机自动全屏不能放按钮问题，就是增加了两个属性 x5-video-player-type=”h5” x5-video-player-fullscreen=”true” ,要去掉IOS自带的进度条，还要加属性 webkit-playsinline=”true” playsinline=”true” ,
但是增加了属性之后，安卓机上面的控制菜单样式靠近头部，按钮又很小，体验很不好，此时加了一个自定义按钮，设置了样式。将控制菜单隐藏