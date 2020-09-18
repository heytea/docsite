# 自助排查

## 根据喜茶网关返回的message的含义排查

Message | 描述 | 解决方案
---------- | -------- | --------
body empty | 请求体不能为空 | 检查请求体是否为空
client not exists | 商户未配置在喜茶网关 | 检查clientId是否填写错误，联系喜茶开发检查网关是否配置商户
request timestamp too late or early | 请求时效校验错误 | 检查传参时间是否准确
sign uncorrected | 签名验证失败 | 检查密钥配置、签名算法是否有误

