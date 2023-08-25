# NGINX Load Balancer + Simple HTML Web Site 

1) Clone to the new folder inside WSL2

2) Go to lb_compose folder

3) docker-compose up -d

4) Add line to hosts file:

127.0.0.1 magento_alb.loc

5) http://magento_alb.loc : Open in browser & Refresh it

=========================================================

6) To prevent the issue:

[emerg] 1#1: host not found in upstream "server.two:8088" in /etc/nginx/conf.d/alb.conf:27

At the first running comment the line 

    upstream all {
        server server.one:8000;
        #server server.two:8088;
    }

7) Then open in browser both servers
    http://server.one:8000/
    http://server.two:8088/

8) Then restart the NGINX container with un-commented line 

`    upstream all {
        server server.one:8000;
        server server.two:8088;
    }
`

9) I hope it should works
