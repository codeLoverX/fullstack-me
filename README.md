# docker

Stop all the containers

docker stop $(docker ps -a -q)
Remove all the containers

docker rm $(docker ps -a -q)
Find more command here