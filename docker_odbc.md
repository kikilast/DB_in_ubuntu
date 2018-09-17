# Install docker for mssql on ubuntu 16.04 and use pyodbc to connect DB

單純個人練習pyodbc用的筆記

## 1.環境設定 

會先拉映像檔
以SA的身分建立
```cmd
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<password>' -p 1433:1433 -d microsoft/mssql-server-linux:2017-latest
```
> <yourStrong(!)Password> 改成自己的密碼，至少8位，包含大小寫，不可有符號

進到sql cmd的模式
```cmd
docker exec -it mssql /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P <password>
```

source:[duckerhub](https://hub.docker.com/r/microsoft/mssql-server-linux/)

下載ODBC的驅動程式

```cmd
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Ubuntu 16.04
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list


exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17

```

source:[Microsoft Doc](https://docs.microsoft.com/zh-tw/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-2017)