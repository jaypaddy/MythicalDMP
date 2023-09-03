# MythicalDMP

az ad sp create-for-rbac --name MythicalAliceSpringsPP1_SPN --role owner --scopes /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361/resourceGroups/MythicalISAFactory_RG
az role assignment create --assignee fe7c4322-bd6e-4564-a830-20d2639fc9d9 --role "Kubernetes Cluster - Azure Arc Onboarding" --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361 

az policy assignment create  --name 'AzureArck8s Azure Policy extension'  --display-name 'Configure Azure Arc enabled Kubernetes clusters to install the Azure Policy extension Assignment' --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361/resourceGroups/dmpcloudcoredevarcrg --policy '0adc5395-9169-4b9b-8687-af838d69410a' --mi-system-assigned --location eastus

          az policy assignment create --name 'DMPEdge Install Flux extension on Kubernetes cluster' --display-name 'Configure installation of Flux extension on Kubernetes cluster Assignment' --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361/resourceGroups/dmpcloudcoredevarcrg --policy 'f9175d5f-abc8-1dc3-bd3c-5d7476ada3d1'  --mi-system-assigned --location EastUS

az policy definition list --query "[?displayName=='Azure Arc enabled Kubernetes clusters should have the Azure Policy extension installed']"

az policy definition list --query "[?displayName=='Configure installation of Flux extension on Kubernetes cluster']"


          #az k8s-configuration flux create --name dmp-gitops-flux-config --cluster-name mythicalnuc --namespace dmpfoundations-ns  --resource-group MythicalAliceSpringsPP1_RG --url "https://dev.azure.com/mythicaljaypaddy/MythicalDMP/_git/MythicalDMPGitopsDev" --https-user mythicaljaypaddy --https-key 5ndcjihajpu2qeccdvctkbopapmu7y3zmneubh76i6fn3higxgda --scope cluster --cluster-type connectedClusters --branch main --kustomization name=dmpfoundations prune=true path=/DMPFoundations/All 

          az k8s-configuration flux kustomization create --resource-group MythicalAliceSpringsPP1_RG --cluster-name mythicalnuc --cluster-type connectedClusters  --name dmp-gitops-flux-config --kustomization-name platform --path /mythicalnuc/platform --prune=true --depends-on dmpfoundations
          az k8s-configuration flux kustomization create --resource-group MythicalAliceSpringsPP1_RG --cluster-name mythicalnuc --cluster-type connectedClusters  --name dmp-gitops-flux-config --kustomization-name apps --path /mythicalnuc/apps --prune=true --depends-on platform


az k8s-configuration flux create --name gitops-flux-config --cluster-name $clustername --namespace gitops-flux-config-ns --resource-group $resourcegroup --url $gitopsurl --https-user $gitopsusername --https-key $gitopspatkey --scope cluster --cluster-type connectedClusters --branch master --kustomization name=platform prune=true path=/Platform --kustomization name=apps path=/$clustername prune=true dependsOn=\["platform"\]


