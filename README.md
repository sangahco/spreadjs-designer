# spreadjs-designer
Docker Image for SpreadJS Designer

You can run this service using `docker-auto.sh` script:

    $ ./docker-auto up
  
If we want to use it with PMIS we need to start it using with-hub option

    $ ./docker-auto --with-hub up
  
and change the configuration file found in the hub, adding the following location:

    location /sjs-designer/ {
        ### 3: CHANGE THE ALIAS!
        set $upstream_webapp spreadjs-dgn;
        rewrite ^/sjs-designer/(.*) /$1 break;
        proxy_pass http://$upstream_webapp;
        include conf.d/proxy-header.include;
    }
