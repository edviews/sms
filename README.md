
# Project setup

Install [Docker](https://docs.docker.com/install/)

``` bash
git clone git@github.com:edviews/sms.git

cd sms
cp .env.example .env

git submodule init
git submodule update

cd laradock
cp env-example .env
```

Open your project’s sms/.env file and set the following:

```env
DB_HOST=mysql
REDIS_HOST=redis
QUEUE_HOST=beanstalkd
```

Install composer packages in sms/ dir

```bash
docker run --rm -v $(pwd):/app composer/composer install
```

Run your containers

```bash
cd laradock
docker-compose up -d nginx mysql redis workspace
docker-compose exec --user=laradock workspace bash
```

stop your containers

```bash
docker-compose stop
```
