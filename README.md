# Steps to reproduce issue

After installation of macOS Ventura beta 5

Create bedrock project from the Quick Start guide
https://ddev.readthedocs.io/en/latest/users/quickstart/

```sh
mkdir my-wp-bedrock-site
cd my-wp-bedrock-site
ddev config --project-type=wordpress --docroot=web --create-docroot
ddev start
ddev composer create roots/bedrock
```

### Issue:
After running the project it keep reloading and dies with 504 Gateway Timeout error

![504 Gateway Timeout error](https://user-images.githubusercontent.com/5176243/185225725-b4c3280a-8770-41cd-b47a-a2f0784f3369.png)

### Things I tried out:

1) Changing document root from  `/var/www/html/web` to `var/www/html/test` inside `/.ddev/apache/apache-site.conf` file. (Inside test folder [index.php](https://github.com/shayanabbas/my-wp-bedrock-site/blob/master/test/index.php) has been created for testing purpose)

```sh
    DocumentRoot /var/www/html/web
    <Directory "/var/www/html/web/">
```

2) Using Colima it shows same issue.
3) Tried using both server types `webserver_type: nginx-fpm  # or apache-fpm`
4) Tried Colima + Mutagen: It works but ddev doesnt get synced, If i try to do `ddev stop` or `ddev mutagen sync` it doesnt work. (probably this could be a different issue)

#### Note: Simple WordPress and Drupal setup are working out of the box except Laravel and BedRock
Issue has been in discussion at https://github.com/drud/ddev/issues/4122
