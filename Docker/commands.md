brug powershell
# /1/
Dockerfile
# /2/
docker ps -a

docker start tek-demo


docker stop tek-demo

docker rm tek-demo

# /3/
docker build -t tek-image .

docker run -d --name sc -p 8080:80 tek-image

exit
# /4/
compose.yaml

docker compose up

docker compose down
# /5/
docker images

docker rmi tek-image

docker image prune

docker system prune
# /6/
Dockerfile - optimized

