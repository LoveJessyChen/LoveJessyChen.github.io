# html select ios 闪屏,移动端常见的兼容性问题


# 移动端常见的兼容性问题
###### 1. meta 基础知识点如下
```
// 启动或禁用自动识别页面中的电话号码
// 启动或禁用自动识别邮箱地址
// 设置 Web 应用是否以全屏模式运行。
// ios 的 safari 顶端状态条的样式，可选的参数有：default、black、black-translucent
// winphone 系统 a、input 标签被点击时产生的半透明灰色背景怎么去掉
```
###### 2. input 基础知识点如下
```
// input 输入框不可编辑
/* disabled 文本框变灰，通过request.getParameter("name")得不到文本框中的内容
readonly 只是使文本框不能输入，样式没有变化，通过request.getParameter("name")可以得到内容 */
// ios 输入的时候英文首字母的默认大写
// android 上去掉语音输入按钮
input::-webkit-input-speech-button {
display: none
}
// ios系统中元素被触摸时产生的半透明灰色遮罩怎么去掉
a,button,input,textarea{
-webkit-tap-highlight-color: rgba(0,0,0,0;)
-webkit-user-modify:read-write-plaintext-only;
}
/* -webkit-user-modify 这个属性使用需谨慎，副作用就是输入法不再能够输入多个字符
另外，有些机型去除不了，如小米2
对于按钮类，不使用a或者input标签，直接用div标签 */
// 表单元素的默认外观重置
-webkit-appearance:none;
// 修改表单输入框 placeholder 的颜色值
input::-webkit-input-placeholder{color:#ccc;}
input:focus::-webkit-input-placeholder{color:#eee;}
// 注意 placeholder, ios 可以换行，android 不可以
// 禁用 select 默认下拉箭头
select::-ms-expand {display: none;}
// 禁用 radio 和 checkbox 默认样式
input[type=radio]::-ms-check,
input[type=checkbox]::-ms-check {
display: none;
}
// 禁用 PC 端表单输入框默认清除按钮
input[type=text]::-ms-clear,
input[type=tel]::-ms-clear,
input[type=number]::-ms-clear {
display: none;
}
```
###### 3. 部分安装手机 a 标签用作按钮的时候，页面显示空白
解决办法：用 button 标签替换 a 标签
###### 4. 微信禁止、选中文本
```
body {
-webkit-user-select: none;
}
```
###### 5. 禁止 ios 长按时不触发系统的菜单，禁止 ios&android 长按时下载图片(3D Touch或Haptic Touch 功能触发的系统菜单也是这个)
```
.css {
-webkit-touch-callout: none
}
```
###### 6. 移动端字体单位的选择 font-size 选择 px 还是rem
解决办法：
- 需要适配手机设备，使用 px 即可
- 需要适配各种移动设备，使用 rem，例如需要适配 iPhone 和iPad等分辨率差别比较挺大的设备，我们就选择 rem
###### 7. 移动端 click 事件，使屏幕产生 200-300ms 的延迟响应
解决办法：
1. 使用 fastclick.js
2. zepto.js 里面的 tap 事件也可以解决 click 的延迟问题
###### 8. 大屏幕中，图片有时候会变模糊
解决办法：用背景图片替换 img 标签，设计稿切出来的图片长宽保证为偶数，并使用 backgroud-size把图片缩小为原来的 1/2；
例如图片宽高为：100px*100px，那么 css 写法如下：
```
.css{
background:url() no-repeat center center;
background-size: 50px 50px;
width:50px;
height:50px;
}
```
###### 9. 打电话&发短信&发邮件的如何实现
```
// 打电话
打电话给:0755-10086
400-810-6999 转 1034
// 发短信
发短信给: 10086
// 发短信 短信内容 (本人进行测试，多个号码发送短信，功能实现不了，始终给第一个号码发送)
安卓手机：发短信给: 10086
苹果手机：发短信给: 10086
多个号码：发短信给: 10086和10010
发短信给: 10086和10010
// 发邮件
单击这里给peun发电子邮件
// 移动web页面自动探测电话号码：
// 使用wtai协议进行拨打电话：
拨打XXX
将XXX存储至电话簿 
// 在电话号码前加上 + (加号)表示国际号码:
+15110418977
// 地图定位GPS：
me位置 比如：me位置
```
##### 10. 屏幕旋转的事件和样式
```
// 1. 事件
window.orientation，取值：正负90表示横屏模式、0和180表现为竖屏模式；
// 代码判断
window.onorientationchange = function(){
switch(window.orientation){
case -90:
case 90:
alert("横屏:" + window.orientation);
case 0:
case 180:
alert("竖屏:" + window.orientation);
break;
}
}
// 2. 样式
/*竖屏时使用的样式*/
@media all and (orientation:portrait) {
.css{}
}
/*横屏时使用的样式*/
@media all and (orientation:landscape) {
.css{}
}
```
###### 11. H5 audio 和 video 在 ios 和 andriod 中无法自动播放
```
// 需要手动去触发事件来播放
$('.div').one('touchstart',function(){
audio.play()
})
```
###### 12. 阻止用户调整微信浏览器字体大小
```
// ios 管事，android 暂无解决方案
body{
-webkit-text-size-adjust: 100%!important;
}
```
###### 13. 解决 transition 闪屏
```
.css{
/*设置内嵌的元素在 3D 空间如何呈现：保留 3D*/
-webkit-transform-style: preserve-3d;
/*(设置进行转换的元素的背面在面对用户时是否可见：隐藏)*/
-webkit-backface-visibility: hidden;
}
```
###### 14. @-webkit-keyframes 注意
- 以0%开始100%结束，0%的百分号不能去掉
- after和before伪类无法使用动画
###### 15. border-radius 注意
- 不支持%单位
- 三星 Galaxy S4中自带浏览器不支持 border-radius 缩写
- 同时写入 border-radius 和背景色的时候，背景色会溢出到圆角以外部分
###### 16. active兼容处理 , 有时候伪类 :active 失效
```
// 1. body 添加 ontouchstart
// 2. js 给 document 绑定 touchstart 或 touchend 事件
// css
a { color:#ccc;}
a:active{ color:#f0f;}
// html
bar
// js
document.addEventListener('touchstart', function(){}, false);
```
###### 17. 视频，音频获取播放结束后的回调函数－ended
```
$('#video').on('ended',function(){
alert(0);
});
```
###### 18. ios 视频默认全屏播放，如何阻止全屏播放－ webkit-playsinline
```
```
###### 18. 前端 iphonex 适配问题
```
目前有三种方法：
1. 机型适配
通过判断 navigator.userAgent 中的字符串 iphone 和 iphoneX 的设备宽和高
const isIphoneX = () => {
return /iphone/gi.test(navigator.userAgent) && (screen.height == 812 && screen.width == 375)
}
2. 通过媒体查询，判断设备宽高和dpr
@media only screen and (device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) {
background: red;
}
或者
@media only screen and (width: 375px) and (height: 690px){
body {
background: red;
}
}
3. 通过 css3 的 content，设置 viewport-fit=cover
body {
background: grey;
padding-top: constant(safe-area-inset-top);
padding-left: constant(safe-area-inset-left);
padding-right: constant(safe-area-inset-right);
padding-bottom: constant(safe-area-inset-bottom);
}
```

