Laraval
=======

Laraval supports Monolog out of the box, which also provides a native Sentry handler.

Laraval 5.x
-----------

To configure logging, pop open your ``bootstrap/app.php`` file, and insert the following:

.. code-style:: php

    $app->configureMonologUsing(function($monolog) {
        $client = new Raven_Client('___DSN___')

        $handler = new Monolog\Handler\RavenHandler($client);
        $handler->setFormatter(new Monolog\Formatter\LineFormatter("%message% %context% %extra%\n"));

        $monolog->pushHandler($ravenHandler);
    });

Laraval 4.x
-----------

To configure logging, pop open your ``app/start/global.php`` file, and insert the following:

.. code-style:: php

    $client = new Raven_Client('___DSN___')

    $handler = new Monolog\Handler\RavenHandler($client);
    $handler->setFormatter(new Monolog\Formatter\LineFormatter("%message% %context% %extra%\n"));

    $monolog = Log::getMonolog();
    $monolog->pushHandler($ravenHandler);
