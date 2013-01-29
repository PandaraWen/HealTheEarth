HealTheEarth
=====
版本：0.1  
作者：[文绍斌](mailto:ultraman_wen@sina.com)

本文档用于描述Heal The Earth的客户端接口
******************************
索引
----
* 下行接口
  	* 	[灾难列表接口](#灾难列表接口)
  	*	[灾难详情接口](#灾难详情接口)
  	*	[用户拯救历史接口](#用户拯救历史接口)
  	*	[用户信息接口](#用户信息接口)
  	*	[通知接口](#通知接口)
* 上行接口
	*	[登陆接口](#登陆接口)
	*	[献爱心接口](#献爱心接口)
	*	[祝福接口](#祝福接口)
	*	[传播接口](#传播接口)

接口说明
--------

<h2>灾难列表接口</h2>
域名:http://hte4mj.sinaapp.com/api/disaster_timeline
#### 请求参数
	* 灾难提交日期 -- date, 格式为yyyy-mm-dd
	* 页码 -- page，默认为1
	* 单页记录数 -- perpage，默认为7
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data, json数组，返回两个数据
		* data[disasters] -- 灾难列表，具体内容如下
			* disaster_id -- 灾难id
			* content -- 灾难对应微博内容
			* image_url -- 灾难图片
			* latitude -- 灾难发生地点纬度
			* longitude -- 灾难发生地点经度
		* data[count] -- 列表条目数
#### 样例
[↑返回顶部](#HealTheEarth)

<h2>灾难详情接口</h2>
域名:http://hte4mj.sinaapp.com/api/disaster
#### 请求参数
	* 登录用户id -- uid，(可选)
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
			* kind_count -- 献爱心数
			* msg_count -- 祝福数
			* relay_count -- 传播数
			* threshold -- 阀值
			* state -- 拯救是否成功，0：拯救未成功，1：拯救成功
			* healed -- 参与拯救标志（当uid未传入时此字段无意义），0：当前用户已参与拯救，1：当前用户未参与拯救
[↑返回顶部](#Heal The Earth)

<h2>用户拯救历史接口</h2>
域名:http://hte4mj.sinaapp.com/api/healed_timeline
#### 请求参数
	* 要查询的用户id -- uid
	* 页码 -- page，默认值1
	* 单页条数 -- perpage，默认值10
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 结果 -- data, json数组，本操作返回两个数据
		* data[healeds] -- 拯救行为信息，具体内容如下
			* disaster_id -- 灾难id
			* operation -- 拯救类型，0：献爱心；1：祝福；2：传播
			* date -- 拯救日期
			* state -- 拯救是否成功，0：拯救未成功，1：拯救成功
		* data[count] -- 列表条目数
#### 样例
[↑返回顶部](#Heal The Earth)

<h2>用户信息接口</h2>
域名:http://hte4mj.sinaapp.com/api/user
#### 请求参数
	* 目标用户id -- uid
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 返回结果 -- data，条目字段如下
		* uid -- 用户id
		* heal_point -- 持有拯救分
		* level -- 等级
#### 样例
[↑返回顶部](#Heal The Earth)

<h2>通知列表接口</h2>
域名:http://hte4mj.sinaapp.com/api/notice_timeline
#### 请求参数
	* 目标用户id -- uid
	* 页码 -- page，默认值1
	* 单页记录数 -- perpage，默认值10
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
	* 返回结果 -- data，json数组，返回两个数据
		* data[notices]，通知列表，具体内容如下
			* content -- 通知内容
			* date -- 通知发出日期
		* data[count] -- 列表条目数
#### 样例
[↑返回顶部](#Heal The Earth)

<h2>登陆接口</h2>
域名:http://hte4mj.sinaapp.com/api/new_account
说明：客户端授权成功后以授权用户uid作为请求参数
#### 请求参数
	* 目标用户id -- uid
#### 返回字段
	* error_code -- 错误代码
	* error_msg -- 错误信息
#### 样例
[↑返回顶部](#Heal The Earth)

<h2>献爱心接口</h2>
域名:http://hte4mj.sinaapp.com/api/kind
#### 请求参数
	* 用户id -- uid
	* 灾难id -- disaster_id
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
#### 样例
[↑返回顶部](#Heal The Earth)

<h2>祝福接口</h2>
域名:http://hte4mj.sinaapp.com/api/msg
#### 请求参数
	* 用户id -- uid
	* 灾难id -- disaster_id
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
#### 样例
[↑返回顶部](#Heal The Earth)

<h2>传播接口</h2>
域名:http://hte4mj.sinaapp.com/api/relay
#### 请求参数
	* 用户id -- uid
	* 灾难id -- disaster_id
#### 返回字段
	* 错误码 -- error_code
	* 错误信息 -- error_msg
#### 样例
[↑返回顶部](#Heal The Earth)
