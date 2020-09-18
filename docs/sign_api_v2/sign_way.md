# 签名生成

# 签名生成流程

1. 排序
2. 拼接
3. 计算签名

## 排序

获取所有公共请求参数，剔除 sign 字段，并按照第一个字符的键值 ASCII 码递增排序（字母升序排序），如果遇到相同字符则按照第二个字符的键值 ASCII 码递增排序，以此类推。

## 拼接

将排序后的参数与其对应值，组合成“参数=参数值”的格式，并且把这些参数用 & 字符连接起来，此时生成的字符串为待签名字符串。

## 计算签名

使用对应的SHA256WithRSA签名函数传入商户私钥对待签名字符串进行签名，并进行Base64编码。

## 示例

### 示例数据
1. clientId = heytea-sample
2. timestamp = 1600413988
3. private-key = MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIB...
4. payload = {"aaa":"dddd"}

### 排序拼接字符串
待签名字符串
```
clientId=heytea-sample&payload={"aaa":"dddd"}&timestamp=1600414223
```

### 计算签名

1. 使用SHA256WithRSA传入商户私钥对待签名字符串进行签名
2. 对生成的签名进行Base64编码

Java伪代码
```
String privateKey = "MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIB..."
String strToSign = "clientId=heytea-sample&payload={\"aaa\":\"dddd\"}&timestamp=1600414223"
byte[] signBytes = RSAUtils.SHA256WithRSA(privateKey, strToSign);
String signStr = Base64.getEncoder().encodeToString(signBytes);
```