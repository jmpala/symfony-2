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

- We can see configuration on path "/config/packages"
- The names of the configuration files are not relevant, the name of the properties are
- We can have all the properties inside one file if we wanted tocah

## Useful Commands

- php bin/console debug:autowiring (show all services)
- php bin/console debug:container (show low level information about services)
- php bin/console debug:config [bundle name] (show all possible configuration)
- php bin/console config:dump [bundle name] (show all current configuration)
