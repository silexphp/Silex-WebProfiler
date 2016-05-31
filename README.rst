Silex Web Profiler
==================

The Silex Web Profiler service provider allows you to use the wonderful Symfony
web debug toolbar and the Symfony profiler in your Silex 2.x application.

.. note::

    If you are using the 1.x Silex version, read the `specific documentation
    <https://github.com/silexphp/Silex-WebProfiler/tree/1.0>`_.

To install this library, run the command below and you will get the latest
version:

.. code-block:: bash

    composer require 'silex/web-profiler:^2.0'

And enable it in your application:

.. code-block:: php

    use Silex\Provider;

    $app->register(new Provider\WebProfilerServiceProvider(), array(
        'profiler.cache_dir' => __DIR__.'/../cache/profiler',
        'profiler.mount_prefix' => '/_profiler', // this is the default
    ));

The provider depends on ``ServiceControllerServiceProvider``,
``TwigServiceProvider``, and ``HttpFragmentServiceProvider`` so you also need
to enable those if that's not already the case:

.. code-block:: php

    $app->register(new Provider\HttpFragmentServiceProvider());
    $app->register(new Provider\ServiceControllerServiceProvider());
    $app->register(new Provider\TwigServiceProvider());

If you are using ``FormServiceProvider``, the ``WebProfilerServiceProvider``
will detect that and enable the corresponding panels.

*Make sure to register all other required or used service providers before*
``WebProfilerServiceProvider``.

If you are using ``MonologServiceProvider`` for logs, you must also add
``symfony/monolog-bridge`` as a Composer dependency to get the
logs in the profiler.

If you are using ``VarDumperServiceProvider``, add ``symfony/debug-bundle`` as
a Composer dependency to display VarDumper dumps in the toolbar and the
profiler.
