# 应用中心数据统计接口

### http请求头部参数
|参数|说明|
|----|---------------|
|PARAMS|公共参数，json格式，包括如下：<br>uuid：设备唯一标识<br>imei：机器码<br>version：客户端版本<br>version_code：客户端版本代号<br>device：设备型号<br>channel：渠道别名|

### host地址：
www.dcenter.com

### 请求方式
POST

### body信息（根据事件类型定义post信息字段）
|参数名|类型|说明|
|---|---|---|
|app_center|string|需要提交的数据(json格式)|

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
	"event":"request/request_auto/pause/pause_auto/resume/resume_auto/downloaded/delete/error",
	"page":"YM-XQ",
	"url":"YM-XQ?game_id=102",
	"app_id":"233",
	"app_type":"software/game",
	"reason":"",				// 触发原因
	"size":"1024",				// 如果event事件时中断类型事件（如pause，error）记录本次下载的大小(kb)
	"error":"", 				// String 错误类型
	"error_detail":"",			// String 错误详细信息
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

游戏安装

```
{
	"action_type":"install",
	"event":"install/installed/error",
	"install_mode":"system/auto/root/manual",
	"page":"YM-XQ",
	"url":"YM-XQ?game_id=102",
	"app_id":"233",
	"app_type":"software/game",
	"error":"",
	"error_detail":"",
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

搜索

```
{
	"action_type":"search",
	"page":"YM-XQ",
	"url":"YM-XQ?game_id=102",
	"word":"呵呵",
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```

唤醒事件

```
{
	"action_type":"wake",
	"is_alive":"0/1",		// 是否存活状态，1为是，0为否
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
	"upgrade_type":"must/suggest",
	"event":" request/pause/resume/downloaded/installed/download_error/install_error",
	"install_mode":"system/auto/root/manual",
	"url":"",					// 当不是自动静默升级的情况下，该字段填写触发升级操作的页面地址
	"error":"",
	"error_detail":"",
	"time":1463932744160,
	"net":"wifi/3G/4G"
}
```




