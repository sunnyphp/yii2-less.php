Yii2 Less.php
=============
This is a Yii2 wrapper extension for PHP port of the official LESS processor http://lesscss.org.
Used composer package [Wikimedia\Less.php](https://packagist.org/packages/wikimedia/less.php) under hood.

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require sunnyphp/yii2-less.php "*"
```

or add

```
"sunnyphp/yii2-less.php": "*"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it (without dots) in your config:

```php
$config = [
    ...
    'components' => [
		...
        'assetManager' => [
            ...
            'converter' => [
                'class' => 'SunnyPHP\Yii2\LessPHP\AssetConverter',
                'compress' => true, // Optional: You can tell less.php to remove comments and whitespace to generate minimized css files.
                'useCache' => true, // Optional: less.php will save serialized parser data for each .less file. Faster, but more memory-intense.
                //'cacheDir' => null, // Optional: is passed to the SetCacheDir() method. Default cache directory in composer package directory.
                'cacheSuffix' => true, // Optional: Filename suffix to avoid the browser cache and force recompiling by configuration changes
            ],
			...
        ],
		...
	],
	...
];
```

So if it is configured you can specify your less files in asset bundle:

```php
class AppAsset extends AssetBundle
{
    public $basePath = '@webroot';
    public $baseUrl = '@web';
    public $css = [
        'css/site.less',
    ];
    public $js = [
    ];
    public $depends = [
    ];
}
```
