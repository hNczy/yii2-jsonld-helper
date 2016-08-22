yii2-jsonld-helper
================

Yii2 helper class for registering structured data markup in [JSON-LD](http://json-ld.org/) format.

## Resources
 * Yii2 [extension page](http://www.yiiframework.com/extension/yii2-jsonld-helper)
 * JSON-LD [documentation](http://json-ld.org/learn.html)
 * Google [Structured Data Testing Tool](https://search.google.com/structured-data/testing-tool)

## Installation

### Composer

Add extension to your `composer.json` and update your dependencies as usual, e.g. by running `composer update`
```js
{
    "require": {
        "nirvana-msu/yii2-jsonld-helper": "1.0.*@dev"
    }
}
```

##Sample Usage

To let search engines know how to display your website name in search results,
you can add the following JSON-LD document somewhere on your landing page:

```php
$doc = (object)[
    "@type" => "http://schema.org/WebSite",
    "http://schema.org/name" => Yii::$app->params['brand'],
    "http://schema.org/url" => Yii::$app->urlManager->hostInfo
];

JsonLDHelper::add($doc);
```

You can also use `JsonLDHelper::addBreadcrumbList` to add `BreadcrumbList` schema.org markup 
based on the application view `breadcrumbs` parameter. E.g. in the beginning of your layout add:

```php
JsonLDHelper::addBreadcrumbList();
```

Finally, you must invoke `JsonLDHelper::registerScripts` method in the `<head>` section of your layout, e.g.

```html
<head>
    <!-- ... -->
    <?php JsonLDHelper::registerScripts(); ?>
    <?php $this->head() ?>
</head>
```

##License

Extension is released under MIT license.