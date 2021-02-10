# 4kube

# Création du namespace:

kubectl create namespace tp-4kube

# Création des service et du volume persistent et du deployment via le YAML deployment.yaml:

kubectl apply -f deployment.yaml


# Deployment MariaDB via YAML deploymentMariaDB.yaml:

kubectl apply -f deploymentMariaDB.yaml

# ConfigMap MariaDB via YAML deploymentDB.yaml:

kubectl apply -f deploymentDB.yaml


# ConfigMap PrestaShop via YAML ConfigMapPresta.yaml:

kubectl apply -f ConfigMapPresta.yaml

# Création d’un secret pour prestashop via le YAML secret.yaml:

kubectl apply -f secret.yaml

# Création d’un secret pour MariaDB via le YAML secretDB.yaml:

kubectl apply -f secretDB.yaml




## Installation de l’outil FluxCTL:

brew install fluxctl

# Création du namespace Flux:

kubectl create ns flux

# Installation de Flux dans le cluster:

export GHUSER="hz59"
fluxctl install \
> --git-user=${GHUSER} \
> --git-email=${GHUSER}@users.noreply.github.com \
> --git-url=git@github.com:${GHUSER}/flux-get-started \
> --git-path=namespaces,workloads \
> --namespace=flux | kubectl apply -f -


# Création de la clé SSH flux à copier et coller dans le git pour synchroniser à Git:

fluxctl identity --k8s-fwd-ns flux




