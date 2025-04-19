## 1、使用 `degit` 生成 `uniapp` 模板（已有模板跳过）
```shell
npx degit dcloudio/uni-preset-vue#vite my-uni-app
```
## 2、安装 `uniapp` 依赖
```shell
npm install
```
## 3、编写你的小程序
## 4、生成 `dist` 目录供微信开发者工具预览
```shell
npm run build:mp-weixin
```
## 5、将 `dist` 目录导入微信开发者工具预览