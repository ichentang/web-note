### 一、nvm安装

下载链接：

https://github.com/coreybutler/nvm-windows/releases

#### 1、安装

自定义安装即可

#### 2、配置

##### （1）配置环境变量（安装时会默认生成）

在用户变量和系统变量中输入：

```json
变量：NVM_HOME      值：nvm路径      eg:  D:\Software\nvm_node\nvm
变量：NVM_SYMLINK   值：nodejs路径   eg:  D:\Software\nvm_node\nodejs
```

##### （2）配置淘宝镜像

nvm目录下的setting文件中加入以下内容：

```json
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

#### 3、打开cmd使用nvm

```
nvm v                       // 显示nvm版本
nvm install 16.16.0  				// 安装16.16.0版的node.js 
nvm use 16.16.0             // 使用16.16.0这个版本
node -v                     // 查看当前node.js的版本
```

#### 4、常用命令

```
nvm off                     // 禁用node.js版本管理(不卸载任何东西)
nvm on                      // 启用node.js版本管理
nvm install <version>       // 安装version版的node.js 
nvm uninstall <version>     // 卸载node.js的命令
nvm ls                      // 显示所有安装的node.js版本
nvm list available          // 显示可以安装的所有node.js的版本
nvm use <version>           // 切换到使用指定的nodejs版本
nvm install stable          // 安装最新稳定版
nvm install                 // 安装最新版本nvm
nvm current                 // 显示当前版本
nvm root [path]             // 设置和查看root路径
```

### 二、NODE.JS环境配置

1. 打开安装的目录（默认安装情况下在`C:\Program Files\nodejs`）（或自定义路径：`D:\Software\nvm_node\nvm\npm` ）

2. 在安装目录下新建两个文件夹`node_global`和`node_cache`

3. 再次打开cmd命令窗口，设置`node_global`和`node_cache`安装路径：


```
npm config set prefix "D:\Software\nvm_node\nvm\npm\node_global"
npm config set cache "D:\Software\nvm_node\nvm\npm\node_cache"
```

4. 设置系统变量，打开【系统属性】-【高级】-【环境变量】，在`系统变量`中新建（提前在`node_global`下创建文件夹`node_modules`）

```
变量名：NODE_PATH
变量值：D:\Software\nvm_node\nvm\npm\node_global\node_modules
```

5. 在系统属性`Path`里面添加`NODE_PATH`

6. 编辑`用户变量（环境变量）`的 path，将默认的 `C:\User\APPData\Roaming\npm` 修改成

```
D:\Software\nvm_node\nvm\npm\node_global
```

7. 测试，配置完成后，安装个module测试下，咱们就安装最经常使用的，打开cmd窗口，输入以下命令进行模块的全局安装：

8. 设置淘宝源

```
npm config set registry https://registry.npmmirror.com/   
```

9. 安装 cnpm

```
npm install -g cnpm --registry=https://registry.npmmirror.com
```

10. npm warn（可以不修改）

打开安装的nodejs文件夹，在`npm`和`npm.cmd`中修改：

```
prefig -g 改为  --location=global
```



















