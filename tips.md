## 1. 删除
#### 删除空目录
```
rmdir xx
```

#### 删除文件、空目录
```
rm xx
```

#### 删除目录
```
rm -rf xx
```

## 2. 新建
#### 新建目录
```
mkdir x
```

## 3. 解压
#### 将.tar.gz压缩文件解压到xx目录下
```
tar zxvf xx.tar.gz -C xx
```

## 4. 环境变量相关文件
#### 设置临时环境变量
```
export PATH=/xx/xx/.../bin:$PATH
```

#### 当前用户的环境变量
```
vim ~/.profile
在最后添加：
export PATH=/xx/xx/.../bin:$PATH
生效：
source .profile
```

#### 所有用户的全局环境变量
```
vim /etc/profile
在最后添加：
export PATH=/xx/xx/.../bin:$PATH
生效：
source /etc/profile
```

## 5. 包安装删除等相关的命令 dpkg
**语法**

```
dpkg（选项）（参数）
```

**选项**

```
-i：         安装软件包
-r：         删除软件包
-P：         删除软件包，同时删除其配置文件
-L：         显示与软甲包关联的文件
-l：         显示以安装软件包列表
--unpack：   解开软件包
-c：         显示软件包内文件列表
--configure：配置软件包
```

**参数**

```
Deb软件包：制定要操作的.deb软件包
```

**实例**
```
dpkg -i package.deb        #安装包
dpkg -r package            #删除包
dpkg -P package            #删除包（包括配置文件）
dpkg -L package            #列出与该包关联的文件
dpkg -l package            #显示该包的版本
dpkg --unpack package.deb  #解开deb包的内容
dpkg -S keyword            #搜索所属的包内容
dpkg -l                    #列出当前已安装的包
dpkg -c package.deb        #列出deb包的内容
dpkg --configure package   #配置包
```
