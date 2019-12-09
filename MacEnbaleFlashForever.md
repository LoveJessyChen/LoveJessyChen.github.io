# Mac永远允许flash启用的政策配置方案 完整版

defaults write com.google.Chrome DefaultPluginsSetting -int "1"
defaults write com.google.Chrome AllowOutdatedPlugins "<true />"
defaults write com.google.Chrome HardwareAccelerationModeEnabled "<true />"
defaults write com.google.Chrome RunAllFlashInAllowMode "<true />"

## ——————————————————————————————————————
defaults write com.google.Chrome PluginsAllowedForUrls -array "https://*"
defaults write com.google.Chrome PluginsAllowedForUrls -array "http://*"

上面这两条只能是添加仅有的单个域名添加方法！！
可以任选一条先添加作为范例，后期容易添加第二条或更多条！！！
## ——————————————————————————————————————

# PluginsAllowedForUrls这条添加多个值需要用以下方法：

## Mac下的Chrome的PluginsAllowedForUrls添加多个值的方法

用finder进入路径：~/Library/Preferences/，
用PrefEdit或Xcode打开com.google.Chrome.plist文件。

然后把PluginsAllowedForUrls 这个字段，分别依次添加两个String类型的值：
"http://*" 、 "https://*" 
不带双引号！！

注意：http放在https前面添加！
