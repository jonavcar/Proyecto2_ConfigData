docker run --name db_mongo -d -p 27017:27017 mongo

docker build -t configserver .
docker run --name api-configserver -d configserver
docker run --name api-configserver -d -p 9997:9997 config-server


docker build -t discovery .
docker run --name api-discovery -d discovery
docker run --name api-discovery -d --network=my-net -p 9999:9999 discovery


docker build -t gateway .
docker run --name api-gateway -d gateway

docker build -t banckaccount .
docker run --name api-banckaccount -d banckaccount
docker run --name api-banckaccount -d --network=my-net -p 8081:8081 banckaccount



docker network ls