tunnin vinkit:  
oikeudet skriptiin: chmod a+x scripti.sh  
#install docker to debian:
https://docs.docker.com/engine/install/debian/

#docker tutorial
https://docs.docker.com/get-started/docker-overview/

#test docker installation:
sudo docker run hello-world

#download debian13 docker image
sudo docker pull debian:trixie

#run the container, start interactive terminal and bash shell
sudo docker run -it debian:trixie bash
