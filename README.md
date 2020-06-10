## YAML

- NGINX (latest)
- PHP-FPM (7.4.6)
- PostgreSQL (latest)

## Usage

build & start
```
sudo docker-compose up -d --build
```

remove
```
sudo docker-compose down
```

remove everything (volumes, images, etc.)
```
sudo docker-compose down --rmi all -v --remove-orphans
```

## License

The Laravel Swoole Docker is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
