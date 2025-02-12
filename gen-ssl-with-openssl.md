# 通过openssl生成自签名ssl证书

## 1.安装openssl

```sh
yum install -y openssl
```

## 2.生成私钥（key）

```sh
openssl genpkey -algorithm RSA -out server.key -pkeyopt rsa_keygen_bits:2048
```
## 3.生成证书签名请求（csr）

```sh
openssl req -new -key server.key -out server.csr
```
## 4.生成自签名证书（crt）

```sh
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
```
