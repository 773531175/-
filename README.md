# -
移动端笔记
1. new Date('2017-10-08 09:00:00') IOS 系统支持：
  ios 8不支持，
  使用正则表达式：.replace(/\-/9,'/');
# 
2.显示不下出现...：
   text-overflow: ellipsis;
    overflow: hidden;
    -webkit-line-clamp: 2;
    display: -webkit-box;
    -webkit-box-orient: vertical;
IOS出现问题：虽然子元素隐藏，但是父元素依然被撑开，解决办法：
在子元素后添加一个伪元素after，设置after
 content: '.';
    	width: 1px;
    	height: 1px;
    	display: block;
    	overflow: hidden;
    	clear: both;
IOS系统为什么这样，原因未知，需要进一步测试。
# 
3.上拉下拉问题：
dropload用户体验不好，采用iscroll做上拉下拉，iscroll ios系统会屏蔽掉touch事件，导致touch事件离开页面后页面检测不到touch事件，页面处于卡顿状态。
解决办法： 当页面检测手指滑动出页面并且页面已下滑到底部时，触发touchend事件。
# 
4.音频播放.m4a格式问题： 
微信中打开音频视频，使用H5标签需要兼容，tinyaudio插件使用还可以，音频播放需要服务端良好的支持。视频直播流IOS只支持m3u8格式，rtmp格式不支持。
# 
5. ios frame的坑：iframe不滚动，
.scroll-wrapper {  
  -webkit-overflow-scrolling: touch;  
 		 overflow-y: scroll;    /* 提示: 请在此处加上需要设置的大小(dimensions)或位置  
                                        (positioning)信息! */  
}  
.scroll-wrapper iframe {  
    /* 你自己指定的样式 */  
}  
iframe 跨域： 同一主域名下，在子页面和父页面添加： document.domain='10jqka,com,cn(主域名)';
iframe 会跳到顶部，iframe中的dom删除添加隐藏等，会是页面重绘，导致iframe页面跳回顶部，跨域情况下目前没有解决方案。
# 
6、position:sticky
# 
7、input number 会出现+-等特殊字符计算输入不出长度；
# 
8、手机ios识别中文容易出现问题；
# 
9、iphone5,iphone5s输入法会挡住页面的50%；
# 
10、input 高度要等于字体大小，否则出现获取焦点时竖线特别长；
# -
11、transform:需要加webkit，不然低版本不支持；
# 
12、fixed ios11 会有问题，很大的问题，
　软键盘唤起后，页面的 fixed 元素将失效（ios认为用户更希望的是元素随着滚动而移动，也就是变成了 absolute 定位），既然变成了absolute，所以当页面超过一屏且滚动时，失效的 fixed 元素就会跟随滚动了。兼容性体验很差，慎用；
建议（1）使用absolute代替，用滚动代替；
（2） 滚动时强制设置位置；
# 
13、ios系统网址需要编码，中文不能识别，需要http或者https协议。
# 
14、垂直居中,超过两行隐藏：
parent:{
position: relative;
 height: 2.4rem;
}
child:{
    overflow: hidden;
    -webkit-line-clamp: 2;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    width: 100%;
    line-height: 1.2rem;
    font-size: .95rem;
    font-weight: 600;
    color: #323232;
    position: relative;
    top: 50%;
    transform: translateY(-50%);
    -webkit-transform: translateY(-50%);
}
