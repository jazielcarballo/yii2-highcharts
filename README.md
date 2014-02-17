yii2-highcharts-widget
======================

Highcharts widget for Yii 2 Framework


Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist miloschuman/yii2-highcharts-widget "*"
```

or add

```
"miloschuman/yii2-highcharts-widget": "*"
```

to the require section of your `composer.json` file.


Usage
-----

To use this widget, insert the following code into a view file:
```php
use miloschuman\highcharts\Highcharts;

echo Highcharts::widget([
   'options' => [
      'title' => ['text' => 'Fruit Consumption'],
      'xAxis' => [
         'categories' => ['Apples', 'Bananas', 'Oranges']
      ],
      'yAxis' => [
         'title' => ['text' => 'Fruit eaten']
      ],
      'series' => [
         ['name' => 'Jane', 'data' => [1, 0, 4]],
         ['name' => 'John', 'data' => [5, 7, 3]]
      ]
   ]
]);
```
By configuring the `options` property, you can specify the options that need to be passed to the Highcharts JavaScript object. Please refer to the demo gallery and documentation on the [Highcharts website](http://www.highcharts.com/) for possible options.

Alternatively, you can use a valid JSON string in place of an associative array to specify options:
```php
Highcharts::widget([
   'options'=>'{
      "title": { "text": "Fruit Consumption" },
      "xAxis": {
         "categories": ["Apples", "Bananas", "Oranges"]
      },
      "yAxis": {
         "title": { "text": "Fruit eaten" }
      },
      "series": [
         { "name": "Jane", "data": [1, 0, 4] },
         { "name": "John", "data": [5, 7,3] }
      ]
   }'
]);
```

*Note:* You must provide a *valid* JSON string (e.g. double quotes) when using the second option. You can quickly validate your JSON string online using [JSONLint](http://jsonlint.com/).


Tips
----

* If you need to use JavaScript in any of your configuration options (e.g. inline functions), use Yii's [[JsExpression]] object. For instance:

  ```php
  ...
  'tooltip' => [
     'formatter' => new JsExpression('function(){ return this.series.name; }')
  ],
  ...
  ```
  Note, this is currently only possible when using a PHP associative array for configuration.
* Highcharts by default displays a small credits label in the lower right corner of the chart. This can be removed using the following top-level option.

  ```php
  ...
  'credits' => ['enabled' => false],
  ...
  ```
* All adapters, modules, themes, and supplementary chart types must be enabled through the top-level 'scripts' option.

  ```php
  ...
  'scripts' => [
     'highcharts-more',   // enables supplementary chart types (gauge, arearange, columnrange, etc.)
     'modules/exporting', // adds Exporting button/menu to chart
     'themes/grid'        // applies global 'grid' theme to all charts
  ],
  ...
  ```
  For a list of available scripts, see the contents of `vendor/miloschuman/highcharts/assets/`.


Change Log
----------

### [v3.0.9](https://github.com/miloschuman/yii2-highcharts-widget/releases/tag/v3.0.9) (2014 February 17) ###
* Upgraded Highcharts core library to the latest release (3.0.9). See the Highcharts [changelog](http://highcharts.com/documentation/changelog "Changelog") for more information about what's new in this version.