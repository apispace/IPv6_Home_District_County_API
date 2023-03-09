# APISpace 介绍
**本 API 服务由 [APISpace（apispace.com）](https://www.apispace.com/?utm_source=github&utm_term=ipv6quxian) 提供。**

APISpace 是 Eolink 旗下专业的 API 开放与交易平台，为广大企业以及个人开发者提供多维度、全方位的API接口，覆盖短信验证、天气查询、快递物流、OCR文字识别等海量 API 服务，帮助用户快速获取数据，降低获取数据的成本和难度，提升开发效率。

APISpace 提供15种开发语言的代码示例，分别是：
- Java(OK HTTP)
- HTTP
- cURL
- 微信小程序
- PHP(pecl_http)、PHP(cURL)
- Python(http.client)、Python(Requests)
- JavaScript(Jquery AJAX)、JavaScript(XHR)
- NodeJS(Native)、NodeJS(Request)
- Ruby(Net:Http)
- Shell(Httpie)、Shell(cUrl)

# IP归属地-IPv6区县级
根据IP地址（IPv6版本）查询归属地信息，包含国家、省、市、区县和运营商等信息。

**使用该产品前，您需要通过 [https://www.apispace.com/eolink/api/ipguishuipv6/introduction](https://www.apispace.com/eolink/api/ipguishuipv6/introduction?utm_source=github&utm_term=ipv6quxian) 申请API服务**

本文档末尾提供了 Python(Requests) 的调用代码示例，可以前往文档末尾查看。

更多代码示例：[https://www.apispace.com/eolink/api/ipguishuipv6/guidence/](https://www.apispace.com/eolink/api/ipguishuipv6/guidence/?utm_source=github&utm_term=ipv6quxian)

### API 版本说明

IPv6归属地分为 **区县级**、**城市级** 共2个版本。

本接口为 **IPv6 归属地 区县级**，查看更多：

-   [IPv6 归属地 城市级](https://www.apispace.com/eolink/api/ipv6city/introduction)

|      | IPv6归属地-区县级                                       | IPv6归属地-城市级                                  |
| ---- | ------------------------------------------------- | -------------------------------------------- |
| 适用人群 | 企业或个人开发者                                          | 企业或个人开发者                                     |
| 数据描述 | ● 2^128全量IPv6 ● 中国地区（不含港台地区）区县级别，定位至区县中心 ● 含运营商数据 | ● 2^128全量IPv6 ● 中国大陆地区（不含港澳台地区）城市级别 ● 含运营商数据 |
| 更新频率 | 每日更新                                              | 每日更新                                         |
| 坐标系  | GPS和百度                                            | GPS和百度                                       |
| 区域类型 | 单区域                                               | 单区域                                          |
| 在线并发 | 1000次/秒                                           | 1000次/秒                                      |


### 应用场景

1.  #### 匿名访客识别，挖掘更多销售线索

用作网站的匿名访客识别，通过解析网站访问用户留存的IP地址，识别访问用户的所属企业、经营地址、官网、联系方式等信息，进而分析来访用户与自身经营业务的匹配程度，挖掘更多的销售线索，辅助业务增长。

2.  #### 建立用户轨迹画像，分析用户需求，辅助产品营销

通过解析已存用户不同登录网站或者APP时间的IP地址，了解用户的地理位置信息，进行用户轨迹画像绘制，通过分析用户常涉区域的经营消费水平，推测用户的理财能力与偏好，根据推导结果进行理财产品匹配，辅助制定营销策略。

3.  #### 互联网在线广告精准投放

对用户进行IP地址解析，了解用户所处的地理位置，同时根据用户所处地理位置的消费水平，对指定半径范围内用户推送适宜的产品。

4.  #### 位置交叉核验，评估用户可信任度

首先根据商户登录的IP地址进行地理位置解析了解用户的真实所处位置，随后利用解析结果与经营注册地址进行匹配校对，判断商户登录位置与经营位置是否一致，作为评估商户可信任程度的风险入参之一。

5.  #### 互联网金融行业风险控制

通过解析用户登录的IP地址了解用户的地理位置位置信息，首先与内部已掌握的风险区域进行数据对比，判断是否发生在高风险地区，同时对同一时间段不同交易用户的IP地址进行解析，了解交易发生地的分布情况，判定是否存在多笔交易发生地聚集，进而辅助内部风控体系建设。

### 返回示例

> ```
> {
>     "code": "Success",
>     "data": {
>         "continent": "亚洲",
>         "country": "中国",
>         "zipcode": "100011",
>         "timezone": "UTC+8",
>         "accuracy": "区县",
>         "owner": "中国教育网",
>         "isp": "中国教育网",
>         "source": "数据挖掘",
>         "areacode": "CN",
>         "adcode": "110105",
>         "asnumber": "23910",
>         "lat": "39.951430",
>         "lng": "116.509342",
>         "radius": "17.3476",
>         "prov": "北京市",
>         "city": "北京市",
>         "district": "朝阳区",
>         "currency_code": "CNY",
>         "currency_name": "人民币"
>     },
>     "charge": true,
>     "msg": "查询成功",
>     "ip": "2001:0250:0211:ffff:ffff:ffff:ffff:4514",
>     "coordsys": "WGS84"
> }
> ```


### 技术原理
![image](https://user-images.githubusercontent.com/36323798/223961409-ea63e1a9-4293-46cd-adff-ca83035038c1.png)

### Python(Requests) 调用代码示例

```
import requests

url = "https://eolink.o.apispace.com/ipguishuipv6/ip/geo/v1/ipv6/district"

payload = {"ip" : "2001:0250:0211:ffff:ffff:ffff:ffff:4514","coordsys" : "WGS84"}

headers = {
    "X-APISpace-Token":"",
    "Authorization-Type":"apikey"
}

response=requests.request("GET", url, params=payload, headers=headers)

print(response.text)

```
