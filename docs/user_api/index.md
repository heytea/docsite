# UPMS提供给第三方系统通过手机号码获取员工信息API
- **请求URL**
> [/api/serice-upms/signapi/v2/user/detail/mobile](#)
- **请求方式**
>**POST**

- **请求参数**

| 参数名                    | 参数类型   | 是否必填 | 参数说明                     | 示例              |
|:-----------------------|:-------|:-----|:-------------------------|:----------------|
| clientId               | String | 是    | 喜茶分配给第三方的client Id       | exampleClientId |
| timestamp              | String | 是    | 请求时间戳（东八区）用于做请求时效验证，单位：秒 | 1600412480      |
| sign                   | String | 是    | 签名结果                     | dFCBnsgzv/2h... |
| payload                | Object | 是    | 请求正文                     |                 |
| --mobile               | String | 否    | 手机号码                     | 13612341234     |
- **请求示例**
```
{
  "mobile":"13612341234"
}

```
- **返回示例**

```
{
"code": 0,
"message": "SUCCESS",
"requestId": null,
"data": 
            {
              "id": 1,
              "wechatUserid": "1234",
              "dingUserid": "1234",
              "jobNumber": "T123456",
              "name": "张三",
              "englishName": "zhang san",
              "email": "XXX@heytea.com",
              "mobile": "13612341234"
        }
}

```

- **data的数据类型和字段说明参考**

| 字段名             | 类型      | 描述     | 示例             |
|:----------------|:--------|:-------|:---------------|
| id	             | Integer | id     | 1              |
| wechatUserid       | 	String | 微信用户ID | 1234           |
| dingUserid	   | String  | 钉钉用户ID | 1234           |
| jobNumber	      | String  | 员工工号   | T123456        |
| name	           | String  | 用户姓名   | 张三             |
| englishName           | String  | 英文名字   | zhang san      |
| email       | 	String | 邮箱     | XXX@heytea.com |
| mobile   | 	String | 手机号码   | 13612341234    |

