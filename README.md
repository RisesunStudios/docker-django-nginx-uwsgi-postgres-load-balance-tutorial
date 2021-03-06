# docker-django-nginx-uwsgi-postgres-load-balance-tutorial

å¯¦æ° Docker + Django + Nginx + uWSGI + Postgres - **Load Balance**  ð

éç¯æç« ä¸»è¦æ¥çºä¸ä¸ç¯

[Docker + Django + Nginx + uWSGI + Postgres åºæ¬æå­¸ - å¾ç¡å°æ ( Docker + Django + Nginx + uWSGI + Postgres Tutorial )](https://github.com/twtrubiks/docker-django-nginx-uswgi-postgres-tutorial)

ç¹¼çºä»ç´¹ï¼éæ¬¡çéé»ææ¾å¨ Nginx ç **Load Balance** ä¸ :blush:

* [Youtube Tutorial PART 1 - æ­£åä»£çå¨  VS ååä»£çå¨ - ç°¡ä»](https://youtu.be/R2I8BBXnJJ8)
* [Youtube Tutorial PART 2 - Docker + Django + Nginx + Load Balance - æ¦å¿µ](https://youtu.be/W4EMOO-THGs)
* [Youtube Tutorial PART 3 - Docker + Django + Nginx + Load Balance - å¯¦æ°](https://youtu.be/ChK8MtQUDf0)
* [Youtube Tutorial PART 4 - Django + Nginx + Load Balance - Docker scale](https://youtu.be/w83_lV5tORI)

## ç°¡ä»

å¨éå§ä»ç´¹ Nginx ç Load Balance ä¹åï¼ææåå¸¶å¤§å®¶äºè§£ä¸äºåè©ã

éè¨å¾å¨ [ä¸ä¸ç¯](https://github.com/twtrubiks/docker-django-nginx-uswgi-postgres-tutorial) æå­¸ä¸­ï¼æå° Nginx å¯ä»¥è¨­å® ååä»£çå¨ åï¼

é£æåæ²æè©³ç´°è§£éä»éº¼æ¯ ååä»£çå¨ ï¼ééæå°åå¸¶å¤§å®¶äºè§£

**æ­£åä»£çå¨** ä»¥å **ååä»£çå¨** çå·®å¥ :notebook:

### æ­£åä»£çå¨  VS ååä»£çå¨

#### æ­£åä»£çå¨

æ­£åä»£çå¨æ¯ä¸åä½æ¼ä½¿ç¨èç«¯ä»¥åç®æ¨ Server ä¹éç **ä»£çä¼ºæå¨ ( Proxy Server )**ï¼

ééä»£çä¼ºæå¨æ¶ç¼ Request / Respond è³æï¼

![](https://i.imgur.com/zWIk8QW.png)

å¦ä¸åï¼X ç¡æ³ç´æ¥å Z è«æ±è³æï¼ä½æ¯ Y å¯ä»¥å Z è«æ±è³æ ( æ¼æ¯ X éé Y å Z è«æ±è³æ )ï¼

Y å¾å°è³æå¾ï¼åå°è³æåå³çµ¦ Xï¼éæ¨£ X å°±è½é å©å¾å° Z çè³æäº ã

éå¸¸æ­£åä»£çå¨å¿é é¡å¤åä¸äºè¨­å®æå¯ä»¥ä½¿ç¨ã

æ­£åä»£çå¨ï¼Client å Proxy å¯è¦çºåä¸å LAN ï¼å° Server æ¯é±èçã

![](https://i.imgur.com/MJ0Pr2q.png)

æº«é¦¨å°æé :heart:

* LAN ( Local Area Network )ï¼åç¨± ååç¶²è·¯

* WAN ( Wide Area Network )ï¼åç¨± å»£åç¶²è·¯

* WLAN ( Wireless LAN )ï¼åç¨± ç¡ç·ååç¶²è·¯

æ­£åä»£çå¨æ¯ä»£çä½¿ç¨èç«¯ï¼ Client ç«¯ ï¼ï¼æ¿ä½¿ç¨èç«¯ï¼ Client ç«¯ ï¼æ¶ç¼ Request / Respondï¼

è®çæ­£çä½¿ç¨èå°ä¼ºæå¨ç«¯ï¼ Server ç«¯ ï¼é±èã

å¯è½ä½ èªå·±ä¹æä½¿ç¨éï¼ ææ­£å¨ä½¿ç¨ :grin: ï¼æ­£åä»£çå¨ ï¼åªæ¯ä½ ä¸ç¥éèä»¥ï¼åæå¸¸è¦çå°±æ¯ **ç¿»ç ( VPN )** :smirk:

ä»å¤©ä¸»è§æ¯é¿é¬¼ï¼é¿é¬¼ç¡æ³çè¦½ FBï¼ä½å¯ä»¥çè¦½ Server Aï¼èé¿é¬¼ç¼ç¾ Server A å¯ä»¥è¨ªå FBï¼

æ¼æ¯é¿é¬¼å°±éé Server A å»çè¦½ FBï¼æ´åæµç¨æ¯ï¼é¿é¬¼éé Server A å»çè¦½ FBï¼Server A æ¶å°

ä¾èªé¿é¬¼ç Request æï¼å»çè¦½ FBï¼FB åæ Response åå³çµ¦ Server Aï¼Server A åææ¶å°ç

Response åå³çµ¦é¿é¬¼ï¼éæ¨£é¿é¬¼å°±è½é å©å¾å° FB çè³æï¼éå°±æ¯éé Proxy ( æ­£åä»£çå¨ )ã

#### ååä»£çå¨

ååä»£çå¨åç¸åéä¾ï¼å°æ¼ä½¿ç¨èç«¯ä¾èªªï¼ååä»£çå¨å°±å¥½åæ¯ç®æ¨ Serverï¼

ä½¿ç¨èç«¯ä¹ä¸éè¦åé¡å¤çè¨­å®ï¼

![](https://i.imgur.com/kUBGgKz.png)

å¦ä¸åï¼éç¶æ´åæµç¨éæ¯ X->Y->Zï¼ä½å çºä¸ç¨ç¹å¥è¨­å®ï¼æä»¥ä½¿ç¨èç«¯ææè¦ºå¥½åç´æ¥æ¯ X->Zï¼

ååä»£çå¨ï¼Proxy å Server å±¬æ¼ä¸å LANï¼å° Client é±è

![](https://i.imgur.com/j6wnvnt.png)

ååä»£çå¨æ¯ä»£çä¼ºæå¨ç«¯ï¼ Server ç«¯ ï¼ï¼æ¿ä¼ºæå¨ç«¯ï¼ Server ç«¯ ï¼æ¶ç¼ Request / Respondï¼

è®çæ­£çä¼ºæå¨ï¼ Server ç«¯ ï¼å°ä½¿ç¨èé±èã

æ¬æ¬¡çä¸»è§ **Load Balance** å°±æ¯ååä»£çå¨çä¸ç¨®æç¨ :open_mouth:

## æå­¸

è§£éäºé£éº¼å¤ï¼æåè¦éå§å¯¦æ° Nginx ç Load Balanceï¼ç¯ä¾ä¸æ¨£æ¯ä½¿ç¨ [ä¸ä¸ç¯](https://github.com/twtrubiks/docker-django-nginx-uswgi-postgres-tutorial) åä¿®æ¹ï¼

å çºè¦å Load Balanceï¼æä»¥å¢å ä¸å°ä¸»æ©ï¼ service ï¼ï¼åç¨±å½åçº [api2](https://github.com/twtrubiks/docker-django-nginx-uwsgi-postgres-load-balance-tutorial/tree/master/api2)ï¼åºæ¬ä¸å§å®¹

é½å [api](https://github.com/twtrubiks/docker-django-nginx-uwsgi-postgres-load-balance-tutorial/tree/master/api) å·®ä¸å¤ï¼åªæ¯ä¿®æ¹äºä¸äºåç¨±ï¼ æ¹ä¾¿åå¥èå·² ï¼ï¼å¯åè [docker-compose.yml](https://github.com/twtrubiks/docker-django-nginx-uwsgi-postgres-load-balance-tutorial/blob/master/docker-compose.yml)ã

æ´é«ç Load Balance çæ¦å¿µå¯ä»¥åèä¸å

![](https://i.imgur.com/RxUtPiz.png)

éæ¨£æä»éº¼å¥½èå¢ ï¼

æç´æ¥çå¥½èå°±æ¯ï¼å¦æä¸å°æäºï¼æ´åç³»çµ±éæ¯ä¸ææ­»ï¼

å çºå¶ä»ç Server éæ¯æ­£å¸¸å·¥ä½:relaxed:

åä¾å°±æ¯æåçä¸»è§ [my_nginx.conf](https://github.com/twtrubiks/docker-django-nginx-uwsgi-postgres-load-balance-tutorial/blob/master/nginx/my_nginx.conf)ï¼å¶å¯¦ä¸»è¦ä¹æ¯ä¿®æ¹ééçè¨­å®èå·² :laughing:

```config
# the upstream component nginx needs to connect to
upstream uwsgi {
    # server api:8001; # use TCP
    server unix:/docker_api/app.sock weight=4 ; # for a file socket
    server unix:/docker_api2/app2.sock  weight=6; # for a file socket
}

# configuration of the server
server {
    # the port your site will be served on
    listen    80;
    # index  index.html;
    # the domain name it will serve for
    # substitute your machine's IP address or FQDN
    server_name  twtrubiks.com www.twtrubiks.com;
    charset     utf-8;

    client_max_body_size 75M;   # adjust to taste

    # Django media
    # location /media  {
    #     alias /docker_api/static/media;  # your Django project's media files - amend as required
    # }

    location /static {
        alias /docker_api/static; # your Django project's static files - amend as required
    }

    location / {
        uwsgi_pass  uwsgi;
        include     /etc/nginx/uwsgi_params; # the uwsgi_params file you installed
    }

}
```

å¶å¯¦è¨­å®ä¸¦ä¸é£ï¼åªæ¯å¨ `upstream` è£¡é¢å¢å ä¸å° Server èå·²ï¼å¾é¢ç `weight` åä»£è¡¨æ¬éï¼

Nginx é è¨­æä½¿ç¨ round-robin æ¼ç®æ³ä¾å¯¦ä½ Load balanceã

### Load balancing methods

Nginx ä¸»è¦ç Load balance æä¸ç¨®

****round-robin â requests to the application servers are distributed in a round-robin fashion****

ä½¿ç¨è¼ªè©¢çæ¹å¼ï¼ä¹å¯ä»¥å ä¸ `weight` æ¬éï¼è®æ¯è¼å¼·ç Server æ¿åæ¯è¼å¤§çå£åï¼ `weight` è¨­å®é«ä¸é»ï¼ã

****least-connected â next request is assigned to the server with the least number of active connections****

æ­¤ç¨®æ¹å¼ï¼Nginx æå°è«æ±çµ¦è² è¼ Loading è¼è¼ç Serverï¼é¿åè² è¼ï¼A Serverï¼ Loading å·²ç¶å¾å¤§äºï¼

éå°è«æ±äº¤çµ¦ A Server èçã

****ip-hash â a hash-function is used to determine what server should be selected for the next request (based on the client's IP address)****

ä¸ç®¡æ¯ round-robin éæ¯ least-connected ç Load balance ï¼æ¯å User éåºçè«æ±é½å¯è½æè¢«åå°ä¸åç

Serverï¼ä¸¦ä¸è½ä¿è­åä¸å User æ¯æ¬¡çè«æ±é½ä¸å®æé£å°åä¸å° Serverï¼
å çºéååå ï¼æ¼æ¯æäº ip-hashï¼

éééåæ¹æ³ï¼æä½¿ç¨ ip çæ¹å¼å°åä¸å User çè«æ±é½å°å°åä¸å°
Server ï¼é¤ééå° Server æäº :sob: ï¼

ä»ç´¹å®äº Nginx ä¸»è¦çä¸ç¨® Load balance æ¼ç®æ³ï¼è³æ¼è¦ä½¿ç¨åªä¸ç¨®ï¼å°±çä½ èªå·±çéæ±äº :grinning:

æ´å¤ç¯ä¾ä»¥åè©³ç´°çèªªæå¯åèå®ç¶²

 ( å»ºè­°é±è® ï¼éç¶ææå¹«å¤§å®¶æ´çéé»åºä¾äº :grinning:  )

[http://nginx.org/en/docs/http/load_balancing.html](http://nginx.org/en/docs/http/load_balancing.html)

## å·è¡æ­¥é©

ç´æ¥å·è¡ `docker-compose up` è¦è­å¥è¹

ç´°é¨çåå°±ä¸åè²¼ä¸æ¬¡äºï¼è«åè [ä¸ä¸ç¯](https://github.com/twtrubiks/docker-django-nginx-uswgi-postgres-tutorial)

æç¼ç¾æåå¤äºä¸å° `api2`

![](https://i.imgur.com/KhROEky.png)

æ¥èéåå¦ä¸å terminalï¼é²å¥ `api` ( Django + uWSGI ) çå®¹å¨ï¼

æä»¤å¯åèä¹åç [docker-tutorial-æä»¤ä»ç´¹](https://github.com/twtrubiks/docker-tutorial#æä»¤ä»ç´¹)ï¼

```cmd
docker exec -it <Container ID> bash
```

å·è¡ migrate

```cmd
python manage.py makemigrations musics
python manage.py migrate
```

![](https://i.imgur.com/nQDwP7e.png)

å»ºç« user

```cmd
python manage.py createsuperuser
```

![](https://i.imgur.com/saaDD7R.png)

æå¾åå·è¡

```cmd
python manage.py collectstatic
```

![](https://i.imgur.com/1EKNNOx.png)

å° Django ä¸­ç static files æ¶éèµ·ä¾ï¼è®æ static folderï¼

æåä¸éè¦åé²å¥ `api2` ç container å·è¡ååçåä½ï¼å çºæåé½æ¯é£åä¸å dbï¼

å°éè£¡åºæ¬ä¸å°±æ¯å®å·¥äº:smile:

çè¦½ [http://localhost:8080/api/music/](http://localhost:8080/api/music/) ç¢ºèªæ¯å¦æ­£å¸¸ã

## å·è¡ç«é¢

çè¦½ [http://localhost:8080/api/music/](http://localhost:8080/api/music/)

![](https://i.imgur.com/jl43jST.png)

![](https://i.imgur.com/Fw6LjbE.png)

é£è¦æéº¼ç¢ºå®ççæ Load balance å¢ï¼

å¯ä»¥å¨é é¢ä¸ççé»æ F5ï¼ç¶å¾æåè§å¯ terminalï¼ä½ æç¼ç¾

![](https://i.imgur.com/7xuFXw5.png)

ææåæ¯ `api`ï¼ææåæ¯ `api2`ï¼éè¨å¾åé¢è¨­å®ç `weight` æ¬éï¼

`api` å `api2` æ¯ 4:6ï¼4:6 æ¯ä»éº¼ææå¢:question::question:

åå¦ç¾å¨æ 10 å Request é²ä¾ï¼4 å Request æäº¤çµ¦ `api` éå Server èçï¼

èå©ä¸ç 6 å Request åæäº¤çµ¦ `api2` éå Server èç :+1:

`weight` æ¬éå¯ä»¥ä¾ç§èªå·±çéæ±è¨­å®ã

æ¥èåä¾æ¨¡æ¬ä¸å° Server æäºçæåï¼å¦ä¸åï¼Server å çºæç¨®åå æäºï¼

![](https://i.imgur.com/fRa1Q9t.png)

åéé stop æä»¤å° `api` container åæ­¢

( æ¨¡æ¬ `api` éå° Server æäº )

```cmd
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```

![](https://i.imgur.com/LkoQeDc.png)

![](https://i.imgur.com/lHmMPUu.png)

ç¶å¾åç¹¼çºçè¦½ [http://localhost:8080/api/music/](http://localhost:8080/api/music/)ï¼ä½ æç¼ç¾ç¶²ç«æ­£å¸¸ work ( ç¢ºå¯¦æ²æææ )ï¼

èä¸ terminal ç¾å¨é½åªæè¼¸åº `api2`ï¼

![](https://i.imgur.com/RTdzQqX.png)

å çºæåå·²ç¶å° `api` åæ­¢äºï¼æ¨¡æ¬æ©å¨æå¤æäºï¼ï¼

ææ²æå¾é· :satisfied: éå°±æ¯æç°¡å®ç Load balance :flushed:

ç¯ä¾æ¯ç¸½å±æå©å° server ( `api` ä»¥å `api2` )ï¼ ä½ ä¹å¯ä»¥èªå·±å¤æ°å¢å¹¾å°ä¾ç©ç©çã

## å¶ä»çè² è¼å¹³è¡¡

é¤äº Nginx ç Load banlance ä¹å¤ï¼åè¨­ä½ çç³»çµ±æ´é¾å¤§ä¸æè¦æ¨¡ï¼

å¯ä»¥èæ®ä½¿ç¨æ´å°æ¥­çè² è¼å¹³è¡¡ï¼åæ¯ [HAProxy](http://www.haproxy.org/) ( High Availability Proxy ) ï¼

å¦æè¦å°æ³¨å¨ Load banlance ä¸ï¼é¸æ [HAProxy](http://www.haproxy.org/) æè©²ææ¯ Nginx ç

Load banlance éä¾çå¥½ã

å¦æå° HAProxy æèè¶£ï¼å¯åè [Docker Swarm + HAProxy](https://github.com/twtrubiks/docker-swarm-tutorial#docker-swarm--haproxy) :sunglasses:

## å¾è¨ï¼

éæ¬¡ä¸»è¦ä»ç´¹äº Nginx ç Load Banlance çµ¦å¤§å®¶ï¼å»ºè­°å¤§å®¶å¯ä»¥åæç©ç©çï¼æ´é«ææ¯è¼ææè¦º :smiley:

éæ¬¡åè©¦åèç¶²è·¯ä¸çåèªå·±ç°¡å®çç«ä¸éï¼å¸æå°å¤§å®¶å¤å¤å°å°æå¹«å©:flushed:

å¦ææå¨ç©åæ¯ AWS çäººï¼å¯ä»¥ç¥ééæä¸ç¨®æ±è¥¿æ´çï¼å°±æ¯ ç°å°åæ­¥åä»½ï¼å¤§å®¶æèè¶£èªè¡ç ç©¶:sunglasses:

å¦ææä»»ä½è¬é¯çå°æ¹ï¼è«éº»ç©å¤§å®¶åæèªªï¼ææåä¿®æ¹ï¼æè¬åä½çé±è®:v:

ä¸ä¸æ­¥å¯ä»¥è©¦è©¦çç¨ Docker scale çæ¹æ³ä¾å®æ( æ´å¥½çå¯«æ³ )ï¼å¯åè [better](https://github.com/twtrubiks/docker-django-nginx-uwsgi-postgres-load-balance-tutorial/tree/better) åæ¯ã

å¦ææç¶æªç¡ï¼å»¶ä¼¸é±è® :satisfied:

* [Docker Swarm åºæ¬æå­¸ - å¾ç¡å°æ Docker-Swarm-Beginners-Guideð](https://github.com/twtrubiks/docker-swarm-tutorial)

## å·è¡ç°å¢

* Mac
* Python 3.6.2
* windows 10

## Reference

* [https://docs.docker.com/](https://docs.docker.com/)
* [nginx-load_balancing](http://nginx.org/en/docs/http/load_balancing.html)

## Donation

æç« é½æ¯æèªå·±ç ç©¶å§åå¾ååµï¼å¦ææå¹«å©å°æ¨ï¼ä¹æ³é¼åµæçè©±ï¼æ­¡è¿è«æåä¸æ¯åå¡:laughing:

![alt tag](https://i.imgur.com/LRct9xa.png)

[è´å©èä»æ¬¾](https://payment.opay.tw/Broadcaster/Donate/9E47FDEF85ABE383A0F5FC6A218606F8)

## License

MIT license
