### Pushing to Cloud Foundry

You can deploy and use the `config/manifest.yml` file to set the initial message:

```bash
./mvnw package  
cf push hello-world -p target/hello-world-0.0.1-SNAPSHOT.jar -f config/manifest.yml --random-route
```

When deploying without the `manifest.yml` you can use the following commands:

```bash
./mvnw package  
cf push hello-world -p target/hello-world-0.0.1-SNAPSHOT.jar --random-route
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
