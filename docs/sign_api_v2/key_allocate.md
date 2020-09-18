# 生成RSA密钥

## 安全要求

第三方在生成RSA密钥对后，将公钥提供给喜茶，务必保管好私钥，生产环境密钥对禁止使用在测试环境。

## 使用OpenSSL工具生成

首先进入 OpenSSL 工具，再输入以下命令。

```
OpenSSL> genrsa -out rsa_private_key.pem   2048  #生成私钥
OpenSSL> pkcs8 -topk8 -inform PEM -in rsa_private_key.pem -outform PEM -nocrypt -out rsa_private_key_pkcs8.pem #Java开发者需要将私钥转换成PKCS8格式
OpenSSL> rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem #生成公钥
OpenSSL> exit #退出OpenSSL程序
```

### 生成后得到密钥
- 私钥：rsa_private_key_pkcs8.pem
- 公钥：rsa_public_key.pem

### 示例
![OpenSSL Generate RSA Key](../images/openssl_generate_rsa_key.png)