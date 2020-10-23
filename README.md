<p align="center"><img src="https://github.com/roni-estein/helper/blob/master/public/nerdy-livewire.png?raw=true" width="300"></p>

# Livewire Helper
## About Livewire Helper

Livewire helper is a simple base project that you can use to ask questions of people in both the [Livewire Discord Help Channel](https://discord.gg/AWZt3P), and to create issues in the [Livewire repository](https://github.com/livewire/livewire) that are too complex for [Laravel Playground](https://laravelplayground.com/#/).

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

This clears your screen, runs your tests with the -n flag (a speed optimization that clears php_ini variables. You can always add specific ones back in the test that needs one). Also, it will exclude long-running tests. You need to annotate those yourself.

Try it out!

```
t
```


### 4. Install [Laravel Telescope](https://laravel.com/docs/8.x/telescope#introduction)

Telescope is a laravel monitoring and debugging system that is insanely powerful. It can help you debug your issues rapidly. If you have a [Laracasts](https://laracasts.com/) account, watch these episodes to learn how you can use it.
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


### 5. Configure your environment by making changes to .env.example. You will need to do steps 5 and 6 locally.

.env.example should always mirror your .env file. The .env file should ***NEVER*** be committed to your git repository. Such that you can share your .env.example and people on your team will know exactly what they will need to populate to run your project. Any keys you add to your .env, you should add with a note to your .evn.example.

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


### 6. Migrate your database

and add database/database.sqlite to your .gitignore, this will allow us to have a database/database.sqlite without adding it to the project

```
echo database/database.sqlite >> .gitignore
```

```
touch database/database.sqlite
```

```
php artisan migrate
```

### 7. Setup Pest to use your database in your `tests/Feature` folder and upgrade `composer.json` to use php ^7.4

 - use Tests\TestCase in both Feature and Unit directories
 - use RefreshDatabase in Feature only, limit your unit tests to class functions only
 - update Unit/ExampleTest to be a pest test
 - update Feature/ExampleTest to be a pest test
 - update composer.json to php 7.4 to allow you the most current function set.


### 8. We did it!!!

You can now make your livewire component with the corresponding models and factories you need to ask your question. You should have a well crafted factory for each model in your issue. So that someone can help you solve your problem or present your issue as quickly and as easily as possible.


Find us [on discord](https://discord.gg/AWZt3P) if you have any questions.

-Roni :)


## License

In order to be open source a project is required to have a license. Lack of a license file actually indicates a closed source project.

The Livewire Helper is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
