## Dependency Injection Component

The Dependency Injection Component allows you to implement the dependency injection design pattern.


### Define your services

The most easy way to create a container is to use the `ContainerBuilder`. The `ContainerBuilder` implements the `ContainerInterface`.
````PHP
$containerBuilder = new ContainerBuilder();
````

The `register()` method allows you to register a new service. It returns a `Definition` object.
You can describe `MailerService`'s constructor by adding arguments using `addArgument()`
````PHP
$containerBuilder
    ->register('mailer.service', MailerService::class)
    ->addArgument(new Reference('entity.manager'))
    ->addArgument('SMTP');
````

You can also enable autowiring for the service definition:
````PHP
$containerBuilder
    ->register('entity.manager', EntityManager::class)
    ->setAutowired(true);
````
The `Builder` class will autowire the `Definition` object.
