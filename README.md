# A basic Hapi.js and Express API following Clean Architecture principies

[Documentation](https://drive.google.com/file/d/1jvU3WTgfNzdoYi1LYB0IBKl0UsDZm9Y9/view?usp=sharing)

## Domain Driven Architectures

Boilerplate template made with DDD

One of the first and main ones was introduced by E. Evans in its [Domain Driven Design approach](http://dddsample.sourceforge.net/architecture.html).

![DDD Architecture](just-eat-hexagonal/doc/DDD_architecture.jpg)

![Boilerplate] (https://github.com/jbuget/nodejs-clean-architecture-app)
Based on [Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/) (by. J. Palermo), [Hexagonal Architecture](https://alistair.cockburn.us/hexagonal-architecture/) (by A. Cockburn) or [Clean Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (by. R. Martin).

 

### Estructura
```
front-just-eat    → Aplicación FrontEnd en ReactJS
Just-eat  → Application backend con Express
just-eat-hexagonal  → Application backend con hapiJS usando arquitectura hexagonal y DDD
```

```
app 
 └ lib                              → Application sources 
    └ application                   → Application services layer
       └ security                   → Security tools interfaces (ex: AccessTokenManager.js, to generate and decode OAuth access token)
       └ use_cases                  → Application business rules 
    └ domain                        → Enterprise core business layer such as domain model objects (Aggregates, Entities, Value Objects) and repository interfaces
    └ infrastructure                → Frameworks, drivers and tools such as Database, the Web Framework, mailing/logging/glue code etc.
       └ config                     → Application configuration files, modules and services
          └ service-locator.js      → Module that manage service implementations by environment
       └ orm                        → Database ORMs middleware (Sequelize for SQLite3 or PostgreSQL, Mongoose for MongoDB)
          └ mongoose                → Mongoose client and schemas
          └ sequelize               → Sequelize client and models
       └ repositories               → Implementation of domain repository interfaces
       └ security                   → Security tools implementations (ex: JwtAccessTokenManager)
       └ webserver                  → Hapi.js Web server configuration (server, routes, plugins, etc.)
          └ oauth                   → Hapi.js authentication strategies and schemas
          └ server.js               → Hapi.js server definition
    └ interfaces                    → Adapters and formatters for use cases and entities to external agency such as Database or the Web
       └ controllers                → Hapi.js route handlers
       └ routes                     → Hapi.js route definitions
       └ serializers                → Converter objects that transform outside objects (ex: HTTP request payload) to inside objects (ex: Use Case request object)
 └ node_modules (generated)         → NPM dependencies
 └ test                             → Source folder for unit or functional tests
 └ index.js                         → Main application entry point
```

### Flujo

![Schema of flow of Control](just-eat-hexagonal/doc/Hapijs_Clean_Architecture.svg)

