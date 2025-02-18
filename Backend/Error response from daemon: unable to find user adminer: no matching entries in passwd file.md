Error response from daemon: unable to find user adminer: no matching entries in passwd file.

Solutions:

1、

```yaml
adminer:
     image: adminer
     restart: always
     ports:
          - 8080:8080
     entrypoint: >
     sh -c "
     if ! id -u adminer > /dev/null 2>&1; then
      echo 'adminer:x:999:999::/home/adminer:/bin/sh' >> /etc/passwd;
     fi;
     exec docker-php-entrypoint"
```

2、

```yaml
adminer:
    image: adminer
    restart: always
    ports:
        - 8080:8080
    command: sh -c "useradd -m -s /bin/bash myuser && exec docker-php-entrypoint"
```

3、

```bash
sudo vim /etc/passwd
```

Add: adminer\:x:999:999::/home/adminer:/bin/sh

4、

```bash
     sudo docker build -t adminer .
     sudo docker compose build
     docker compose up -d
```
