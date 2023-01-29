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

## Autowiring

- The container is responsible for containing all app instances and injecting them into where they are needed
- A service that is not a class or interface name, is not atowireable

## Environments

- 

## Useful Commands

- php bin/console debug:autowiring (show all autowireable services)
- php bin/console debug:container (show low level information about services)
- php bin/console debug:config [bundle name] (show all possible configuration)
- php bin/console config:dump [bundle name] (show all current configuration)
- php bin/console debug:container (show all services that are registered in the container, not all are autowireable)
