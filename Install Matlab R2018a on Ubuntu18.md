1. 下载Matlab R2018a镜像文件及破解所需文件。链接：[百度网盘](https://pan.baidu.com/s/1AbnGYJMiliwoYHGNydBsFA) 密码: qjag
2. 进入下载后的文件夹，解压Matlab2018aLinux64Crack.tar.gz, 创建一个文件夹Crack来防止解压后的文件
3. 挂载镜像。
```
cd ~
sudo mkdir /media/yourname/MatlabR2018a
sudo mount -t auto -o loop R2018a_glnxa64_dvd1.iso /media/yourname/MatlabR2018a
```
4. 安装
```
cd ~
sudo /media/yourname/MatlabR2018a/install
```
5. 选择默认安装目录 /usr/local
6. 输入安装密钥 09806-07443-53955-64350-21751-41297
7. 安装进程中提示插入iso2，这时候挂载iso2
```
cd ~
sudo mount -t auto -o loop R2018a_glnxa64_dvd2.iso /media/yourname/MatlabR2018a
```
8. 最后安装完成
9. 激活。 复制Crack中license_standalone.lic到安装目录中
```
cd ~/Crack
sudo cp license_standalone.lic /usr/loca/MATLAB/R2018a/licenses
```
10. 复制Crack的R2018a到安装目录
```
cd ~/Crack
sudo cp -r R2018a /usr/local/MATLAB
```
恭喜完成！Big thanks to [Ref1](NO.1) and [Ref2](https://blog.csdn.net/zzc15806/article/details/82313072)
