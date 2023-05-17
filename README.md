## Laravel Log Activity

This package provides easy to use functions to log the activities of the users of your app. It can also automatically log model events. All activity will be stored in the activity_log table

### Installation

To install the package, simply require it using Composer:
```
composer require waqar/activitylog    
```

### Publish configuration  files

```
php artisan vendor:publish --tag=migrations
```


After the package is installed, you can run the migration to create the activity_logs table in your database:

```
php artisan migrate
```

### Usage

Add it to your App/Providers/EventServiceProvider.php file:

```
use waqar\activitylog\Events\LogActivity;
use waqar\activitylog\Listeners\LogActivityListener;

protected $listen => [
    // ...
      LogActivity::class => [
                  LogActivityListener::class,
      ],
],
```
Next extends the ``BaseActivity`` class in ``Model`` which need to use:

Like below:
```
<?php

namespace App\Models;

use bushart\activitylog\BaseClass\BaseActivity;
use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Log extends BaseActivity
{
    use HasFactory;
}
```

For Custom use:

Dispatch the event with the desired data:

```
event(new LogActivity(['log_name' => 'test', 'description' => 'test description']));
```

This will activity log to the activity_logs table in your database.

### Support

If you encounter any issues with this package, please open an issue on the GitHub repository or contact us at waqarhussainkhalid@gmail.com.

I hope this example description helps you write your own README file! Let me know if you have any other questions.