# Backend Template

`yarn init`

`yarn add --dev typescript @types/node`

`yarn add --dev ts-node-dev`

ts-node-env 無法解析 alias path

https://www.npmjs.com/package/tsconfig-paths

`yarn add --dev tsconfig-paths`

pacjage.json script 要加上參數 `-r tsconfig-paths/register`

## with Prettier
VScode 不支援 Eslint 8，需要安裝舊版本
`yarn add --dev eslint@7.32.0 prettier prettier-eslint`

`yarn add --dev @typescript-eslint/parser`

要裝 eslint-plugin，否則 prettier-eslint formatting 會跳錯誤

`yarn add --dev @typescript-eslint/eslint-plugin`

## Express (optional)
`yarn add express`

`yarn add --dev @types/express`


## MongoDB (optional)
### Mongoose
`yarn add mongoose`

`yarn add --dev @types/mongoose`

### MongoDB Server
在 WSL 安裝 MongoDB Community Server

https://docs.microsoft.com/zh-tw/windows/wsl/tutorials/wsl-database#install-mongodb

### 開發紀錄：啟動 WSL 的 systemd 失敗
為了讓系統自動啟動 mongodb 服務，依照這個網頁說明啟用 WSL 2 原本沒有的 systemd

https://ithelp.ithome.com.tw/articles/10255920

但 wsl-terminal 因此改變了初始資料夾，在 wsl-terminal 的內容更改開始位置

`\\wsl$\Ubuntu-20.04\home\deemo`

然後又發現 VSCode 開不了 WSL 2 的 bash

https://github.com/microsoft/vscode/issues/102628#issuecomment-662624376

跑完 script 發現 wsl bash terminal 進不去了，只寫了一行字就跳出

`You need to run -bash through sudo`

最後轉回 WSL 1 把 script 跑的東西 revert 回來才救回來

事實上安裝 MongoDB 雖然顯示沒有 systemd 但還是有安裝成功

### 設定 MongoDB 驗證
https://blog.yowko.com/mongodb-enable-auth/

建立使用者出現錯誤

`Error: couldn't add user: Use of SCRAM-SHA-256 requires undigested passwords`

解法: https://stackoverflow.com/questions/51149455/mongodb-getting-error-while-creating-new-user

設定好後重啟伺服器，記得加上 --auth，客戶端登入要先 use admin