---
layout: post
title:  "Getting Started with Queues in Laravel"
date:   2019-03-08 14:53:15 +0530
categories: laravel
---

# WARNING: Work in progress
### Getting Started with Queues in Laravel
Points you should remember
- Queue needs a driver and we can use database for starting
- To do that type `php artisan queue:table` and then `php artisan migrate`
- Queue requires Jobs, so create a new job for a task you're going to do.
- `php artisan make:job SendNotification`
- Job constructor receives an argument and calls dispatch method to do something you want to do
