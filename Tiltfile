allow_k8s_contexts('gke_csplayground-354114_europe-west1_demo-inps')
SOURCE_IMAGE = os.getenv("SOURCE_IMAGE", default='source-image-location')
LOCAL_PATH = os.getenv("LOCAL_PATH", default='/Users/schiara/Documents/GitHub/tap-hello-world')
NAMESPACE = os.getenv("NAMESPACE", default='dev')

k8s_custom_deploy(
    'hello-world',
    apply_cmd="tanzu apps workload apply -f config/workload.yaml --debug --live-update" +
        " --local-path " + LOCAL_PATH +
        " --source-image " + SOURCE_IMAGE +
        " --namespace " + NAMESPACE +
        " --yes >/dev/null" +
        " && kubectl get workload hello-world-live-update --namespace " + NAMESPACE + " -o yaml",
    delete_cmd="tanzu apps workload delete -f config/workload.yaml --namespace " + NAMESPACE + " --yes" ,
    deps=['pom.xml', './target/classes'],
    container_selector='workload',
    live_update=[
        sync('./target/classes', '/workspace/BOOT-INF/classes')
    ]
)

k8s_resource('hello-world', port_forwards=["8080:8080"],
    extra_pod_selectors=[{'serving.knative.dev/service': 'hello-world-live-update'}])