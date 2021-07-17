# uniapp小程序自定义tabbar

## 截图

<div align=center>
	<img src="https://github.com/WeiLin-Liao/uniapp-custom-tabbar/blob/master/static/sa3os-5bhqt.gif"/>
</div>

## 使用方法

一、将`uni-custom-tabbar`复制到`components`目录下

目录结构：
>components
>>uni-custom-tabbar
>>>uni-custom-tabbar.vue

二、在`pages.json`中添加`easycom`
```json
"easycom": {
	"autoscan": true,
	"custom": {
		"^uni-(.*)": "@/components/uni-$1/uni-$1.vue"
	}
},

"tabbar": {
	"custom": true
}
```

三、在页面中引入
```vue
<uni-custom-tabbar :current="0"></uni-custom-tabbar>
```
---

## 参数列表

|参数				|说明						|type	|
|---				|---						|---	|
|current			|tabbar索引					|String	|
|paddingBottomHeight|苹果X以上手机底部适配高度		|Number	|

---

## 联系方式
- 📧 电子邮件：2476127622@qq.com
- 🚩 个人博客：<a target="_blank" href="https://weilin-liao.github.io">Reselfs'Blog</a>
- 🐧 QQ交流群：<a target="_blank" href="//shang.qq.com/wpa/qunwpa?idkey=6aa387c1738b5fd614b9971bf976ff3cde84e49f6a918316cf635e83a7c0d418">240491909</a>