Docker-Wordpress-Nginx
======================

####Wordpress Application stack using Docker

This will build a simple wordpress PHP application stack using Nginx (front-end container), 
and Application server (back-end container) which is connected to a MySQL container.

This configuration will use VOLUME to create a shared volume containing the wordpress application, also it uses
 the **link** feature to simplify the connection proccess between the containers.

##Usage

To start a wordpress application build the images and run the stack from the top down:

###Building the images:

```
#git clone https://github.com/galal-hussein/Docker-Wordpress-Nginx.git
#cd Docker-Wordpress-Nginx/mysql
#docker build -t husseingalal/mysql .
#cd ../fpm
#docker build -t husseingalal/phpfpm .
#cd ../downloader
#docker build -t husseingalal/downloader .
#cd ../nginx
#docker build -t husseingalal/nginx .
```

###Mysql contianer:

```#docker run -d --name mysql husseingalal/mysql```

###Downloader container:
```#docker run -i -t --name downloader husseingalal/downloader```

###Application server containers:

```#docker run -d --name app1 --volumes-from downloader --link mysql:db husseingalal/phpfpm```

```#docker run -d --name app2 --volumes-from downloader --link mysql:db husseingalal/phpfpm```

###Nginx container:

```#docker run -d -p 80:80 --name nginx --volumes-from downloader --link app1:app1 --link app2:app2 husseingalal/nginx```

The Website will be accessible from port 80.

``` http://127.0.0.1/ ```

##Docker Orchestration Using Fig

Use fig to build and run the containers automatically

```
# cd Docker-Wordpress-Nginx/
# fig up -d
```
