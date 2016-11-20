### Flask starter in a Docker multicontainer

Docker multi-container and flask skeleton with [Flask](http://flask.pocoo.org/) + [MySQL](https://mysql.com) + [uWSGI](http://uwsgi-docs.readthedocs.io/en/latest/) + [Nginx](https://www.nginx.com/)

### Starting

In order to make it work you need [Docker](https://docs.docker.com) & [Docker Compose](https://docs.docker.com/compose/)

Once you've your docker environment ready, clone this repo

```sh
git clone https://github.com/0x13a/docker-flask && cd docker-flask
```

### Configuration

Well, now you have to configure your MySQL server credentials, port & address here in the `docker-compose.yml`

```yml
db:
    image: mysql
    ports:
        - 127.0.0.1:3306:3306
    networks:
        - appnet
    volumes:
        - "./.data/db:/var/lib/mysql"
    environment:
        MYSQL_ROOT_PASSWORD: changeThisSecretPasswordHere
```

You have to configure your project dependencies as well here in the `src/requirements.txt` eg.

```txt
Flask==0.8
Jinja2==2.6
requests==0.11.1
```

### Usage

Build your docker multicontainer

```sh
docker-compose build
```

Run your docker multicontainer

```sh
docker-compose up -d
```

Now your Flask app is ready and running at `http://localhost`

---

Learn more at [https://docs.docker.com/compose/](https://docs.docker.com)