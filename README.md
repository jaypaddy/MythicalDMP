# MythicalDMP

az ad sp create-for-rbac --name MythicalAliceSpringsPP1_SPN --role owner --scopes /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361/resourceGroups/MythicalISAFactory_RG
az role assignment create --assignee fe7c4322-bd6e-4564-a830-20d2639fc9d9 --role "Kubernetes Cluster - Azure Arc Onboarding" --scope /subscriptions/d0272d81-bf47-4f2b-b8dc-c56cb783e361