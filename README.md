小巧的前端七牛上传工具
----------------------

介绍
----
`不依赖任何第三方库`  


如何使用
---------
**客户端**
```javascript
var options = {
	domain: '七牛分配给你的域名',
	tokenUrl: '你的服务器上获取uptoken的访问地址'
}
var ins = new fontQnUper(options);
$('#upload').on('change', function() {
	var file = this.files[0];
	ins.post(file, function(err, result) {
		if (err) {
			console.log(err)
		}
		/*result datas
			{
				hash: "", 
				key: "", 
				imageUrl: ""
			}
		*/
	});
	// 上传进度, total: 一共上传的数据, loaded: 已经上传的数据(bytes)
	ins.progress = function(total,loaded){
         //do something 
    }
});
```

**服务器**

**注意事项**
本人使用的是基于`Meteor`的服务端, 如果你换为Nodejs, 可以改一下配置
-  比如获取json文件的配置  
-  路由配置的修改

**配置文件说明**

>  三个参数, 分别是: `BUCKET_NAME`,	`ACCESS_KEY`, `SECRET_KEY`
就是你定义的空间以及七牛提供给你的访问秘钥