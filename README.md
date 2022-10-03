# ghw-terrapipe

## Repo Secrets 
This Action requires terraform to have permission to work on the target environment.
Therefore it will INHERIT the secrets from the hosting repository, to complete this action.

The following secrets are therefore required on the repository which uses this action

| Github Secret                       | Description    | Sample |
| ---------------------- | --- |---|
| AZURE_AD_CLIENT_ID     | ObjectId of the Service Principal    ||
| AZURE_AD_CLIENT_SECRET | Secret from the Service Principal    ||
| AZURE_SUBSCRIPTION_ID  | Any subscription the Service has access to, used to ensure correct context, as the principal may have access to multiple tenancy, or used in lighthouse    ||
| AZURE_AD_TENANT_ID     | Tenant ID the Service Principal was created in    ||
| ACF_REF_AZ_MODULE_ARTIFACT_STORAGE_CONNECTION | Connection string to blob storage account |BlobEndpoint=https://name.blob.core.windows.net/;QueueEndpoint=https://name.queue.core.windows.net/;FileEndpoint=https://name.file.core.windows.net/;TableEndpoint=https://name.table.core.windows.net/;SharedAccessSignature=sv=2021-21-21&ss=b&srt=sco&sp=rwdlacitfx&se=2025-25-25T01:01:01Z&st=2022-07-07T01:01:01Z&spr=https&sig=QbrdrRr99e7Y6kfcgK8V5iJQSSdiN5NspASAqDcHe0l%3D|

## Input Variables

The Action has the following inputs
| Input Variables                       | Description   |Required | Sample |
| ---------------------- | --- |---|
| repo-token     | The Action requires access to the calling repo, pass it your github_token   | Yes | `repo-token: ${{ github.token }}` |
