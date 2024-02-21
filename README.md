This repository allows us to create a GKE cluster with Terraform as well as destroy it, all with GitHub Actions workflow.

We need to set up a google service account with permissions to manage the GKE clusters first, then add the credentials (they come in a json file) to a Github secret.

Assuming the cluster does not yet exist, we just need to add in the commit message the keyword 'terraform' for it to run the plan job. We must then manually validate the apply job, this is a failsafe measure to prevent disasters :wink: .

This repository was also used to deploy an argocd server to that cluster with `helm upgrade -i argo-cd argo/argo-cd -n argo-cd --create-namespace`

Which can then be configured to manage the helloworld app that also lies in this repository.

We can change the specs for our cluster in <terraform/gke.tf`> and we must also set the <project_id> in the <terraform/terraform.tfvars> file to our own. Region can also be changed there.
