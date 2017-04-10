# metrics-k8s
*A basic metrics project built with patternfly*

[![npm dependency statuses](http://img.shields.io/david/ryanj/http-base.svg "npm dependencies, via david-dm")](https://david-dm.org/ryanj/http-base)
[![Available on Quay](https://quay.io/repository/ryanj/metrics-k8s/status "container image available on Quay")](https://quay.io/repository/ryanj/metrics-k8s)

## GitHub Pages
Fork to run, push to publish:

1. Use your GitHub account to create a fork of [ryanj/metrics-k8s](http://github.com/ryanj/metrics-k8s/)
2. View your resulting [`gh-pages`](http://pages.github.com) site by replacing **"ryanj"** with your github username or orgname in the following URL: 
    > https://ryanj.github.io/metrics-k8s
3. Publish updates by adding commits to your hosted `gh-pages` branch

## Local Development
For local development environment, clone the repo and run:

```bash
npm start
```

## Docker
Container images are automatically built at [quay.io/ryanj/metrics-k8s](http://quay.io/ryanj/metrics-k8s) whenever changes are merged into [`github.com/ryanj/metrics-k8s:master`](https://github.com/ryanj/metrics-k8s/tree/master)

To make the container image available at [`localhost:8088`](http://localhost:8088/), run:
```bash
docker run -p 8088:2015 -it quay.io/ryanj/metrics-k8s
```

Or, use docker to preview your changes (pre-commit/pre-build) by mounting your local repo clone into the container at `/var/www/html`:
```bash
docker run -p 8088:2015 -v /path/to/metrics-k8s:/var/www/html:ro -it quay.io/ryanj/metrics-k8s 
```

## Kubernetes
To create a kubernetes `deployment` and a "NodePort" `service`, both named `metrics-k8s`, run:

```bash
kubectl run metrics-k8s --image=quay.io/ryanj/metrics-k8s \
--expose --port=2015 --service-overrides='{ "spec": { "type": "NodePort" } }'
```

Minikube users will be able to open the resulting service in their browser by running:
```bash
minikube service metrics-k8s
```

## License: MIT
