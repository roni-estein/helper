<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Livewire Helper

Livewire helper is a simple base project that you can use to ask question of people in both the [Livewire Discord Help Channel](https://discord.gg/AWZt3P), and to create issues in the [Livewire repository](https://github.com/livewire/livewire) that are too complex for [Laravel Playground](https://laravelplayground.com/#/)

### Sections

Steps are broken down into sections that are tagged, so you can jump to a specific place in the installation process if you need to make any changes. I'll list the steps we've made to produce this helper project in case you want to do this on your own.


### 1. Git Init

The first step you should do in any project, you should always start off by making a git repository so that you can roll back and undo

Navigate to the helper directory and run the command

```
git init
```


### 2. Install [Laravel](https://laravel.com/)

```
laravel new helper --jet --stack=livewire
```


### 3. Install [Pest PHP](https://pestphp.com/docs/installation)

```
composer require phpunit/phpunit:"^9.3.10" --dev --update-with-dependencies
```

```
composer require pestphp/pest --dev --with-all-dependencies
```

Install the Pest PHP - Plug-in

```
composer require pestphp/pest-plugin-laravel --dev && php artisan pest:install
```

You can now verify your example tests

```
./vendor/bin/pest
```

If you are running bash or zsh you can now make an alias to easily run your tests and save it to your .bash_aliases or other shell initialization file or even just type it into your console here is mine.

```
alias t='clear;php -n vendor/bin/pest --exclude-group external'
```

This clears your screen, runs your tests with the -n flag (a speed optimization that clears php_ini variables. You can always add specific ones back in the test that needs one) Also it will exclude long-running tests. You need to annotate those yourself.

```
t
```


### 4. Install [Laravel Telescope](https://laravel.com/docs/8.x/telescope#introduction)

Telescope, is a laravel monitoring and debugging system that is insanely powerful that could help you debug your issues rapidly. If you have a [Laracasts](https://laracasts.com/) account, watch these episodes to learn how you can use it.
 - [Telescope Features](https://laracasts.com/series/learn-telescope/episodes/1)
 - [Telescope as a Monitoring App](https://laracasts.com/series/learn-telescope/episodes/2)

Installation instructions

```
composer require laravel/telescope
```

```
php artisan telescope:install
```

You will need to migrate your database before you can use telescope 


### 5. Configure you environment by making changes to .env.example

.env.example, should always mirror you .env file, which should ***NEVER*** be committed to your git repository. Such that you can share your .env.example and people on your team will know exactly what they will need to populate to run your project. Any keys you add you .env, you should add with a note to your.evn.example

```
# change this ...

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=

# to this

DB_CONNECTION=sqlite
#DB_HOST=127.0.0.1
#DB_PORT=3306
#DB_DATABASE=laravel
#DB_USERNAME=root
#DB_PASSWORD=

# next, change mail from smtp to log
MAIL_MAILER=log
```

Finally, copy .env.example to .env and generate your app key

```
cp .env.example .env
```

```
php artisan key:generate
```






## License

In order to be open source a project is required to have a license. Lack of a license file actually indicates a closed source project.

The Livewire Helper is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
