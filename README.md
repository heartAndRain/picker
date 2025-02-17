# picker
[![npm](https://img.shields.io/npm/v/react-better-picker.svg?style=flat-square)](https://www.npmjs.com/package/react-better-picker)

移动端最好用的的筛选器组件，高仿 ios 的 UIPickerView ，非常流畅的体验。

## 注意

**先占个坑，未来支持react**

**Not for React Now**

## Fetures
- 支持单列、多列选择
- 支持动态更新每列的数据
- 支持从外部设置选择状态

## 如何使用

### 通过npm引入 ###

安装react-better-picker

```shell
yarn add react-better-picker
```
引入react-better-picker

```javascript
import Picker from 'react-better-picker'
```

>如果不支持import, 请使用

```javascript
var Picker = require('react-better-picker')
```


html 部分：

    <div id="name">点我选择</div>

JS 部分：

    var nameEl = document.getElementById('name');
    
    var data1 = [
    	{
    		text: '小美',
    		value: 1
    	}, {
    		text: '猪猪',
    		value: 2
    	}
    ];
    
    var data2 = [
    	{
    		text: '张三',
    		value: 1
    	},
    	{
    		text: '李四',
    		value: 2
    	},
    	{
    		text: '王五',
    		value: 3
    	},
    	{
    		text: '赵六',
    		value: 4
    	},
    	{
    		text: '吴七',
    		value: 5
    	},
    	{
    		text: '陈八',
    		value: 6
    	},
    	{
    		text: '杜九',
    		value: 7
    	},
    	{
    		text: '黄十',
    		value: 8
    	},
    	{
    		text: '呵呵',
    		value: 9
    	},
    	{
    		text: '哈哈',
    		value: 10
    	},
    	{
    		text: '嘿嘿',
    		value: 11
    	},
    	{
    		text: '啦啦',
    		value: 12
    	}
    ];
    
    var data3 = [
    	{
    		text: '开心',
    		value: 1
    	}, {
    		text: '生气',
    		value: 2
    	},
    	{
    		text: '搞笑',
    		value: 3
    	}, {
    		text: '难过',
    		value: 4
    	}
    ];
    
    var picker = new Picker({
    	data: [data1, data2, data3],
    	selectedIndex: [0, 1, 2],
    	title: '我们都是小学生'
    });
    
    picker.on('picker.select', function (selectedVal, selectedIndex) {
    	nameEl.innerText = data1[selectedIndex[0]].text + ' ' + data2[selectedIndex[1]].text + ' ' + data3[selectedIndex[2]].text;
    })
    
    picker.on('picker.change', function (index, selectedIndex) {
    	console.log(index);
    	console.log(selectedIndex);
    });
    
    picker.on('picker.valuechange', function (selectedVal, selectedIndex) {
    	console.log(selectedVal);
    	console.log(selectedIndex);
    });
    
    nameEl.addEventListener('click', function () {
    	picker.show();
    });

   

### Options
options.title  (String)

筛选器标题，默认为空。

options.data  (Array)

筛选器的数据，是一个二维数组，第一维表示多少列数据，第二维表示每列的数据，单个数据是一个 object，由 text 和 value 两个字段组成，text 表示显示在筛选器的文本，value 表示数据的值。

options.selectedIndex (Array)

筛选器初始化默认选择的数据索引，是一个二维数组，第一维表示列的序号，第二维表示每列的行号，从 0 开始。

### Event
picker.change

当一列滚动停止的时候，会派发 picker.change 事件，同时会传递列序号 index 及滚动停止的位置 selectedIndex。

picker.select

当用户点击确定的时候，会派发 picker.select 事件，同时会传递每列选择的值数组 selectedVal 和每列选择的序号数组 selectedIndex。

picker.cancel

当用户点击取消的时候，会派发picker.cancel事件。

picker.valuechange

当用户点击确定的时候，如果本次选择的数据和上一次不一致，会派发 picker.valuechange 事件，同时会传递每列选择的值数组 selectedVal 和每列选择的序号数组 selectedIndex。

### Method
show (next)

显示筛选器，next 为筛选器显示后执行的回调函数。

hide ()

隐藏筛选器，一般来说，筛选器内部已经实现了隐藏逻辑，不必主动调用。

refill (datas)

重填全部数据，datas为二位数组，如[lists1, lists2, lists3]

refillColumn(index, data)

重填某一列的数据，index为列序号，data为数据数组。

scrollColumn(index, dist)

复位某一列的默认选项，index为列序号，dist为选项的下标，起始值为0

setSelectedIndex(selectedIndex)

设置选择下标

## 如何构建
picker的源码是基于webpack构建的

首先，clone项目源码
```bash
git clone https://github.com/ustbhuangyi/picker.git
```

安装依赖
```bash
cd picker
npm install
```
测试demo页

```bash
npm run dev
```
打开浏览器访问如下地址, 查看效果

> localhost:9090

