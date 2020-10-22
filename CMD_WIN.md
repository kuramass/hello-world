# CMD for Win

## 查詢誰在某Server上
Qwinsta /Server:10.xx.xx.xx

## 踢掉Server上的某人(Qwinsta查到的1號user)
RWinsta /Server:10.xx.xx.xx 1

## 電腦的連接訊息
net use

## 中斷電腦連接
net use \\10.xx.xx.xx\D$ /delete

## 確認domain是否已存在
> nslookup
> Server xx.xx.xx.xx (DNS IP)
> www.google.com (要查的domain)

## 列出目錄下所有檔案(含子資料夾)
> cd "目標目錄"
> DIR /S /A:-D /B /O:N > list.txt

## 批次改名(無檔名改為jpeg)
> cd "目標目錄"
> ren *. *.jpeg

## 批次改名動手前先確保語法無誤：
### 測試檔名搜尋語法(無檔名)
> DIR *.
### 測試檔名搜尋語法(所有檔案)
> DIR *.*
### 測試檔名搜尋語法(jpeg)
> DIR *.jpeg
### 測試檔名搜尋語法(f開頭所有檔案)
> DIR f*.*
