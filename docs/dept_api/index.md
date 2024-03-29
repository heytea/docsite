# UPMS提供给第三方系统获取组织信息API
- **请求URL**
> [/api/service-staff/signapi/v2/dept](#)
- **请求方式**
>**POST**

- **请求参数**

| 参数名        | 参数类型         | 是否必填 | 参数说明                                                                                               | 示例                                     |
|:-----------|:-------------|:-----|:---------------------------------------------------------------------------------------------------|:---------------------------------------|
| clientId   | String       | 是    | 喜茶分配给第三方的client Id                                                                                 | exampleClientId                        |
| timestamp  | String       | 是    | 请求时间戳（东八区）用于做请求时效验证，单位：秒                                                                           | 1600412480                             |
| sign       | String       | 是    | 签名结果                                                                                               | dFCBnsgzv/2h...                        |
| payload    | Object       | 是    | 请求正文                                                                                               |  |
| --cursorId         | Long         | 否    | 查询的id (默认按id排序获取1000条数据,传具体id数据查询大于该id的数据)                                                         | 1                                      |
| --size     | integer      | 否    | 查询的条数(默认值1000,限制最大为1000)                                                                           | 1000                                   |
| --source   | String       | 是    | 数据来源（E_ROAD->EHR系统，PRM->事业合伙人）                                                                     | E_ROAD                                 |
| --selector | List<String> | 否    | 查询字段集(id,deptCode,outDeptCode,deptName,ifStore,parentDeptCode,status,financialBusinessCode,source) |                                    |
| --lastUpdatedTimeStart | String       | 否    | 适用于增量更新场景的数据获取，每次从上一次的更新时间往后增量拉取数据。格式： yyyy-MM-dd HH:mm:ss                                              | 2023-10-10 00:00:00 |
| --lastUpdatedTimeEnd   | String       | 否    | 根据修改时间筛选 end 格式： yyyy-MM-dd HH:mm:ss                                                                    | 2023-10-10 00:00:00 |

- **请求示例**
```
{
  "cursorId": 1,
  "size": 1000, 
  "source": "E_ROAD",
  "selector": [
    "id",
    "deptCode",
    "outDeptCode",
    "deptName",
    "ifStore",
    "parentDeptCode",
    "status"
  ]
}
```
- **返回示例**

```
"code": 0,
"message": "SUCCESS",
"requestId": null,
"data": [

            {
              "id": 123,
              "deptCode": "123456",
              "outDeptCode":"123456",
              "deptName": "测试组织名称",
              "ifStore": true,
              "parentDeptCode": "1122",
              "status": "ACTIVE",
              "financialBusinessCode":"123456",
              "source":"E_ROAD",
              "lastUpdatedTime":"2023-10-10 00:00:00"
        }
    ]
}
```
- **data的数据类型和字段说明参考**


| 参数名                   | 参数类型    | 参数说明                           | 示例     |
|:----------------------|:--------|:-------------------------------|:-------|
| id	                   | Long    | id                             | 123    |
| deptCode              | 	String | 组织编码                           | 123456 |
| outDeptCode           | 	String | 源系统组织编码                        | 123456 |
| deptName	             | String  | 组织名称                           | 测试组织名称 |
| ifStore	              | String  | TRUE-门店；FALSE-非门店              | true   |
| parentDeptCode        | 	String | 父级组织编码                         | 1122   |
| status                | 	String | ACTIVE-有效；INACTIVE-无效          | ACTIVE |
| financialBusinessCode | 	String | 门店经营代码                         | 123456 |
| source                | String  | 数据来源（E_ROAD->EHR系统，PRM->事业合伙人） | E_ROAD |
| lastUpdatedTime | String        | 最近更新的时间                        | 2023-10-10 00:00:00 |
