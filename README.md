# Helm package example

## Install push plugin
```sh
helm plugin install https://github.com/chartmuseum/helm-push.git
```

## Add our own repository
```sh
helm repo add codeware http://charts.codeware.local
helm repo update
```
## Lint and package
```sh
helm lint laravel1/
helm package laravel1/
```
## Push package
```sh
helm cm-push laravel1-0.1.0.tgz http://charts.codeware.local
helm repo update
helm search repo codeware
helm inspect chart codeware/laravel1
helm inspect values codeware/laravel1
```

## Install package
```sh
helm repo update
helm install laravel1 codeware/laravel1 --namespace laravel-app
```

## Upgrade/install package
```sh
helm --namespace laravel-app upgrade -i laravel1 codeware/laravel1 --set autoscaling.enabled=false --set ingress.hosts[0].host="laravel-app.codeware.icu" --set ingress.hosts[0].paths[0].path="/" --set ingress.hosts[0].paths[0].pathType=ImplementationSpecific --reuse-values
helm --namespace laravel-app upgrade -i laravel1 codeware/laravel1 -f values-override.yml --reuse-values
```
