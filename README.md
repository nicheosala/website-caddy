# Caddy

[Caddy](https://caddyserver.com) is a software that I want to use as a web server for my website. In this repository, you can find my configs for Caddy.

I've decided to move from Nginx to Caddy because I like the simplicity of the latter.

Moreover, I'm trying to configure Caddy so to run inside a Docker container. The good news is: I'm doing it! Now that I'm able to run Caddy inside Docker, maybe I would be able to do the same for Nginx. However, I have to learn how to compile Nginx from source the best way so to get Brotli and HTTP3 compatibility in it, before thinking about Docker.

## How to use this repository

In this repository, you can find my Caddyfile and my Docker Compose file. I would appreciate your advice!
I'm using a test domain name in this repository for now. If you want to have a fully-functional website in two minutes, you can:
1. clone this repository
2. open Caddyfile and replace my domain name (nicheotest.tk) with yours
3. install Docker and Docker Compose
4. be sure your domain point to your machine and you have opened all the necessary ports also on your router (80 and 443)
5. copy the folder that contains your website inside the repo. The folder must be named "website"
6. inside the repo folder, execute `sudo docker-compose up`
7. After some seconds, the container will be up, Caddy will have got certificates for your website and you will be able to reach your website form the internet. Enjoy!

## Changes
### Caddyfile
If you change the Caddyfile, you have to reload Caddy inside the container so to make the changes effective.
```
sudo docker exec $(sudo docker ps | grep caddy | awk '{print $1;}') caddy reload --config /etc/caddy/Caddyfile --adapter caddyfile
```

### Website
If you change anything inside the website folder, the change is immediately visible in the website, without doing nothing else.

## Next steps
- Get into the caddy container and simplify its structure: you don't need a lot of the things in here, I think.