# What is this about? #
This excercise is about (de que trata el ejercicio)

# How To #
Pending to develop

# Installation guide #


- Configure Apache virtual host for directory PATH_TO_PROJECT_IN_SERVER/public
- Copy project file to PATH_TO_PROJECT_IN_SERVER

```bash
cd PATH_TO_PROJECT_IN_SERVER
chmod -R 777 storage
chmod -R 777 bootstrap/cache
composer install
mv -v .env.example .env
php artisan key:generate
```

## Technology stack used ##
- **OS** Linux Mint 18.2 Sonya - Cinnamon 3.4.3
- **Apache** 2.4.18 (Ubuntu)1.5.6
- **PHP** 7.0.22-0ubuntu0.16.04.1 (cli) (NTS)
- **Laravel Framework** 5.5.28
- **Composer** 1.5.6

