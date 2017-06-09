
# electron 环境搭建
- 安装 electron 
```
  npm install --g electron
```
-  改变目录owner 权限 【可选】
```
  sudo chown -R 用户名 /usr/local
```

- 安装打包程序 
```
 npm install -g electron-packager
```

- 安装asar 压缩包 
```
 npm install -g asar
```


- 创建项目
```
mkdir TestElectron  
cd TestElectron
npm init
```

- 安装开发环境依赖
```
npm install --save-dev electron
npm install  --save-dev electron-packager
npm install --save-dev asar
```
- 添加 main.js index.html 文件  
	*main.js*   
	**index.html**

- 设置 package.json 启动脚本
```
{
  "name": "testelectron",
  "version": "1.0.0",
  "description": "",
  "main": "main.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "electron .",
    "build": "electron-packager . TestElectron --out=dist --overwrite --ignore=node_modules/electron-* --ignore=node_modules/.bin --ignore=.git --ignore=dist --icon=icon.icns",
    "pack": "asar pack dist/TestElectron-darwin-x64/TestElectron.app/Contents/Resources/app dist/TestElectron-darwin-x64/TestElectron.app/Contents/Resources/app.asar && rm -rf dist/TestElectron-darwin-x64/TestElectron.app/Contents/Resources/app"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "asar": "^0.13.0",
    "electron": "^1.6.10",
    "electron-packager": "^8.7.1"
  },
  "dependencies": {
    "express": "^4.15.3"
  }
}


```
 

- 设置 vscode 启动脚本
```
{
    // 使用 IntelliSense 以学习相关的 Node.js 调试属性。
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Electron Main",
            "runtimeExecutable": "${workspaceRoot}/node_modules/.bin/electron",
            "windows": {
                "runtimeExecutable": "${workspaceRoot}/node_modules/.bin/electron.cmd"
            },
            "program": "${workspaceRoot}/main.js",
            "protocol": "legacy"
        },
    ]
}
```
