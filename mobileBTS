#mobileBTS接口规范
> **Beta:**
> 该API仍处于 Beta 阶段

```
1. 该接口适用对象：中汇进件通APP
2. 该接口实现功能：代理商交易汇总信息查询、结算查询、消息展示
3. 该接口调用规范：采用HTTPS请求与中汇的前置POSP进行通信
```
> **注：**
> 文中所有 `<>` 标注的字段，均需根据你的实际情况替换（无需 `<>` 符号，仅作标注之用）
> 文中所有 `:id` 标注的字段，均需根据该资源的实际 `id` 值替换
> 文中所有 `{x|y|...}` 标注的字段，均需根据你的实际情况用其中一个 `x` 或者 `y`（ `|` 分割）替换

## API 接口地址
```
暂无 # 生产环境
http://mposp.21er.tk:9877 # 测试环境
```

## 标准请求
```sh
curl -X POST \
    http://mposp.21er.tk/<资源路径> \
    # 其他可选参数，参数以键值对呈现...
```

## 标准响应
* 校验通过的情况下  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Wed, 09 Nov 2016 07:18:41 GMT

...body...
```

* 请求Method不被支持的情况下  
```
response:{
    "respCode": "ILLEGAL_ARGUMENT",
    "respMsg": "请求错误, 请稍候再试",
    "respTime": "20161109152150",
    "isSuccess": false
}
```
* 请求参数不正确的情况下 
```
{
    "respCode": "ILLEGAL_ARGUMENT", 
    "respMsg": "缺少参数", 
    "respTime": "20161101202414", 
    "isSuccess": false
}
```
<a id="content-title"></a>
## 功能路径列表
| 资源名称     | 路径                                     | Content-Type         | 请求方式     | 维护人     | 是否需要登录|
|-------------|-----------------------------------------|----------------------|---------------|---------------|---------------|
| 登录| [/user/login](#/user/login)                      | urlencoded           | POST      | 张树彬     | 否   |
| 退出登录| [/user/logout](#/user/logout)                      | urlencoded           | POST      | 张树彬     | 是   |
| 主页汇总信息展示| [/agency/homeInfo](#/agency/homeInfo)                      | urlencoded           | GET |张树彬| 是   |
| 商户列表搜索| [/merchant/list](#/merchant/list)                      | urlencoded           | GET |张树彬| 是   |
| 代理商日交易汇总列表|[/agency/transSummaryList](#/agency/transSummaryList)               | urlencoded        | GET |张树彬| 是   |
| 商户交易信息列表|[/merchant/transList](#/merchant/transList)                      | urlencoded           | GET |张树彬| 是   |
| 代理商结算信息列表|[/agency/settleList](#/agency/settleList)  | urlencoded    | GET |张树彬| 是   |
| 广告|[/manage/banner](#/manage/banner)                      | urlencoded           | GET |张树彬| 是   |
| 图片下载| [/manage/downloadImg](#/manage/downloadImg)                      | urlencoded           | GET   | 张树彬     | 否   |
| 消息列表|[/manage/message](#/manage/message)                      | urlencoded           | GET |张树彬| 是 |
| 消息全部已读|[/manage/messageAllReaded](#/manage/messageAllReaded)             | urlencoded           | POST |张树彬| 是   |
| 消息已读|[/manage/messageReaded/{messageId}](#/manage/messageReaded/{messageId})           | urlencoded           | POST |张树彬| 是  |
| 获取IOS最低版本的参数|[/manage/getForceUpdate](#/manage/getForceUpdate)           | urlencoded           | GET |张树彬| 是  |
----------------------------------------------------------------------------------
##### [返回目录↑](#content-title)
<a id="/user/login"></a>
### 登录  /user/login
#### 1\. 代理商账号登录
请求：  
```
POST /user/login HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"loginName": "18911156118"
"passwd": "qqqqqq"(SHA1加密)
"appVersion": "android.ZFT.1.2.143"
```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Set-Cookie: JSESSIONID=8A0A4D013C9D64E69E66D56EAEB776FC; Path=/; HttpOnly
WSSESSION: 8A0A4D013C9D64E69E66D56EAEB776FC-70
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:41:55 GMT

{
    "respTime": "20161110174155", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "登录成功"
}
```

##### [返回目录↑](#content-title)
<a id="/user/logout"></a>
### 
/user/logout
#### 1\. 退出登录
请求：  
```
POST /user/logout HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:43:02 GMT

{
    "respTime": "20161110174302", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "退出成功"
}
```

##### [返回目录↑](#content-title)
<a id="/agency/homeInfo"></a>
### 
/agency/homeInfo
#### 1\. 主页汇总信息展示
请求：  
```
GET /agency/homeInfo HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:44:25 GMT

{
    "respTime": "20161110174425", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "homeInfo": {
        "todayTransMoney": 100, //交易总额(单位元)
        "merchantCount": 5000, //商户数量
        "payInTimeMerchantCount": 10, //D0商户数量
        "updateTime": "16:00" //更新时间
    }
}
```

##### [返回目录↑](#content-title)
<a id="/merchant/list"></a>
### 
/merchant/list
#### 1\. 商户列表搜索
请求：  
```
GET /merchant/list HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"searchType": 0, //搜索类型(0:全部, 1:商户编号, 2:商户名称)
"searchText": "杂货铺",//搜索文本(非必传)
"pageSize":10,//每页展示的条数(非必传)
"lastId":10,//最后一条的id(非必传)
"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:45:30 GMT

{
    "respTime": "20161110174530", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "isLoadComplete": true,//是否加载完成
    "merchantList": [
        {
            "merchantNo": "Z08000000000005", //商户m编号
            "merchantName": "小张杂货铺", //商户名称
            "merchantStatus": "正常", //商户状态
            "linkman": "张三", //联系人
            "phone": "15801376998", //联系电话
            "address": "青年路你强哥",//地址
            "mId":1//唯一标识
        }, 
        {
            "merchantNo": "Z08000000000006", 
            "merchantName": "小张杂货铺", 
            "merchantStatus": "正常", 
            "linkman": "张三", 
            "phone": "15801376998", 
            "address": "青年路你强哥",
            "mId":2//唯一标识
        }
    ]
}
```

##### [返回目录↑](#content-title)
<a id="/agency/transSummaryList"></a>
### 
/agency/transSummaryList
#### 1\. 代理商日交易汇总列表
请求：  
```
GET /agency/transSummaryList HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"searchType": 0, //搜索类型(0:全部, 1:商户编号, 2:商户名称)
"searchText": "杂货铺",//搜索文本(非必传)
"pageSize":10,//每页展示的条数(非必传)
"startTime":"2016-11-15",//开始时间(非必传)
"endTime":"2016-11-15",//结束时间(非必传)
"lastId":10,//最后一条的id(非必传)
"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:46:15 GMT

{
    "respTime": "20161110174615", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "isLoadComplete": true,//是否加载完成
    "transSummaryList": [
        {
            "merchantNo": "Z08000000000005", //商户编号
            "merchantName": "小张杂货铺", //商户名称
            "transTotal": 100, //累计交易笔数
            "transMoneySum": 100000000,//累计交易总额(单位：元)
            "tId": 11111//唯一标识
        }, 
        {
            "merchantNo": "Z08000000000006", 
            "merchantName": "小张杂货铺", 
            "transTotal": 100, 
            "transMoneySum": 100000000,
            "tId": 11112//唯一标识
        }
    ]
}
```

##### [返回目录↑](#content-title)
<a id="/merchant/transList"></a>
### 
/merchant/transList
#### 1\. 商户交易信息列表
请求：  
```
GET /merchant/transList HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"merchantNo": "杂货铺",//商户号
"transType":0,//交易类型(0:"全部", 1:"预授权完成", 2:消费)
"pageSize":10,//每页展示的条数(非必传)
"startTime":"2016-11-15",//开始时间(非必传)
"endTime":"2016-11-15",//结束时间(非必传)
"lastId":10,//最后一条的id(非必传)
"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:47:52 GMT

{
    "respTime": "20161110174751", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "isLoadComplete": true,//是否加载完成
    "transList": [
        {
            "merchantNo": "Z08000000000005", //商户编号
            "merchantName": "小张杂货铺",  //商户名称
            "transNo": "1000001", //交易i编号
            "transType": "消费", //交易类型
            "transStatus": "完成", //交易状态
            "amount": 100000000, //交易金额(单位:元)
            "transTime": "08:00:00", //交易时间
            "terminalNo": "302554", //终端号
            "bankAccountNo": "621700***1412",//交易卡号
            "tId":1111//唯一标识
        }, 
        {
            "merchantNo": "Z08000000000006", 
            "merchantName": "小张杂货铺", 
            "transNo": "1000001", 
            "transType": "消费", 
            "transStatus": "完成", 
            "amount": 100000000, 
            "transTime": "08:00:00", 
            "terminalNo": "302554", 
            "bankAccountNo": "621700***1412",
            "tId":1112//唯一标识
        }
    ]
}
```

##### [返回目录↑](#content-title)
<a id="/agency/settleList"></a>
### 
/agency/settleList
#### 1\. 代理商结算信息列表
请求：  
```
GET /agency/settleList HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"searchType": 0, //搜索类型(0:全部, 1:商户编号, 2:商户名称)
"searchText": "杂货铺",//搜索文本(搜索类型不为0时必传)
"pageSize":10,//每页展示的条数(非必传)
"startTime":"2016-11-15",//开始时间(非必传)
"endTime":"2016-11-15",//结束时间(非必传)
"lastId":10,//最后一条的id(非必传)
"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:48:39 GMT

{
    "respTime": "20161110174839", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "isLoadComplete": true,//是否加载完成
    "settleList": [
        {
            "merchantId": 11111, //商户Id
            "merchantNo": "Z08000000000006",//商户编号 
            "merchantName": "小张杂货铺", //商户名称
            "agencyName": "恒大", //签约渠道
            "settleTime": "2016-10-11", //结算时间
            "amount": 100000000, //结算金额
            "settlePattern": "T+0", //结算模式
            "settleStatus": "成功",//结算状态
            "sId":1111//唯一标识
        }, 
        {
            "merchantId": 11112, 
            "merchantNo": "Z08000000000007", 
            "merchantName": "小张杂货铺", 
            "agencyName": "恒大", 
            "settleTime": "2016-10-11", 
            "amount": 100000000, 
            "settlePattern": "T+0", 
            "settleStatus": "成功",
            "sId":1112//唯一标识
            
        }
    ]
}
```

##### [返回目录↑](#content-title)
<a id="/manage/banner"></a>
### 
/manage/banner
#### 1\. 广告
请求：  
```
GET /manage/banner HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Nginx
Date: Thu, 09 Apr 2015 11:36:53 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Cache-Control: no-cache
Content-Length: 100

{
    "respTime": "20161102112231", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "head": {
        "total": "3"//广告总条数
    }, 
    "body": [
        {
            "title": "广告位1", //广告名称
            "imageUrl": "http://mposp.21er.tk/downloadImg?fileName=main_home_ad_1.png&appVersion=android.ZFT.1.2.226", //图片路径
            "targetUrl": ""//跳转地址
        }, 
        {
            "title": "广告位1", //广告名称
            "imageUrl": "http://mposp.21er.tk/downloadImg?fileName=main_home_ad_1.png&appVersion=android.ZFT.1.2.226", //图片路径
            "targetUrl": ""//跳转地址
        }, 
        {
            "title": "广告位1", //广告名称
            "imageUrl": "http://mposp.21er.tk/downloadImg?fileName=main_home_ad_1.png&appVersion=android.ZFT.1.2.226", //图片路径
            "targetUrl": ""//跳转地址
        }
    ]
}
```

##### [返回目录↑](#content-title)
<a id="/manage/downloadImg"></a>
### 
/manage/downloadImg
#### 1\. 图片下载
请求：  
```
GET /manage/downloadImg HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"fileName"  : "b500000000620994.png", //图片名称
"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Nginx
Date: Thu, 09 Apr 2015 11:36:53 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Cache-Control: no-cache
Content-Length: 100

{
    流
}
```

##### [返回目录↑](#content-title)
<a id="/manage/message"></a>
### 
/manage/message
#### 1\. 消息列表
请求：  
```
GET /manage/message HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:49:39 GMT

{
    "respTime": "20161110174938", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "body": [
        {
            "content": "就问你怕不怕！！！", //消息内容
            "linkAddress": "", //链接地址
            "title": "进件通内部测试", //消息标题
            "newsId": "575513d784aeddcc333a7a10",//消息id 
            "linkText": "", //链接文本内容
            "hasLink": false, //是否有链接
            "createTimeStr": "20160606140803",//创建时间 
            "businessType": "1", //业务类型
            "newsType": "0", //消息类型(0:公告， 1：通知)
            "isRead": 0//是否已读(0:否， 1：是)
        }, 
        {
            "content": "通知测试之所有", 
            "linkAddress": "", 
            "title": "通知测试之所有", 
            "newsId": "5753d725737f247007d596db", 
            "linkText": "", 
            "hasLink": false, 
            "createTimeStr": "20160605153917", 
            "readTimeStr": "20160605162312", 
            "businessType": "1", 
            "newsType": "1", 
            "isRead": 1
        }, 
        {
            "content": "通知测试之安卓", 
            "linkAddress": "", 
            "title": "通知测试之安卓", 
            "newsId": "5753d711737f247007d596da", 
            "linkText": "", 
            "hasLink": false, 
            "createTimeStr": "20160605153857", 
            "businessType": "1", 
            "newsType": "1", 
            "isRead": 0
        }
    ], 
    "head": {
        "hasUnRead": true, //是否有未读
        "unReadNotice": false, //是否有未读通知
        "unReadBulletin": false, //是否有未读公告
        "totalCount": 3, //总条数
        "readCount": 1, //总已读数
        "unReadCount": 2,//总未读书
        "unReadBulletinCount": 5,//公告未读数
        "unReadNoticeCount": 1 //通知未读数
    }
}
```

##### [返回目录↑](#content-title)
<a id="/manage/messageAllReaded"></a>
### 
/manage/messageAllReaded
#### 1\. 消息全部已读
请求：  
```
POST /manage/messageAllReaded HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"appVersion": "android.ZFT.1.2.143"

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:49:39 GMT

{
    "respTime": "20161110175056", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功"
}
```

##### [返回目录↑](#content-title)
<a id="/manage/messageReaded/{messageId}"></a>
### 
/manage/messageReaded/{messageId}
#### 1\. 消息已读
请求：  
```
POST /manage/messageReaded/{messageId} HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

"appVersion": "android.ZFT.1.2.143",
"messageId": "5753d725737f247007d596db"//消息id

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:51:45 GMT

{
    "respTime": "20161110175145", 
    "isSuccess": true, 
    "respCode": "SUCCESS", 
    "respMsg": "成功", 
    "messageId": "1"//消息id
}
```

##### [返回目录↑](#content-title)
<a id="/manage/getForceUpdate"></a>
### 
/manage/getForceUpdate
#### 1\. 获取IOS最低版本的参数
请求：  
```
GET /manage/getForceUpdate HTTP/1.1
Host: mposp.21er.tk
Date: Thu, 03 Dec 2015 10:22:53
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Content-Length: 30

无

```
响应：  
```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Expires: -1
Pragma: no-cache
Content-Type: application/json;charset=UTF-8
Transfer-Encoding: chunked
Date: Thu, 10 Nov 2016 09:51:45 GMT

{
    "respTime": "20161116114419",
    "isSuccess": true,
    "respCode": "SUCCESS",
    "respMsg": "获取成功",
    "minVersion": "1.0.0"
}
```
