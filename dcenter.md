# 应用中心数据统计接口

### http请求头部参数
|参数|说明|
|----|---------------|
|X-Client-Info|公共参数，json格式，包括如下：<br>uuid：设备唯一标识<br>imei：机器码<br>version：客户端版本<br>version_code：客户端版本代号<br>device：设备型号<br>channel：渠道别名|

### host地址：
http://dcenter.ol.ttigame.cn

### 请求方式
POST

### body信息（根据事件类型定义post信息字段）
|参数名|类型|说明|
|---|---|---|
|data|string|需要提交的数据(json格式)|
|source|string|app_center(来源)|

##### 根据事件类型定义不同的json数据
页面浏览数据

```
{
	"action_type":"page_view",
	"page":"YM-XQ",
	"url":"YM-XQ?game_id=102",		// 待详细定义
	"from_page":"YM-JX",
	"time":1463932744160,			// 微秒
	"net":"wifi/3G/4G"
}
```

游戏下载

```
{
	"action_type":"download",
	"event":"request/upgrade/request_auto/pause/pause_auto/
	continue/downloaded/retry/delete/error/
	onekey_request/onekey_retry/onekey_upgrade",//一键下载/一键升级
	"page":"YM-XQ",
	"url":"YM-XQ?game_id=102",
	"app_id":"233",
	"app_type":"software/game",
	"reason":"",				// 触发原因
	"size":"1024",				// 如果event事件时中断类型事件（如pause，error）记录本次下载的大小(byte)
	"error":"", 				// String 错误类型（packageError/netError/memoryError/MD5Error）
	"error_detail":""			//错误详情
	"time":1463932744160,
	"net":"wifi/3G/4G",
	"package_name":"com.lt.cn",
	"ad_type":"wandoujia"  			//广告类型
}
```

游戏安装

```
{
	"action_type":"install",
	"event":"install/installed/error/warn/onekey_install",//新加一键安装事件
	"install_mode":"system/auto/root/normal",
	"page":"YM-XQ",
	"url":"YM-XQ?game_id=102",
	"app_id":"233",
	"app_type":"software/game",
	"error":"",
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

广告位点击

```
{
	"action_type":"click",
	"page":"YM-JX",					// 当前页面
	"url":"YM-XQ?resource_id=102",
	"resource_id":"233",				// 资源id（如游戏id、礼包id等）
	"resource_type":"software/game/gift/topic",
	"p1":"",						// 页面位置
	"p2":"",						// 资源子位置
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

搜索

```
{
	"action_type":"search",
	"page":"YM-XQ",
	"url":"YM-XQ?title="天天游戏中心"",
	"word":"天天游戏中心",
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

唤醒事件

```
{
	"action_type":"wake",
	"is_alive":"true/false",		// 是否存活状态，true为是，false为否
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

推送

```
{
	"action_type":"push",
	"event":"received/clicked",
	"push_id":"12",
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

客户端升级

```
{
	"action_type":"client",
	"from_version":"",				// 版本号
	"to_version":"",				// 版本号
	"upgrade_type":"force/suggest",
	"event":" request/downloaded/install/installed/retry/download_error/install_error",
	"install_mode":"system/auto/root/manual",
	"error_detail":"",			//错误详情
	"error":"", 				// String 错误类型（包体问题/网络/内存不足/MD5不匹配）
	"from":"",					//升级来源（page/notification/service）	
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

启动客户端时上报客户已安装应用信息

```
{
	"action_type":"app_start",
	"app_info":[
		{
			"package":"com.yitian",		// 包名
			"version_name":"1.0.0",
			"version_code":"1000",
			"used_time":"60"			// 使用时长(s)
		},
		{
			"package":"com.yitian",
			"version_name":"1.0.0",
			"version_code":"1000",
			"used_time":"60"
		},
		...
	],
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
 ```

广告位展示

```
{
	"action_type":"ads_view",
	"ads_type":"wandoujia";				//广告来源
	"package_name":"com.lt.appstore"		//包名
	"page":"tj",					//所在页面名称
	"position":"11"，				//所在页面位置
	...
	...
	"time":1463932744160,
	"net":"wifi/3G/4G"
	
}



