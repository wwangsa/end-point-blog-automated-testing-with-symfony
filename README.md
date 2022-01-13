# end-point-blog-automated-testing-with-symfony
Learning unit testing from this [article](https://www.endpointdev.com/blog/2020/09/automated-testing-with-symfony/). 
The [author's repo](https://github.com/megakevin/end-point-blog-automated-testing-with-symfony) missing versioning 

If the repo still not doing the job, try the commands below
Here how to get the app running in docker container
On the host
```shell

  # Build the image with (replace USER accordingly):
  #   docker build --build-arg USER=kevin --build-arg UID=$(id -u) --build-arg GID=$(id -g) -t weather-app .
  #
  # Run a container based on the image:
  #   docker run -d --name weather-app --network host -v ${PWD}:/workspaces/weather-app weather-app
  #
  # Connect to the container:
  #   docker exec -it weather-app bash
```

On the container's bash
```shell
        #PHP 7.4 and its libraries need to be installed inside the container
        sudo cp -pr /workspaces/weather-app/. /workspaces/symfony-demo/
        sudo apt install php7.4 php7.4-mbstring php7.4-xml php7.4-sqlite3 php7.4-curl
        cd /usr/bin
        sudo rm php
        sudo ln -s /usr/bin/php7.4 php
        sudo chown -R kevin:kevin /workspaces/symfony-demo
        cd /workspaces/symfony-demo
        composer install
        php bin/console doctrine:schema:create
        composer serve
 ```
 The site is running on localhost:3000
