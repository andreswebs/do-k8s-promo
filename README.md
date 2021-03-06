# do-k8s-promo

## TODO:

- digital ocean promotheus on the managed cluster (https://yetiops.net/posts/prometheus-service-discovery-digitalocean/)
- dashboard using grafana showing something fun

## Pre-Requisites

1. Install [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)

2. Install [Terragrunt](https://terragrunt.gruntwork.io/docs/getting-started/install/)

3. Install [doctl](https://www.digitalocean.com/docs/apis-clis/doctl/how-to/install/)

4. (Optionally) Install [s3cmd](https://github.com/s3tools/s3cmd/blob/master/INSTALL.md)


5. Add a valid Digital Ocean API token to a `.tfvars` file, e.g. `terraform.tfvars`:

```hcl
do_token = "hextokenfromdigitalocean"
```

## Deploy

```sh
terragrunt init
terragrunt plan
terragrunt apply
```

## Get kube config

This example saves the kube config to a file at the root of the project.

(Files named `*.kubeconfig.yml` are being ignored by `.gitignore`.)

```sh
export CLUSTER_NAME="k8s"
export KUBECONFIG_BAK="$KUBECONFIG"
export KUBECONFIG=./do-k8s.kubeconfig.yml
doctl kubernetes cluster kubeconfig save "$CLUSTER_NAME"
```

## References

<https://www.padok.fr/en/blog/digitalocean-kubernetes>
