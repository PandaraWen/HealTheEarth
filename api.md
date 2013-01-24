Heal The Earth
=====
版本：0.1  
作者：[文绍斌](mailto:ultraman_wen@sina.com)

本文档用于描述Heal The Earth的客户端接口
******************************
索引
----
* 下行接口
  	*	[灾难详细信息接口](#灾难详细信息接口)
  	*	[用户拯救历史接口](#用户拯救历史接口)

接口说明
--------

<h2>灾难详细信息接口</h2>
域名http://hte4mj.sinaapp.com/api/disasters_timeline?date=2013-01-02
#### 请求参数
	* 灾难提交日期 -- date, 格式为yyyy-mm-dd
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data, 灾难信息列表,条目字段如下
		* date -- 灾难提交日期
		* content -- 灾难对应微博内容
		* image_url -- 灾难图片
		* kind_count -- 被献爱心累积分数
		* msg_count -- 被留言累积分数
		* relay_count -- 被转发累积分数
		* threshold -- 设定的拯救阀值
		* status_id -- 灾难对应微博id
		* latitude -- 灾难发生地点纬度
		* longitude -- 灾难发生地点经度
#### 样例
	{
		"error_code": "0000",
	    "error_msg": "",
	    "data": [
	        {
	        	"date": "2013-01-02",
	        	"content": "2013-01-02，此处发生一起accident",
	        	"image_url": "http://hte4mj-htedata.stor.sinaapp.com/images/02%2820130102194543%29.jpg",
	            "kind_count": 0,
	            "msg_count": 260,
	            "relay_count": 60,
	            "threshold": 12345,
	            "status_id": 3530109460382137,
	            "latitude": 23.146678,
	            "longitude": 113.368159,
	        }
	    ],
	}
[↑返回顶部](#betit)

<h2>用户拯救历史接口</h2>
域名http://hte4mj.sinaapp.com/api/healing_timeline?uid=1978225951
#### 请求参数
	* 要查询的用户id -- uid
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data, 拯救记录列表,条目字段如下
		* uid -- 用户账号id
		* disaster_id -- 被拯救灾难
		* operation -- 拯救类型，0：献爱心；1：祝福；2：传播
		* date -- 拯救发生日期
#### 样例
	{
		"error_code": "1000",
	    "error_msg": ""
	    "data": [
	        {
	            "date": "2013-01-11",
	            "operation": 1,
	            "disaster_id": 19,
	            "uid": 1978225951
	        },
	        {
	            "date": "2013-01-07",
	            "operation": 1,
	            "disaster_id": 18,
	            "uid": 1978225951
	        },
	        {
	            "date": "2013-01-06",
	            "operation": 1,
	            "disaster_id": 18,
	            "uid": 1978225951
	        }
	    ],
	}
[↑返回顶部](#betit)
