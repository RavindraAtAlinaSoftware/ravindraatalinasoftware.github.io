---
layout: post
title:  "Laravel Polymorphic Relations"
date:   2019-03-08 14:53:15 +0530
categories: laravel
---

### Laravel Polymorphic Relationships

For this tutorial I am going to use same post, video and comment example as seen all over internet.

### Steps
#### Create A New Laravel Project
```bash
composer create-project --prefer-dist laravel/laravel Polymorphic-Training
```

### Create new models and controllers
```bash
php artisan make:auth
php artisan make:model -mcr Photo
php artisan make:model -mcr Video
php artisan make:model -mcr Comments
```

### Edit Migration Files
```php
// Comments Migration
public function up()
{
    Schema::create('comments', function (Blueprint $table) {
        $table->bigIncrements('id');
        $table->timestamps();
        $table->morphs('commentable');
    });
}

// Photos Migration
public function up()
{
    Schema::create('photos', function (Blueprint $table) {
        $table->bigIncrements('id');
        $table->timestamps();
        $table->string('name');
    });
}

// Videos Migration
public function up()
{
    Schema::create('videos', function (Blueprint $table) {
        $table->bigIncrements('id');
        $table->timestamps();
        $table->string('name');
    });
}
```

### Add Relationship to models
```php
// Photo Model
class Photo extends Model
{
    protected $guarded = [];

    public function comment()
    {
        return $this->morphMany('App\Comment', 'commentable');
    }
}

// Video Model
class Video extends Model
{
    protected $guarded = [];

    public function comment()
    {
        return $this->morphMany('App\Comment', 'commentable');
    }
}

// Comment Model
class Comment extends Model
{
    protected $guarded = [];

    public function commentable()
    {
        return $this->morphTo();
    }
}
```


### Create Factories
```php
// Comment Factory
$factory->define(App\Comment::class, function (Faker $faker) {
    return [
        'name' => $faker->sentence($nbWords = 6, $variableNbWords = true),
    ];
});

// Photo Factory
$factory->define(App\Photo::class, function (Faker $faker) {
    return [
        'name' => $faker->name
    ];
});

// Video Factory
$factory->define(App\Video::class, function (Faker $faker) {
    return [
        'name' => $faker->name
    ];
});
```


### Add these to default seeder
```php
// Create 5 photos with 5 comments each
factory(Photo::class, 5)->create()->each(function ($photo) {
    $photo->comment()->saveMany(factory(Comment::class, 5)->make());
});

// Create 5 videos with 5 comments each
factory(Video::class, 5)->create()->each(function ($video) {
    $video->comment()->saveMany(factory(Comment::class, 5)->make());
});
```

### Migrate and seed data

```
php artisan migrate:fresh --seed
```

### Play with app

- Launch Tinker: `php artisan tinker`


```php
// Select first photo
$firstPhoto = Photo::first()

// Select all comment for first photo
$firstPhoto->comment

// Select only comment body for first photo
$firstPhoto->comment->pluck('name')

// Feel free to play with it then implement

```
