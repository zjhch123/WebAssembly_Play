# Wow! WebAssembly!

## 运行:
1. `git clone https://github.com/zjhch123/WebAssembly_Play.git`
2. `cd WebAssembly_Play`
3. 在当前目录随便启一个服务器

## Env:
1. macOS 10.13.3
2. [emscripten](https://github.com/kripken/emscripten)
3. Chrome 浏览器
4. Xcode CommonLine Tools

## 安装Emscripten时出现的问题:
```
Error downloading URL 'https://github.com/kripken/emscripten/archive/1.37.34.tar.gz': <urlopen error [SSL: TLSV1_ALERT_PROTOCOL_VERSION] tlsv1 alert protocol version (_ssl.c:661)>
```
解决:
1. 打开浏览器，下载[https://github.com/kripken/emscripten/archive/1.37.34.tar.gz]`https://github.com/kripken/emscripten/archive/1.37.34.tar.gz`
2. 将下载好的文件命名改为和链接最后一个/之后的文件名一样，例如这里改成`1.37.34.tar.gz`
3. 将下载好的文件拖入`zips`文件夹里，重新运行安装命令即可

## 将C语言文件编译为WebAssembly:
```
emcc xxx.c -s WASM=1 -Os -o xxxx.js
```
* emcc - 表示使用emcc编译器
* xxx.c - 要编译的文件
* -s WASM=1 - 指定使用WebAssembly
* -Os - 代码优化级别
* -o xxxx.js 输出的文件

## 在浏览器上调用函数:
1. 使用`Module.ccall`
```
Module.ccall(
  'funcName',     // 函数名
  'number',       // 返回类型
  ['number'],     // 参数类型
  [42]);  
```

2. 直接调用
```
// 通过在函数名前添加下划线来调用C函数
const result = _funcName();
```
