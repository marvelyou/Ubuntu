### 删除<hr>

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

### 新建

#### 新建目录

```
mkdir x
```

### 解压

#### 将.tar.gz压缩文件解压到xx目录下

```
tar zxvf xx.tar.gz -C xx
```

### 环境变量相关文件

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
