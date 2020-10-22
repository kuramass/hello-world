# Use Openssl to generate CSR

## 移到/home/xx

## 確認openssl版本1.0.1e(若不是，要確認以下指令是否可用)
$ openssl version

## 產RSA 2048金鑰
$ openssl genrsa -out key名稱.key 2048

## 備份金鑰
$ openssl genrsa -des3 -out key名稱.key 2048

## 產CSR
$ openssl req -new -sha256 -key key名稱.key -out csr名稱.csr

資訊:
Country Name (2 letter code) [XX]:TW
State or Province Name (full name) []:TAIWAN
Locality Name (eg, city) [Default City]:TAIPEI
Organization Name (eg, company) [Default Company Ltd]:組織名
Organizational Unit Name (eg, section) []:單位名
Common Name (eg, your name or your server's hostname) []: Domain名


6. 將key&csr取出 (可能用到以下檔案操作)
$ chown --reference=參考檔 csr名稱.csr
$ chmod --reference=參考檔 csr名稱.csr
$ cp 來源檔 目標檔
