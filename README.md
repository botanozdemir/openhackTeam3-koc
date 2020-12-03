# OpenHack Team 3 Space

•	Docker kurulum
•	Source code clone 
•	Yeni git repository oluşturmak ve source kodu push etmek 
•	Yeni repo kodlarının clone edilmesi : https://github.com/botanozdemir/openhackTeam3-koc.git
•	SQL server image pull edilmesi : 
 docker pull mcr.microsoft.com/mssql/server:2019-latest  
•	Docker network oluşturulması : https://docs.docker.com/network/network-tutorial-standalone/
•	Source code daki docker file ile image oluşturulması : 
docker build -f Dockerfile_0 -t <taggedimage> .
•	SQL server ile image ı birlikte run etmek
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' 51aa81a3bd27
