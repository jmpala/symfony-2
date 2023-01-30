# Symfony

## Components

- Services
- Bundles
- Configuration
- Environments
- Environment Variables

## Bundles

- Are Symfony plugins and give us services
- Hook into the Symfony framework,and we can retrieve services through autowiring
- There are Symfony libraries that are not bundles, thus don't hook by themselves, still are detected by Symfony's "FrameworkBundle"

## Services

- We can see registered services on path "/config/bundles.php"
- With command "php.exe bin/console debug:container" we can see all services

## Useful Services

- http-client (make http requests)

## Configuration

- We can see configuration on path "/config/packages" (for services)
- "/config/packages" defines how services are going to be instantiated
- The names of the configuration files are not relevant, the name of the properties are
- We can have all the properties inside one file if we wanted to
- When the same property appears more than one time, the order of the properties is relevant

## Autowiring

- The container is responsible for containing all app instances and injecting them into where they are needed
- A service that is not a class or interface name, is not autowireable
- Autowiring works on the constructor and controller methods
- We can configure how DI Injection works inside "services.yaml"
- The "_defaults" property configures the default behavior for all services "inside the file!!!"
- We can bind values to a service with "bind" property, followed by the controller parameter name and the value
- We can use #[Autowire(servive: "service_name")] to autowire any service

## Parameters 

- Are values contained in the DI container
- We can access them with "%parameter_name%" on the yaml config files
- or $this->getParameter("parameter_name") on the php controllers
- We can see the parameters with "php bin/console debug:container --parameters"
- We can autowire parameters with #[Autowire('kernel.debug')]

## Environments

- We can have different environments, like "dev", "prod", "test", etc
- We can set the config environment with directories or withing files
- On directories, we can use "./config/packages/{env}/*"
- Within files, we can use "when@{env}:"
- cache lives inside "./var/cache/{env}"
- we can use the flag --env={env} to run commands on a certain environment (need to clear cache first)
- we can "modify" an environment variable with the "environment variable processors" (https://symfony.com/doc/current/configuration/env_var_processors.html)

### Prod Environment

- The cache is not refreshed on changes, we need to manually clear the cache
- php bin/console cache:clear (we clear the cache)

### Dev Environment

- The cache is refreshed on changes, Symfony is smart enough to detect changes on files and refresh the cache
- The .env files are hierarchically loaded
- We can see the environment variables with command "php bin/console debug:dotenv"

### Symfony Secrets Vault

- We can store secrets in the vault
- They are safe to store in the repository
- We need one for each environment, dev&prod

## Useful Commands

- php bin/console debug:autowiring (show all autowireable services)
- php bin/console debug:container (show low level information about services)
- php bin/console debug:config [bundle name] (show all possible configuration)
- php bin/console config:dump [bundle name] (show all current configuration)
- php bin/console debug:container (show all services that are registered in the container, not all are autowireable)
- php bin/console cache:clear (we clear the cache)
- php bin/console cache:warmup (clears and rebuilds the cache)#
- php bin/console debug:container --parameters (show all parameters)
- php bin/console debug:dotenv (environment files & variables information)

## Deplyoment

1. Get the code from the repository to the server
2. Install dependencies with composer
3. Create .env.local file with the environment variables (only when no possibility to store env vars on OS)
4. run "php bin/console cache:clear"
5. run "php bin/console cache:warmup"
