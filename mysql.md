# Install docker for mysql on ubuntu 16.04 and use pyodbc to connect DB

單純個人練習pymysql用的筆記

## 環境設定 

先拉映像檔
```cmd
docker run --name mysql -p 3306:3306 -v $(pwd)/mysql_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=<password> -e MYSQL_DATABASE=<db_name> -d mysql
```

進到sql cmd的模式
```cmd
docker exec -it mysql /bin/bash
```
mysql>```mysql -u <account_name> -p```
再輸入密碼就OK惹
source:[dockerhub](https://hub.docker.com/_/mysql/)