# NODE 安装

### step1：下载

node官网：[下载 | Node.js (nodejs.org)](https://nodejs.org/zh-cn/download/)

默认安装或者自定义安装路径     

### step2：查看

打开CMD窗口，执行命令`node -v`查看node版本

执行`npm -v`查看npm版本

```js
npm -v：查看npm安装的版本。
npm init：会引导你建立一个package.json文件，包括名称、版本、作者等信息。
npm list：查看当前目录下已安装的node包。
npm ls：查看当前目录下已安装的node包。
npm install moduleNames：安装Node模块到本地目录node_modules下。
npm install < name > -g：将包安装到全局环境中。
npm install < name > --save：安装的同时，将信息写入package.json中，项目路径中若是有package.json文件时，直接使用npm install方法就能够根据dependencies配置安装全部的依赖包，这样代码提交到git时，就不用提交node_modules这个文件夹了。
npm install < name> --save-dev：安装的同时，将信息写入package.json中项目路径中若是有package.json文件时，直接使用npm install方法就能够根据devDependencies配置安装全部的依赖包，这样代码提交到git时，就不用提交node_modules这个文件夹了。
npm uninstall moudleName：卸载node模块。
```

### step3：环境配置

① 打开安装的目录（默认安装情况下在C:\Program Files\nodejs）（或者自定义路径下）

② 在安装目录下新建两个文件夹【node_global】和【node_cache】

③ 再次打开cmd命令窗口，输入npm config set prefix “你的路径\node_global”

④ npm config set cache “你的路径\node_cache” 可直接复制刚刚新建的空文件夹目录

```
npm config set prefix "E:\KF\nodejs\node_global"
npm config set cache "E:\KF\nodejs\node_cache"
```

⑤设置环境变量，打开【系统属性】-【高级】-【环境变量】，在`系统变量`中新建

```
变量名：NODE_PATH
变量值：C:\Program Files\nodejs\node_global\node_modules
```

⑥ 编辑`用户变量（环境变量）`的 path，将默认的 C 盘下 `APPData\Roaming\npm` 修改成 `C:\Program Files\nodejs\node_global`

⑦ 最后在`Path`里面添加`NODE_PATH`

⑧ 测试，配置完成后，安装个module测试下，咱们就安装最经常使用的express模块，打开cmd窗口，输入以下命令进行模块的全局安装：

⑨ 设置淘宝源

```
npm config set registry https://registry.npmmirror.com/   (淘宝源地址已更换)
```

⑩ 安装 cnpm

```
npm install -g cnpm --registry=https://registry.npmmirror.com
```

express 4.x版本之前  全局安装express 命令是 npm install express -g 

express 4.x版本之后 全局安装express 命令是 npm install -g express-generator













