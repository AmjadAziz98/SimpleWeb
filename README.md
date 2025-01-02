# SimpleWeb
Simple Web site

## Deployment Instructions

To deploy the website to Azure, follow these steps:

1. Clone the repository to your local machine.
2. Navigate to the repository directory.
3. Ensure you have the Azure CLI installed and logged in.
4. Run the following command to create a resource group:
   ```
   az group create --name myResourceGroup --location "East US"
   ```
5. Run the following command to create an App Service plan:
   ```
   az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --sku FREE
   ```
6. Run the following command to create a web app:
   ```
   az webapp create --name myWebApp --resource-group myResourceGroup --plan myAppServicePlan
   ```
7. Deploy the website using the following command:
   ```
   az webapp up --name myWebApp --resource-group myResourceGroup
   ```

## Configuring Azure Credentials

To configure Azure credentials, follow these steps:

1. Create a service principal using the Azure CLI:
   ```
   az ad sp create-for-rbac --name "myServicePrincipal" --role contributor --scopes /subscriptions/{subscription-id}/resourceGroups/myResourceGroup
   ```
2. Note down the `appId`, `password`, and `tenant` values from the output.
3. Set the following GitHub secrets in your repository:
   - `AZURE_CLIENT_ID`: The `appId` value from the service principal.
   - `AZURE_CLIENT_SECRET`: The `password` value from the service principal.
   - `AZURE_TENANT_ID`: The `tenant` value from the service principal.
   - `AZURE_WEBAPP_PUBLISH_PROFILE`: The publish profile of your web app.

## Azure Deployment Configuration

For more details, refer to the [azure-deploy.yml](./azure-deploy.yml) file.

## Deployed Website

The website is deployed and can be accessed at the following link:
https://purple-island-047478400.4.azurestaticapps.net/


