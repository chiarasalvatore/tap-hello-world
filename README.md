# hello-world

This repo provides a simple Hello World sample project for Spring Boot.

It can be deployed as a standalone web app, as a Cloud Foundy app or as a TAP workload, depending on the deployment option choosen when generating the project.

## Deployment

### Standalone app with embedded Tomcat server

You can build the project using Maven:

```bash
./mvnw clean package
```

To run the app using the embedded Tomcat server you can run this command:

```bash
./mvnw spring-boot:run
```

You can modify the default message "World" using an application property of `app.message`:

```bash
./mvnw package  
java -jar target/hello-world-0.0.1-SNAPSHOT.jar --app.message=Test
```

