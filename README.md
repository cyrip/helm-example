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

## Push package
```sh
helm cm-push laravel1-0.1.0.tgz http://charts.codeware.local
```

## Lint and package
```sh
helm lint laravel1/
helm package laravel1/
```

## Install package
```sh
helm repo update
helm install laravel1 codeware/laravel1 --namespace laravel-app
```

## Upgrade package
```sh
helm --namespace laravel-app upgrade -i laravel1 codeware/laravel1 --set autoscaling.enabled=true --reuse-values
```
