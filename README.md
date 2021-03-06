# albaraam/php-gcm

A PHP library for sending messages to devices registered through Google Cloud Messaging.


Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

add

```json
"albaraam/php-gcm": "dev-master"
```

to the `require` section of your composer.json.


Usage
------------

```php

use albaraam\gcm\GCMNotification;
use albaraam\gcm\GCMMessage;
use albaraam\gcm\GCMClient;

$notification = new GCMNotification("Title","Body");
$notification
	->setIcon("noti")
	->setSound("water.mp3");
.....

$message = new GCMMessage($notification, "ids"); // "ids" field can contain a array/single registration token or a topic key
$message
	->setData(['foo'=>'bar', 'baz'=>[1,2,3]])
	->setCollapseKey("collapse-key-1");
.....

$gcm = new GCMClient("YOUR_API_KEY"); 
$response = $gcm->send($message);

var_dump($response);

```