# Laboratorium 11
W plikach: strona, plik docker compose

## Uruchomienie kontenerów:
`docker compose up -d `
## Sprawdzenie czy strona działa:
```
bartosz@tismpad ~/lab11> curl http://localhost:80
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Lab 11</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
</head>
<body>
    <h1>Lab 11</h1>
    <h1>Bartosz Brudkowski</h1>
</body>
</html>⏎                                                                                                            bartosz@tismpad ~/lab11> curl http://localhost:81
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Lab 11</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
</head>
<body>
    <h1>Lab 11</h1>
    <h1>Bartosz Brudkowski</h1>
</body>
</html>⏎                                                                                                            bartosz@tismpad ~/lab11> curl http://localhost:82
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Lab 11</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
</head>
<body>
    <h1>Lab 11</h1>
    <h1>Bartosz Brudkowski</h1>
</body>
</html>⏎
```
## Sprawdzenie czy logi są zapisywane:
```
bartosz@tismpad ~/lab11> tree
.
├── web1
│   ├── access.log
│   └── error.log
├── web2
│   ├── access.log
│   └── error.log
└── web3
    ├── access.log
    └── error.log
bartosz@tismpad ~/lab11> cat web1/access.log
172.20.0.1 - - [16/May/2026:17:31:08 +0000] "GET /stub_status HTTP/1.1" 404 153 "-" "Netdata go.d.plugin/v2.10.0-25-nightly" "-"
172.20.0.1 - - [16/May/2026:17:31:08 +0000] "GET /basic_status HTTP/1.1" 404 153 "-" "Netdata go.d.plugin/v2.10.0-25-nightly" "-"
172.20.0.1 - - [16/May/2026:17:31:08 +0000] "GET /nginx_status HTTP/1.1" 404 153 "-" "Netdata go.d.plugin/v2.10.0-25-nightly" "-"
172.20.0.1 - - [16/May/2026:17:31:08 +0000] "GET /status HTTP/1.1" 404 153 "-" "Netdata go.d.plugin/v2.10.0-25-nightly" "-"
172.20.0.1 - - [16/May/2026:17:31:51 +0000] "GET / HTTP/1.1" 200 296 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36" "-"
172.20.0.1 - - [16/May/2026:17:44:11 +0000] "GET / HTTP/1.1" 200 296 "-" "curl/8.5.0" "-"
bartosz@tismpad ~/lab11> cat web1/error.log 
2026/05/16 17:30:51 [notice] 1#1: using the "epoll" event method
2026/05/16 17:30:51 [notice] 1#1: nginx/1.29.8
2026/05/16 17:30:51 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/05/16 17:30:51 [notice] 1#1: OS: Linux 6.17.0-14-generic
2026/05/16 17:30:51 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1024:524288
2026/05/16 17:30:51 [notice] 1#1: start worker processes
2026/05/16 17:30:51 [notice] 1#1: start worker process 30
2026/05/16 17:30:51 [notice] 1#1: start worker process 31
2026/05/16 17:30:51 [notice] 1#1: start worker process 32
2026/05/16 17:30:51 [notice] 1#1: start worker process 33
2026/05/16 17:30:51 [notice] 1#1: start worker process 34
2026/05/16 17:30:51 [notice] 1#1: start worker process 35
2026/05/16 17:30:51 [notice] 1#1: start worker process 36
2026/05/16 17:30:51 [notice] 1#1: start worker process 37
2026/05/16 17:31:08 [error] 30#30: *1 open() "/usr/share/nginx/html/stub_status" failed (2: No such file or directory), client: 172.20.0.1, server: localhost, request: "GET /stub_status HTTP/1.1", host: "172.20.0.4:80"
2026/05/16 17:31:08 [error] 31#31: *2 open() "/usr/share/nginx/html/basic_status" failed (2: No such file or directory), client: 172.20.0.1, server: localhost, request: "GET /basic_status HTTP/1.1", host: "172.20.0.4:80"
2026/05/16 17:31:08 [error] 32#32: *3 open() "/usr/share/nginx/html/nginx_status" failed (2: No such file or directory), client: 172.20.0.1, server: localhost, request: "GET /nginx_status HTTP/1.1", host: "172.20.0.4:80"
2026/05/16 17:31:08 [error] 33#33: *4 open() "/usr/share/nginx/html/status" failed (2: No such file or directory), client: 172.20.0.1, server: localhost, request: "GET /status HTTP/1.1", host: "172.20.0.4:80"
```


