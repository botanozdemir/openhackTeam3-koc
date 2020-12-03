# OpenHack Team 3 Space

•	Docker kurulum

•Source code clone 

•	Yeni git repository oluşturmak ve source kodu push etmek 

•	Yeni repo kodlarının clone edilmesi : https://github.com/botanozdemir/openhackTeam3-koc.git

•	SQL server image pull edilmesi : 
 docker pull mcr.microsoft.com/mssql/server:2019-latest  

•	Docker network oluşturulması : https://docs.docker.com/network/network-tutorial-standalone/

•	Source code daki docker file ile image oluşturulması : 
docker build -f Dockerfile_0 -t <taggedimage> .

•	SQL server ile image ı birlikte run etmek
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' 51aa81a3bd27


# Kullanılan komutlar

docker image rm image_id
docker container ls
docker network inspect mssql-network

docker network create --driver bridge mssql-network

docker build -f dockerfiles\Dockerfile_0 -t tripapp:latest src\user-java
docker build -f dockerfiles\Dockerfile_3 -t poiapp:latest src\poi
docker build -f dockerfiles\Dockerfile_2 -t userprofile:latest src\userprofile


docker run --network mssql-network -e "ACCEPT_EULA=Y" -e "SQLFQDN=openhackteam3" -e "SQLUSER=SA" -e  "SA_PASSWORD=P@ssw0rd8688" -e 'MSSQL_PID=Express' -p 1433:1433 --name mydrivingDB -d mcr.microsoft.com/mssql/server:2019-latest

docker run --network mssql-network --name tripApp -p 80:80 -e SQL_SERVER=mydrivingDB -e SQL_USER=SA -e SQL_PASSWORD=P@ssw0rd8688 -e SQL_DBNAME=mydrivingDB tripapp:latest
docker run --network mssql-network --name poiapp -p 8080:80 -e SQL_SERVER=mydrivingDB -e SQL_USER=SA -e SQL_PASSWORD=P@ssw0rd8688 -e SQL_DBNAME=mydrivingDB poiapp:latest
docker run --network mssql-network --name userprofileApp -p 80:80 -e SQL_SERVER=mydrivingDB -e SQL_USER=SA -e SQL_PASSWORD=P@ssw0rd8688 -e SQL_DBNAME=mydrivingDB userprofile:latest

docker exec -it mydrivingDB "bash"
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P P@ssw0rd8688
CREATE DATABASE mydrivingDB
GO
SELECT Name from sys.Databases
GO

az login
az acr login --name registrygto0216
docker login registrygto0216registrygto0216.azurecr.io
docker images
docker tag userprofile:latest registrygto0216.azurecr.io/userprofile:latest
docker push registrygto0216.azurecr.io/userprofile:latest


-----------------------------------------------------------------

https://k8syaml.com/

kubectl run nginx --image=nginx --dry-run=client -o yaml -- bin/sh -c "date;" > pod.yaml
kubectl create deploy busybox --image-busybox --dry-run=client -o yaml > pod.yaml
kubectl get pods



# AKS Cluster oluşturma

TODO

# SQL Server Connections

Information you'll need for challenges. You can find these later in the 'Messages' tab.

Web-dev User: webdev@OTAPRD1545ops.onmicrosoft.com
Web-dev PW: pA6ql7Ua5
Api-dev User: apidev@OTAPRD1545ops.onmicrosoft.com
Api-dev PW: gG8gr2Jd5

Azure SQL FDQN: sqlservergto0216.database.windows.net
Azure SQL Server User: sqladmingTo0216
Azure SQL Server Pass: nG2ma5Jm8
Azure SQL Server Database: mydrivingDB

Simulator url:simulatorregistrygto0216.northeurope.azurecontainer.io



