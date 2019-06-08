# Docker Setup 

## Build docker image

```
cd docker
./build
```


## Up & Running


- New laravel project
    + `./develop composer create-project --prefer-dist laravel/laravel MO_JS-PHP_A`

- Check that our nodejs container works
    + `./develop run --rm -w /www/html/projects node -v` 
    + `./develop run --rm -w /www/html/projects/MO_JS-PHP_A composer install`
    + `./develop run --rm -w /www/html/projects/MO_JS-PHP_A artisan`


- We'll need an APP_KEY as well for the .env file:

```
docker-compose run --rm \
    -w /var/www/html/projects/demo \
    app \
    php artisan key:generate
```

update .env `DB_HOST=mysql`

- Then we can spin up our containers to run this in development:
    + `./develop up -d`

- Stop containers
    + `./develop stop`


# Install composer deps
./develop composer install

# Run phpunit
./develop test

# Install node_modules dependencies
./develop npm install


