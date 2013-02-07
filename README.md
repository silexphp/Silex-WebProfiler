Silex Web Profiler
==================

The Silex Web Profiler service provider allows you to use the wonderful
Symfony web debug toolbar and the Symfony profiler in your Silex application.

To enable it, add this dependency to your `composer.json` file:

    "silex/web-profiler": "1.0.0"

And enable it in your application:

    use Silex\Provider\WebProfilerServiceProvider;

    $app->register($p = new WebProfilerServiceProvider(), array(
        'profiler.cache_dir' => __DIR__.'/../cache/profiler',
    ));
    $app->mount('/_profiler', $p);

The provider depends on `ServiceControllerServiceProvider`, so you also need
to enable it if that's not already the case:

    use Silex\Provider\ServiceControllerServiceProvider;

    $app->register(new ServiceControllerServiceProvider());
