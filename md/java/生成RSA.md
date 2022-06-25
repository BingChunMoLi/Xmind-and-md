### 使用JDK工具:
```shell
keytool -genkeypair -alias moli -keyalg RSA -keypass password -keystore key.key -storepass password
```

#### 查看公私钥:
```shell
keytool -list -rfc --keystore jwt.key | openssl x509 -inform pem -pubkey
```
### 使用ssh-keygen
```shell
ssh-keygen -t rsa -b 4096 -f private.key
openssl rsa -in ${private}.key -pubout -outform PEM -out ${public}.key.pub
openssl pkcs8 -topk8 -inform PEM -in jwtRS256.key -outform pem -nocrypt -out pkcs8.pem
```
分别是，生成私钥、生成公钥、转换格式

### 使用openssl
```shell
openssl genrsa -out rsaprivatekey.pem 4096
openssl rsa -in rsaprivatekey.pem -out rsapublickey.pem -pubout
openssl pkcs8 -topk8 -in rsaprivatekey.pem -out pkcs8rsaprivate_key.pem -nocrypt
```
分别是，生成私钥、生成公钥、转换格式