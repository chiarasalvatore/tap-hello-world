### Deploying to TAP

If you make modifications to the source and push to your own Git repository, then you can update the `spec.source.git` information in the `config/workload.yaml` file.

You can deploy and use the `config/workload.yaml` file to set the initial message:

```bash
tanzu apps workload apply -f config/workload.yaml
```

If you would like deploy the code from tyour local working directory you can use the following command:

```bash
tanzu apps workload create hello-world -f config/workload.yaml \
  --local-path . \
  --source-image <REPOSITORY-PREFIX>/hello-world-source \
  --type web
```

## Accessing the app deployed to your cluster

Determine the URL to use for the accessing the app by running:

```
tanzu apps workload get hello-world
```

To access the deployed app use the URL shown under "Workload Knative Services".

Then, use `curl` or some other utility to access the URL:

```
curl <URL>
```

This depends on the TAP installation having DNS configured for the Knative ingress.
