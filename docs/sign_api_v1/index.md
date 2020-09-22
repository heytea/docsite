# 协议规则

## API 协议

 - | -
------------ | -------------
传输方式 | HTTPS
数据格式 | JSON 格式，Content-Type: application/json;charset=utf-8
字符编码 | UTF-8
签名算法 | SHA256-RSA
签名要求 | 请求时，必须携带签名
时效要求 | 时效性验证，早于或晚于 5 分钟的请求，将被拒绝

## 请求 Body 参数

字段名 | 类型 | 是否必填 | 描述 | 示例
------- | ------- | ------- | ------- | -------
clientId | String | 是 | 喜茶分配给第三方的 client ID | exampleClientID
timestamp | String | 是 | 请求时间戳（东八区）用于做请求时效验证，单位：秒 | 1600412480
payload | JSON | 是 | 请求正文，业务数据都需要封装在这个字段里面，否则不会参与接口签名验证 | {"order":"3423768327","action":"pay"}
sign | String | 是 | 签名结果  | dFCBnsgzv/2h...








## 签名生成

### 签名生成流程

1. 排序
2. 拼接
3. 计算签名

#### 排序

获取所有公共请求参数，剔除 sign 字段，并按照第一个字符的键值 ASCII 码递增排序（字母升序排序），如果遇到相同字符则按照第二个字符的键值 ASCII 码递增排序，以此类推。

#### 拼接

将排序后的参数与其对应值，组合成“参数=参数值”的格式，并且把这些参数用 & 字符连接起来，此时生成的字符串为待签名字符串。

#### 计算签名

使用对应的SHA256WithRSA签名函数传入商户私钥对待签名字符串进行签名，并进行Base64编码。

### 示例

#### 示例数据
1. clientId = heytea-sample
2. timestamp = 1600413988
3. private-key = MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIB...
4. payload = {"aaa":"dddd"}

#### 排序拼接字符串
待签名字符串
```
clientId=heytea-sample&payload={"aaa":"dddd"}&timestamp=1600414223
```

#### 计算签名

1. 使用SHA256WithRSA传入商户私钥对待签名字符串进行签名
2. 对生成的签名进行Base64编码

Java伪代码
```
String privateKey = "MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIB..."
String strToSign = "clientId=heytea-sample&payload={\"aaa\":\"dddd\"}&timestamp=1600414223"
byte[] signBytes = RSAUtils.SHA256WithRSA(privateKey, strToSign);
String signStr = Base64.getEncoder().encodeToString(signBytes);
```







## 生成RSA密钥

### 安全要求

第三方在生成RSA密钥对后，将公钥提供给喜茶，务必保管好私钥，生产环境密钥对禁止使用在测试环境。

### 使用OpenSSL工具生成

首先进入 OpenSSL 工具，再输入以下命令。

```
OpenSSL> genrsa -out rsa_private_key.pem   2048  #生成私钥
OpenSSL> pkcs8 -topk8 -inform PEM -in rsa_private_key.pem -outform PEM -nocrypt -out rsa_private_key_pkcs8.pem #Java开发者需要将私钥转换成PKCS8格式
OpenSSL> rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem #生成公钥
OpenSSL> exit #退出OpenSSL程序
```

#### 生成后得到密钥
- 私钥：rsa_private_key_pkcs8.pem
- 公钥：rsa_public_key.pem

#### 示例
![OpenSSL Generate RSA Key](../images/openssl_generate_rsa_key.png)










## 自助排查

### 根据喜茶网关返回的message排查

Message | 描述 | 解决方案
---------- | -------- | --------
body empty | 请求体不能为空 | 检查请求体是否为空
client not exists | 商户未配置在喜茶网关 | 检查clientId是否填写错误，联系喜茶开发检查网关是否配置商户
request timestamp too late or early | 请求时效校验错误 | 检查传参时间是否准确
sign uncorrected | 签名验证失败 | 检查密钥配置、签名算法是否有误
unknown system error | 系统错误 | 联系喜茶排查并提供请求参数



