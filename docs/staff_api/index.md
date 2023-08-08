# UPMS提供给第三方系统获取员工信息API
- **请求URL**
> [/api/service-staff/signapi/v2/staff](#)
- **请求方式**
>**POST**

- **请求参数**

| 参数名       | 参数类型         | 是否必填 | 参数说明                                                                  | 示例                                     |
|:----------|:-------------|:-----|:----------------------------------------------------------------------|:---------------------------------------|
| clientId  | String       | 是    | 喜茶分配给第三方的client Id                                                    | exampleClientId                        |
| timestamp | String       | 是    | 请求时间戳（东八区）用于做请求时效验证，单位：秒                                              | 1600412480                             |
| sign      | String       | 是    | 签名结果                                                                  | dFCBnsgzv/2h...                        |
| payload   | Object       | 是    | 请求正文                                                                  | {"id":1,"size":1000,"source":"E_ROAD"} |
| --id      | Integer      | 是    | 查询的id (默认按id排序获取1000条数据,传具体id数据查询大于该id的数据)                            | 1                                      |
| --size    | integer      | 否    | 查询的条数(默认值1000,限制最大为1000)                                              | 1000                                   |
| --source  | String       | 是    | 数据来源（E_ROAD->EHR系统，PRM->事业合伙人）                                        | E_ROAD                                 |
| --field   | List<String> | 否    | 查询字段集(id,staffCode,jobNumber,name,depts,positions,phoneNumber,status) |                                    |
- **请求示例**
- **返回示例**
- **data的数据类型和字段说明参考**
```
{
"code": 0,
"message": "SUCCESS",
"requestId": null,
"data": [

            {
              
              "id": "123456",
              "staffCode": "ER_T123456",
              "jobNumber": "T123456",
              "name": "张三",
              "depts": [
                "123"
                ,
                "234"
                ],
            "positions": [
                "1",
                "2"
                ],
            "phoneNumber": "18812341234",
            "status": "ON_WORK"

        }
    ]
}

```

| 字段名         | 类型            | 描述                        | 示例            |
|:------------|:--------------|:--------------------------|:--------------|
| id	         | String        | id                        | 123456        |
| staffCode   | 	String       | 员工编码                      | ER_T123456    |
| jobNumber	  | String        | 员工工号                      | T123456       |
| name	       | String        | 用户姓名                      | 张三            |
| depts       | 	List<String> | 用户所属组织                    | ["123","234"] |
| positions   | 	List<String> | 用户岗位                      | ["1","2"]     |
| phoneNumber | 	String       | 用户手机号码                    | 18812341234"  |
| status	     | String        | TERMINATION-离职；ON_WORK-在职 | ON_WORK       |

