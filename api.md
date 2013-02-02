拯救地球
==============

版本：0.1  
作者：[文绍斌](mailto:ultraman_wen@sina.com)

本文档用于描述“拯救地球”的客户端接口
******************************
索引
----
* 下行接口
  	* 	[灾难列表接口](#灾难列表接口)
  	*	[灾难详情接口](#灾难详情接口)
  	*	[用户拯救历史接口](#用户拯救历史接口)
  	*	[用户信息接口](#用户信息接口)
  	*	[新通知接口](#新通知接口)
  	*	[通知列表接口](#通知列表接口)
* 上行接口
	*	[登陆接口](#登陆接口)
	*	[献爱心接口](#献爱心接口)
	*	[祝福接口](#祝福接口)
	*	[传播接口](#传播接口)

接口说明
--------

<h2>灾难列表接口</h2>
域名:http://hte4mj.sinaapp.com/api/disaster_timeline?page=1&perpage=7
#### 请求参数
	* 页码 -- page，默认为1
	* 单页记录数 -- perpage，默认为7
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data, json数组，返回两个数据
		* data[disasters] -- 灾难列表，具体内容如下
			* date -- 灾难提交日期
			* disaster_id -- 灾难id
			* content -- 灾难对应微博内容
			* image_url -- 灾难图片
			* latitude -- 灾难发生地点纬度
			* longitude -- 灾难发生地点经度
		* data[count] -- 列表条目数
#### 样例
	{
	    "error_code": 1000,
	    "error_msg": "",
	    "data": {
	        "count": 7,
	        "disasters": [
	            {
	                "content": "2013-01-03，此处…………",
	                "latitude": 41.64007838,
	                "image_url": "http://hte4mj-htedata.stor.sinaapp.com/images/03.jpg",
	                "date": "2013-01-03",
	                "disaster_id": 20,
	                "longitude": 13.0078125
	            },
	            {
	                "content": "2013-01-02，此处发生一起accident",
	                "latitude": 23.32208001,
	                "image_url": "http://hte4mj-htedata.stor.sinaapp.com/images/02%2820130102194543%29.jpg",
	                "date": "2013-01-02",
	                "disaster_id": 19,
	                "longitude": 113.5546875
	            },
	     		……
	        ]
	    },
	}
[↑返回顶部](#拯救地球)

<h2>灾难详情接口</h2>
域名:http://hte4mj.sinaapp.com/api/disaster?disaster_id=20
#### 请求参数
	* 灾难id -- disaster_id
#### 返回值
	* 错误代码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data，json数组，本操作返回一个数据
		* data[disaster] -- 灾难详情，具体内容如下
			* date -- 灾难提交日期
			* latitude -- 灾难点纬度
			* longitude -- 灾难点经度
			* status_id -- 微博id
			* content -- 微博内容
			* image_url -- 微博配图链接
			* kind_count -- 献爱心积分数
			* msg_count -- 祝福积分数
			* relay_count -- 传播积分数
			* threshold -- 阀值
			* state -- 拯救是否成功，0：拯救未成功，1：拯救成功
#### 样例
	{
	    "error_code": 2000,
	    "error_msg": "",
	    "data": {
	        "disaster": {
	            "kind_count": 20,
	            "msg_count": 580,
	            "status_id": 3530113394639088,
	            "relay_count": 30,
	            "longitude": 13.0078125,
	            "content": "2013-01-03，此处…………",
	            "latitude": 41.64007838,
	            "state": 1,
	            "image_url": "http://hte4mj-htedata.stor.sinaapp.com/images/03.jpg",
	            "threshold": 620,
	            "date": "2013-01-03"
	        }
	    },
	}
[↑返回顶部](#拯救地球)

<h2>用户拯救历史接口</h2>
域名:http://hte4mj.sinaapp.com/api/healed_timeline?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08
#### 请求参数
	* 要查询的用户id -- uid
	* api密钥 -- key，用以验证用户身份
	* 页码 -- page，默认值1
	* 单页条数 -- perpage，默认值10
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data, json数组，本操作返回两个数据
		* data[healeds] -- 拯救行为列表，具体内容如下
			* disaster_id -- 灾难id
			* operation -- 拯救类型，0：献爱心；1：祝福；2：传播
			* date -- 拯救日期
			* state -- 拯救是否成功，0：拯救未成功，1：拯救成功
		* data[count] -- 列表条目数
#### 样例
	{
	    "data": {
	        "count": 10,
	        "healeds": [
	            {
	                "date": "2013-02-01",
	                "state": null,
	                "disaster_id": 20,
	                "operation": 0
	            },
	            {
	                "date": "2013-02-01",
	                "state": null,
	                "disaster_id": 19,
	                "operation": 0
	            },
	            ……
	        ]
	    },
	    "error_code": 3000,
	    "error_msg": ""
	}
[↑返回顶部](#拯救地球)

<h2>用户信息接口</h2>
域名:http://hte4mj.sinaapp.com/api/healer?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08
#### 请求参数
	* 目标用户id -- uid
	* api密钥 -- key
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 返回结果 -- data，条目字段如下
		* uid -- 用户id
		* heal_points -- 持有拯救分
		* level -- 等级
#### 样例
	{
	    "data": {
	        "level": 0,
	        "uid": 1978225951,
	        "heal_points": 100003319
	    },
	    "error_code": 9100,
	    "error_msg": ""
	}
[↑返回顶部](#拯救地球)

<h2>新通知接口</h2>
域名:http://hte4mj.sinaapp.com/api/new_notice?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08
#### 请求参数
	* 目标用户id -- uid
	* api密钥 -- key
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 是否有新通知 -- new, 0:没有新通知，1:有新通知
#### 样例
	{
	    "new": 0,
	    "error_code": 8000,
	    "error_msg": ""
	}
[↑返回顶部](#拯救地球)

<h2>通知列表接口</h2>
域名:http://hte4mj.sinaapp.com/api/notice_timeline?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08
#### 请求参数
	* 目标用户id -- uid
	* api密钥 -- key
	* 页码 -- page，默认值1
	* 单页记录数 -- perpage，默认值10
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 返回结果 -- data，json数组，返回两个数据
		* data[notices]，通知列表，具体内容如下
			* id -- 通知id
			* content -- 通知内容
			* date -- 通知发出日期
		* data[count] -- 列表条目数
#### 样例
{
    "data": {
        "count": 6,
        "notices": [
            {
                "content": "您的在2013-01-11拯救过的灾难20于20130201被成功拯救！",
                "date": "2013-02-01",
                "disaster_id": 20,
                "id": 1978225951,
                "readed": 0
            },
            {
                "content": "您的在2013-01-11拯救过的灾难20于20130201被成功拯救！",
                "date": "2013-02-01",
                "disaster_id": 20,
                "id": 1978225951,
                "readed": 0
            },
            ……
        ]
    },
    "error_code": 9000,
    "error_msg": ""
}
[↑返回顶部](#拯救地球)


<h2>登陆接口</h2>
域名:http://hte4mj.sinaapp.com/api/new_account?uid=1978225951
说明：客户端授权成功后以授权用户uid作为请求参数
#### 请求参数
	* 目标用户id -- uid
#### 返回字段
	* error_code -- 错误代码
	* error_msg -- 错误信息
	* key -- api密钥
#### 样例
	{
    	"error_code": 4000,
    	"error_msg": "",
    	"key": "34f0e78d3ec68dce89085e35338b8a08"
	}
[↑返回顶部](#拯救地球)

<h2>献爱心接口</h2>
域名:http://hte4mj.sinaapp.com/api/kind?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08&disaster_id=17
#### 请求参数
	* 用户id -- uid
	* api密钥 -- key
	* 灾难id -- disaster_id
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
#### 样例
	{
	    "error_code": 5000,
	    "error_msg": ""
	}
[↑返回顶部](#拯救地球)

<h2>祝福接口</h2>
域名:http://hte4mj.sinaapp.com/api/msg?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08&disaster_id=16
#### 请求参数
	* 用户id -- uid
	* api密钥 -- key
	* 灾难id -- disaster_id
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
#### 样例
	{
	    "error_code": 6000,
	    "error_msg": ""
	}
[↑返回顶部](#拯救地球)

<h2>传播接口</h2>
域名:http://hte4mj.sinaapp.com/api/relay?uid=1978225951&key=34f0e78d3ec68dce89085e35338b8a08&disaster_id=15
#### 请求参数
	* 用户id -- uid
	* api密钥 -- key
	* 灾难id -- disaster_id
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
#### 样例
	{
	    "error_code": 7000,
	    "error_msg": ""
	}
[↑返回顶部](#拯救地球)
