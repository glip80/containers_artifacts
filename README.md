# Containers 2.0 Openhack

<!-- 
Guidelines on README format: https://review.docs.microsoft.com/help/onboard/admin/samples/concepts/readme-template?branch=master

Guidance on onboarding samples to docs.microsoft.com/samples: https://review.docs.microsoft.com/help/onboard/admin/samples/process/onboarding?branch=master

Taxonomies for products and languages: https://review.docs.microsoft.com/new-hope/information-architecture/metadata/taxonomies?branch=master
-->

This repo houses the source code and dockerfiles for the Containers OpenHack event.

The application used for this event is a heavily modified and recreated version of the original [My Driving application](https://github.com/Azure-Samples/MyDriving).

## Contents

| File/folder       | Description                                |
|-------------------|--------------------------------------------|
| `.devcontainer`   | VS Code [development container](https://code.visualstudio.com/docs/remote/containers) with useful utils (Azure CLI, Kubectl, Helm, etc.)   |
| `dockerfiles`     | Dockerfiles for source code                |
| `src`             | Sample source code for POI, Trips, User (Java), UserProfile (Node.JS), and TripViewer                     |
| `.gitignore`      | Define what to ignore at commit time.      |
| `CODE_OF_CONDUCT.md` | Code of conduct.                        |
| `LICENSE`         | The license for the sample.                |

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.


docker run --network my-network -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=coder!5123" -p 1433:1433 --name sql_server_container -d mcr.microsoft.com/mssql/server
docker run --network my-network -e "ACCEPT_EULA=Y" -e SQLUSER=sa -e SQLPASS=coder!5123 -e SQLDB=mydrivingDB registrynbu1374.azurecr.io/dataload:1.0
docker run --network my-network -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=coder!5123" -e SQLDB=mydrivingDB registrynbu1374.azurecr.io/dataload:1.0

    docker run --network <networkname> -e SQLFQDN=<servername> -e SQLUSER=<db-user> -e SQLPASS=<password> -e SQLDB=mydrivingDB <your-registry>.azurecr.io/dataload:1.0
    docker run --network <networkname> -e SQLFQDN=<servername> -e SQLUSER=<db-user> -e SQLPASS=<password> -e SQLDB=mydrivingDB <your-registry>.azurecr.io/dataload:1.0


docker network create my-network


docker run --network my-network -e SQLFQDN=localhost -e SQLUSER=sa -e SQLPASS=coder!5123 -e SQLDB=mydrivingDB registrynbu1374.azurecr.io/dataload:1.0

docker run --network my-network -e SQLPASS=coder!5123 -e SQLUSER=sa -e SQLDB=mydrivingDB registrynbu1374.azurecr.io/dataload:1.0

docker run --network my-network -e SQLFQDN=sql_server_container -e SQLUSER=sa -e SQLPASS=coder!5123 -e SQLDB=mydrivingDB registrynbu1374.azurecr.io/dataload:1.0


docker build --no-cache --build-arg IMAGE_VERSION="1.0" --build-arg IMAGE_CREATE_DATE="$(Get-Date((Get-Date).ToUniversalTime()) -UFormat '%Y-%m-%dT%H:%M:%SZ')" --build-arg IMAGE_SOURCE_REVISION="$(git rev-parse HEAD)" -f Dockerfile -t "tripinsights/poi:1.0" .


docker run -d -p 8080:80 --name poi -e "SQL_PASSWORD=coder!5123" -e "SQL_SERVER=sql_server_container" -e "ASPNETCORE_ENVIRONMENT=Production" tripinsights/poi:1.0
docker run --network my-network -d -p 8081:80 --name poi_dev -e "SQL_PASSWORD=$SQL_PASSWORD" -e "SQL_SERVER=$SQL_SERVER" -e "ASPNETCORE_ENVIRONMENT=Production" tripinsights/poi:1.0

docker run --network my-network -d -p 8080:80 --name poi -e "SQL_PASSWORD=coder!5123" -e "SQL_SERVER=sql_server_container" -e "ASPNETCORE_ENVIRONMENT=Production" tripinsights/poi:1.0


docker tag poi_table_3_5 registrynbu1374.azurecr.io/poi_table_3_5:latest

docker push registrynbu1374.azurecr.io/poi_table_3_5:latest

docker build --no-cache --build-arg IMAGE_VERSION="1.0" --build-arg IMAGE_CREATE_DATE="$(Get-Date((Get-Date).ToUniversalTime()) -UFormat '%Y-%m-%dT%H:%M:%SZ')" --build-arg IMAGE_SOURCE_REVISION="$(git rev-parse HEAD)" -f Dockerfile -t "registrynbu1374.azurecr.io/tripinsights/tripviewer.api:1.0" .

docker build --no-cache --build-arg IMAGE_VERSION="1.0" --build-arg IMAGE_CREATE_DATE="$(Get-Date((Get-Date).ToUniversalTime()) -UFormat '%Y-%m-%dT%H:%M:%SZ')" --build-arg IMAGE_SOURCE_REVISION="$(git rev-parse HEAD)" -f Dockerfile -t "registrynbu1374.azurecr.io/tripinsights/trips.api:1.0" .

docker build --no-cache --build-arg IMAGE_VERSION="1.0" --build-arg IMAGE_CREATE_DATE="$(Get-Date((Get-Date).ToUniversalTime()) -UFormat '%Y-%m-%dT%H:%M:%SZ')" --build-arg IMAGE_SOURCE_REVISION="$(git rev-parse HEAD)" -f Dockerfile -t "registrynbu1374.azurecr.io/userj_table_3_5:1.0" .


docker build --no-cache --build-arg IMAGE_VERSION="1.0" --build-arg IMAGE_CREATE_DATE="$(Get-Date((Get-Date).ToUniversalTime()) -UFormat '%Y-%m-%dT%H:%M:%SZ')" --build-arg IMAGE_SOURCE_REVISION="$(git rev-parse HEAD)" -f Dockerfile -t "registrynbu1374.azurecr.io/tripviewer_table_3_5:1.0" .

docker build --no-cache --build-arg IMAGE_VERSION="1.0" --build-arg IMAGE_CREATE_DATE="$(Get-Date((Get-Date).ToUniversalTime()) -UFormat '%Y-%m-%dT%H:%M:%SZ')" --build-arg IMAGE_SOURCE_REVISION="$(git rev-parse HEAD)" -f Dockerfile -t "registrynbu1374.azurecr.io/userprofile_table_3_5:1.0" .

kubectl create secret generic dev-db-secret --from-literal=sql='Server=tcp:sqlservernbu1374.database.windows.net,1433;Initial Catalog=mydrivingDB;Persist Security Info=False;User ID=sqladminnBu1374;Password=myPassword123!;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;'


Server=tcp:sqlservernbu1374.database.windows.net,1433;Initial Catalog=mydrivingDB;Persist Security Info=False;User ID=sqladminnBu1374;Password=myPassword123!;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;

docker run -e SQLFQDN=sqlservernbu1374.database.windows.net -e SQLUSER=sqladminnBu1374 -e SQLPASS=myPassword123! -e SQLDB=mydrivingDB registrynbu1374.azurecr.io/dataload:1.0


kubectl create secret generic dev-trips-secret --from-literal=sql_password='myPassword123!' --from-literal sql_user='sqladminnBu1374'

#3

kubectl create namespace web-dev
kubectl create namespace api-dev

kubectl create secret generic dev-trips-secret --from-literal=sql_password='myPassword123!' --from-literal sql_user='sqladminnBu1374' -n api-dev

kubectl apply -f .\src\aks\poi.yml -n api-dev
kubectl apply -f .\src\aks\trips.yml -n api-dev
kubectl apply -f .\src\aks\user-java.yml -n api-dev
kubectl apply -f .\src\aks\userprofile.yml -n api-dev
kubectl apply -f .\src\aks\tripviewer.yml -n web-dev

kubectl exec --stdin --tty tripinsights-tripviewer-9fb54485d-66kzp -n web-dev -- /bin/sh

sed -i 's/<subscription-id>/420573c6-de7a-4585-b9ce-34dd795a83ac/g' kv-flexvol-installer.yaml
sed -i 's/<keyvault-name>/challenge4keyvault/g' kv-flexvol-installer.yaml


export RESOURCE_GROUP='teamResources'
export UAMI='challenge4UAMI'
export KEYVAULT_NAME=challenge4Keyvault
export CLUSTER_NAME=Challenge3


# az keyvault create --location eastasia --name $KEYVAULT_NAME --resource-group $RESOURCE_GROUP
# az identity create --name $UAMI --resource-group $RESOURCE_GROUP
export USER_ASSIGNED_CLIENT_ID="$(az identity show -g $RESOURCE_GROUP --name $UAMI --query 'clientId' -o tsv)"
export IDENTITY_TENANT=$(az aks show --name $CLUSTER_NAME --resource-group $RESOURCE_GROUP --query identity.tenantId -o tsv)

# az keyvault set-policy -n $KEYVAULT_NAME --key-permissions get --spn $USER_ASSIGNED_CLIENT_ID
# az keyvault set-policy -n $KEYVAULT_NAME --secret-permissions get --spn $USER_ASSIGNED_CLIENT_ID
# az keyvault set-policy -n $KEYVAULT_NAME --certificate-permissions get --spn $USER_ASSIGNED_CLIENT_ID

# az keyvault secret set --name sqluser --vault-name $KEYVAULT_NAME --value sqladminnBu1374
# az keyvault secret set --name sqlpassword --vault-name $KEYVAULT_NAME --value myPassword123!
export AKS_OIDC_ISSUER="$(az aks show --resource-group $RESOURCE_GROUP --name $CLUSTER_NAME --query "oidcIssuerProfile.issuerUrl" -o tsv)"
export SERVICE_ACCOUNT_NAME="workload-identity-sa"  # sample name; can be changed
export SERVICE_ACCOUNT_NAMESPACE="api-dev" # can be changed to namespace of your workload


export FEDERATED_IDENTITY_NAME="aksfederatedidentity" # can be changed as needed
az identity federated-credential create --name $FEDERATED_IDENTITY_NAME --identity-name $UAMI --resource-group $RESOURCE_GROUP --issuer ${AKS_OIDC_ISSUER} --subject system:serviceaccount:${SERVICE_ACCOUNT_NAMESPACE}:${SERVICE_ACCOUNT_NAME}