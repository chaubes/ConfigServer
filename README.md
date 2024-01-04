
# Sample Spring Cloud Config Server

## Overview
Spring Cloud Config Server provides a centralized external configuration management backed by a Git repository. It's designed to work well with Spring Boot applications but can be used with any application working with Spring Cloud.

### Configuration Repository
The configuration server is backed by a Git repository. You need to specify the URI of the repository in the `application.yaml` file of the config server.
Update the URI and other parameters as needed.

Example `application.yaml`:
```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/chaubes/config-server-properties.git
          searchPaths: 'config/{application}/{profile}'
          cloneOnStart: true
          default-label: master
          force-pull: true
          timeout: 10
```

### Basic Authentication
For basic authentication, update the `application.yaml` to include the security configuration. Update the user-password as needed.

Example `application.yaml`:
```yaml
spring:
  security:
    user:
      name: admin
      password: admin
```

## Accessing Configurations
Once the server is up and running, configurations can be accessed via HTTP requests. The default port is `8888`.

Example:
```bash
curl http://localhost:8888/app1/sit
```
## Further Customization
You can further customize the server by modifying the `application.yaml` file. Refer to the [official documentation](https://cloud.spring.io/spring-cloud-config/reference/html/) for more details.
A postman collection is also included in the repository for quick testing.