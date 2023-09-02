# MythicalDMP

az ad sp create-for-rbac --name MythicalAliceSpringsPP1_SPN --role owner --scopes /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361/resourceGroups/MythicalISAFactory_RG
az role assignment create --assignee fe7c4322-bd6e-4564-a830-20d2639fc9d9 --role "Kubernetes Cluster - Azure Arc Onboarding" --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361

az policy assignment create  --name 'AzureArck8s Azure Policy extension'  --display-name 'Configure Azure Arc enabled Kubernetes clusters to install the Azure Policy extension Assignment' --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e36/resourceGroups/dmpcloudcoredevarcrg --policy '/providers/Microsoft.Authorization/policyDefinitions/6b2122c1-8120-4ff5-801b-17625a355590'

az policy assignment create --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361/resourceGroups/dmpcloudcoredevarcrg --policy /providers/Microsoft.Authorization/policyDefinitions/f9175d5f-abc8-1dc3-bd3c-5d7476ada3d1

az policy definition list --query "[?displayName=='Azure Arc enabled Kubernetes clusters should have the Azure Policy extension installed']"

az policy definition list --query "[?displayName=='Configure installation of Flux extension on Kubernetes cluster']"