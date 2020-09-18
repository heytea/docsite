# 公共请求参数

字段名 | 类型 | 是否必填 | 描述 | 示例
------- | ------- | ------- | ------- | -------
clientId | String | 是 | 喜茶分配给第三方的ID | facebook
timestamp | String | 是 | 请求秒级时间戳（东八区）用于做请求时效验证 | 1600412480
payload | JSON | 是 | 请求正文 | {"order":"3423768327","action":"pay"}
sign | String | 是 | 签名戳 | dFCBnsgzv/2h...
