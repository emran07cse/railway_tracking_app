docker-compose build
docker-compose up -d --force-recreate --build

docker-compose exec php chown -R www-data:www-data /var/www/public
docker-compose exec php chown -R www-data:www-data /var/www/storage/logs
docker-compose exec php chown -R www-data:www-data /var/www/storage/

docker-compose exec php php /var/www/artisan vendor:publish --provider="Encore\Admin\AdminServiceProvider"
docker-compose exec php php /var/www/artisan admin:install
docker-compose exec php php /var/www/artisan Tracking APP-admin:install
