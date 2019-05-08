---
layout: post
title:  "Getting Started with Queues in Laravel"
date:   2019-03-08 14:53:15 +0530
categories: laravel
---

# Getting Started with Queues in Laravel
## WARNING: Work in progress

### Step 1: Select A Driver

Queue requires a driver to store information about failed and success tasks, we are going to use database as driver so open your terminal and type the following command

```bash
php artisan queue:table
php artisan migrate
```

On default setup queue driver is set to sync, which means everything will be executed synchronously but we are going to change it to database so open your `.env` file and add this line

```
QUEUE_DRIVER=database
```

# Step 2: Create a job

To use a queue we need jobs, to do that open your terminal and type

```bash
php artisan make:job SendWelcomeEmail
```

# Step 3: Implement login in the handle method

```php
// app/jobs/SendWelcomeEmail.php


````

# Curl Send A Notification
```
eKp8Hgo6tLQ:APA91bGrR4iBUmKwhKN2dGhSvYK6f-dIgYozI1P19CqPRWVK3vygELtRfX7-_9CpJng0yFryXeit-1R3dHAegjZVxNXf6aeyshT7JVFlYW2VE66RwB_1xlgb6wx85a-r5uSFPhQ42pQH
```

curl -X POST --header "Authorization: key=AAAA0C5pN-A:APA91bH7bEjG2Jsm5BOR2_nlm-u7L2kvHZfv0BNnV195Nj0xQ5LND8C7b3TtUUT1vgzYCgytOcpb1flCNhwiZmYoJInI6t4igFs1fp7UrgP-BlwopTf4DLbiuZD1XI0DDRZ9PHdigm8G" \
	--Header "Content-Type: application/json" \
	https://fcm.googleapis.com/fcm/send \
	-d "{\"to\":\"eKp8Hgo6tLQ:APA91bGrR4iBUmKwhKN2dGhSvYK6f-dIgYozI1P19CqPRWVK3vygELtRfX7-_9CpJng0yFryXeit-1R3dHAegjZVxNXf6aeyshT7JVFlYW2VE66RwB_1xlgb6wx85a-r5uSFPhQ42pQH\",\"notification\":{\"body\":\"ENTER YOUR MESSAGE HERE\"}"
