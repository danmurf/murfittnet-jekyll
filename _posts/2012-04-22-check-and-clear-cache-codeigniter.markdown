---
layout: post
title:  " Check and clear cache in CodeIgniter with this Output extension"
date:   2012-04-22 19:06:00 +0000
tags: [ Web Development, PHP, CodeIgniter ]
permalink: blog/check-and-clear-cache-codeigniter
---
I decided to write an extension to the CodeIgniter core Output library as it's great for working with cache but doesn't contain any mechanisms for clearing or managing the cache.

##Installation

Download the extension (details below) and extract the `MY_Output.php` file to your `application/core` folder. The core output library is loaded automatically so the extension should load automatically too. If you have changed the extension prefix to something other than `MY_` in your `config.php` file you will need to update the extension file appropriately.

##Clearing a cached path

You can clear any specified path of its cache by calling `$this->output->clear_path_cache('path/to/clear');`. This method will return `boolean` `TRUE` if successful, `FALSE` if not.

```php
if ($this->output->clear_path_cache('path/to/clear'))
{
    //Cache has been cleared for 'path/to/clear'
}
else
{
    //Cache not cleared - check file exists / permissions
}
```

##Clearing all cache

You can clear the entire cache directory by calling `$this->output->clear_all_cache();`.

*Note: this will **not** remove the `.htaccess` and `index.html` files in the `applications/cache` folder.*

```php
$this->output->clear_all_cache(); //This method returns NULL
```

##Checking to see if a path is cached

You can check to see if a specified path has been cached by calling `$this->output->path_cached('path/to/check')`, which will return `BOOLEAN` `TRUE` if cache does exist for the path or `FALSE` if it doesn't.

```php
if ($this->output->path_cached('path/to/check')
{
    //The path 'path/to/check' is cached
}
else
{
    //There is no cache doe 'path/to/check'
}
```

##Checking the expiration time of a cached path

You can check to see when a specified path's cache will expire by calling `$this->output->get_path_cache_expiration('path/to/check/)`. This will return the an `INTEGER` of the timestamp when the cache is due to expire or `BOOLEAN` `FALSE` if there is no cache for the path.

```php
$cache_expires = $this->output->get_path_cache_expiration('path/to/check/');

if ($cache_expires > 0)
{
    //The cache for 'path/to/check' will expire on the unix timestanp $cache_expires
}
else
{
    //There is no cache for 'path/to/check'
}
```

##Download

The project is hosted on github, so you can always download the latest version from there.

*   **Direct download:** <https://github.com/danmurf/CI-MY_Output/zipball/master>
*   **Project page:** <https://github.com/danmurf/CI-MY_Output>

##License

I added the GNU Public License (GPLv3) to this extension. Read <http://opensource.org/licenses/gpl-license.php> for more information.

##Comments, questions and suggestions

I hope you find this extension useful. If you have any comments or suggestions please leave them in the comments section below. Thanks!