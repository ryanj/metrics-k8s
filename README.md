# metrics-k8s
*A basic metrics project built with patternfly*

## Local Development
For local development environment, clone the repo and run:

```bash
npm start
```

## GitHub Pages
Fork to run, push to publish:

1. Use your GitHub account to create a fork of [ryanj/metrics-k8s](http://github.com/ryanj/metrics-k8s/)
2. View your resulting [`gh-pages`](http://pages.github.com) site by replacing **"ryanj"** with your github username or orgname in the following URL: 
    > https://ryanj.github.io/metrics-k8s
3. Publish updates by adding commits to your hosted `gh-pages` branch

## Kubernetes
To create a kubernetes `deployment` and a "NodePort" `service`, both named `metrics-k8s`, run:

```bash
kubectl run metrics-k8s --image=quay.io/ryanj/metrics-k8s \
--expose --port=8080 --service-overrides='{ "spec": { "type": "NodePort" } }'
```

Minikube users will be able to open the resulting service in their browser by running:
```bash
minikube service metrics-k8s
```

## Docker
Container images are automatically built on [quay.io](http://quay.io/ryanj/metrics-k8s) whenever changes are merged into [`ryanj/metrics-k8s:master`](https://github.com/ryanj/metrics-k8s/tree/master)

To make the container image available at [`localhost:8088`](http://localhost:8088/), run:
```bash
docker run -p 8088:8080 -it quay.io/ryanj/metrics-k8s
```

#### License: MIT
