# hello-world

This repo provides a simple Hello World sample project for Spring Boot on Cloud Foundry

It can be deployed as a standalone web app, as a Cloud Foundy app with r without the provided `manifest.yml` file.

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

### Pushing to Cloud Foundry

You can deploy and use the `manifest.yml` file to set the initial message:

```bash
./mvnw package  
cf push hello-world -p target/hello-world-0.0.1-SNAPSHOT.jar -f manifest.yml --random-route
```

When deploying without the `manifest.yml` you can use the following commands:

```bash
./mvnw package  
cf push hello-world -p target/hello-world-0.0.1-SNAPSHOT.jar -f manifest.yml --random-route
```

Then, when you want to update the message you can set the env var `APP_MESSAGE` using:

```
cf set-env hello-world APP_MESSAGE 'Cloud Foundry'
cf restage hello-world
```

### Accessing the deployed app

Determine the route for the app by running:

```
cf app hello-world
```

Then, use `curl` or some other utility to access the route:

```
curl <route-for-hello-world>
```

### Deleting the Cloud Foundy app

You can delete the running app using:

```
cf delete hello-world
```
