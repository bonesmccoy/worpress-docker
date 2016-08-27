#Wordpress Docker image

This is a bare Wordpress docker installation I made for myself in order to play with it.
It is a very raw version, but enough for my purposes

##Configuration
Go into `docker/app/` and rename `wp-config.php.dist` to `wp-config.php`
Set all wordpress constants

##Run
run `docker-compose up`

At the beginning you should have an error connecting to the database.
Connect to your mysql container and add the database you entered into the wp-config file.



