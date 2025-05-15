# Luckysheet 二次开发

## chartMix

`chartMix` 是一个 Luckysheet 图表插件，用于在 Luckysheet 中添加自定义图表。

### 功能修改

修改了官方的 chartMix 插件的`createChart`方法，删除其中随机生成柱状图或折线图逻辑，并增加了`chartType`参数，用于指定图表类型。

### 使用方法

- 确保`NodeJs 14.21.3`
- 运行`npm install`安装依赖
- 运行`npm run lib`打包插件
- 将打包结果`lib/chartmix.umd.min.js`、`chartmix.umd.min.js.map`、`chartmix.css`三个文件复制到`Luckysheet/src/expendPlugins/chart`目录下
  - 注意：**`Luckysheet/src/expendPlugins/chart`目录中还存在一个`plugin.js`文件，不对此文件进行任何操作**
- 切换到`Luckysheet`目录，运行`npm run build`，生成最终的`Luckysheet`包文件

## Luckysheet

### 功能修改

- 修改`fx-editor`公式按钮操作逻辑，单元格不可编辑时不可点击，避免不必要的点击操作触发单元格保护弹窗
- 增加 `hook - rangeDeleteAfter` 钩子，在单元格删除后触发，用于删除选区内容后触发其他操作
- 增加图表相关方法
  - `insertChart` 插入图表
  - `delChart` 删除图表
  - `checkCurrentBoxChange` 交换图表XY轴x显示

### 使用方法

- 确保`NodeJs 14.21.3`
- 运行`npm install`安装依赖
- 运行`npm run build`，生成最终的`Luckysheet`包文件

### 注意事项

打包时，因为`icmes-web`已经引用并定制了`element-ui`，所以删除对`element-ui`的引用，避免重复引用；同时，`icmes-web`引用`luckysheet`地址为`/luckysheet`，所以在打包插件时，修改插件引用的相对路径。
具体表现为: 根据本地运行和打包`icmes-web`需要，切换`src/expendPlugins/chart/plugin.js`中`dependScripts`和`dependLinks`，具体参照注释。
