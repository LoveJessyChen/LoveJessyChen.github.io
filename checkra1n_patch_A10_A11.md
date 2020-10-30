# 利用bspatch注入A10和A11的iOS 14.x以上系统的checkra1n越狱支持

## 利用bspatch注入A10和A11的iOS 14.x以上系统的checkra1n越狱支持，但是利用这个方法越狱的时候，A10-A11的设备将不支持开启锁屏密码以及指纹和面容。需在越狱之前关闭锁屏密码，否则不支持用户数据分区的解密，也不读取SEP的内容。

### 以下测试的checkra1n版本是0.11.0 。
现阶段默认支持14.x的硬件是A8(X)-A9(X),此补丁仅添加支持A10-A11的手机或者平板

### 本文下面的机器是iPad 6 WiFi (7,5)


# ——————————————————————————

# bspatch命令的使用方法：

## bspatch oldfile newfile patchfile



# ——————————————————————————

## 1. checkra1n_A11_A10 patch

先到下面的网站下载patch文件：https://github.com/Exploite-d/checkra1n_patch_A10_A11

## 2.然后，把“checkra1n_A11_A10_mac.patch”文件复制到“/Applications/checkra1n.app/Contents/MacOS”目录下面。


## 3. 然后运行“终端”，输入下面的命令。

bspatch /Applications/checkra1n.app/Contents/MacOS/checkra1n /Applications/checkra1n.app/Contents/MacOS/checkra1n-patch /Applications/checkra1n.app/Contents/MacOS/checkra1n_A11_A10_mac.patch

## 4. 最后还需要修复这个文件夹的完整读写权限，仍然是在终端输入下面的命令：

sudo chmod -R 777 /Applications/checkra1n.app/Contents/MacOS

## 5.所有以上的步骤完成之后，我们可以来用终端运行下面的命令开始我们的checkra1n熟悉的越狱步骤。
（需要注意的是我们在终端手动进入CLi的黑屏DFU模式，但是方法和原GUi的界面方法是相同的。）
 
/Applications/checkra1n.app/Contents/MacOS/checkra1n-patch -cs

