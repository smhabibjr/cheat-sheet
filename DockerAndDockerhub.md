Add Dockerfile to your project directory

````docker
FROM ruby:3.1
RUN apt-get update -yqq
RUN apt-get install -yqq --no-install-recommends nodejs
COPY . /usr/src/app
WORKDIR /usr/src/app
RUN bundle
````

Open the command line and type the below command to build our first image
````sh
docker build .
````

After that, we need to check whether our app image builds or not. To check it run the command below.
````sh
docker images
````

Docker build command doesn't run the image. To run newly created image we need to execute this command.

````sh
docker run -p 3000:3000 5b450be52d9b rails s -b 0.0.0.0
````

Now you can see it on localhost:3000

To stop docker container 

````sh
docker stop [OPTIONS] CONTAINER [CONTAINER...]
````
To change docker container name and tag
````sh
docker tag container_id repository_name:tag_name
````
Add cmd for rails 
````sh
CMD ["rails","s","-b","0.0.0.0"]
````
Rebuild the image and run the command 
````sh
docker build -t rubyapp .
````
Now to run it
````sh
docker run -p 3000:3000 railsappName:AppTagName
````
Remove specific docker container
````sh
docker rm -f container_id
````
To remove all the docker containers at once.
````sh
docker rm $(docker ps -aq)
````
To remove specific docker image 
````sh
docker rmi -f image_id
````

To remove all the docker images at once.
````sh
docker rmi $(docker images -aq)
````

To get some space 
````sh
docker system prune
````
To get container performace 
````sh
docker stats container_name_or_id
````
````sh
docker inspect container_name_or_id
````
