转换域名证书至p12
```shell
openssl pkcs12 -export -clcerts -in .\fullchain.cer -inkey .\bingchunmoli.com.key -out bingchunmoli.com.p12
```
导入到计算机个人证书中
声明式更新
```powershell
wmic /namespace:\\root\cimv2\TerminalServices PATH Win32_TSGeneralSetting Set SSLCertificateSHA1Hash="证书hash"
```