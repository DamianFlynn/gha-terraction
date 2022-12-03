# Terraform Action

## Secrets

The following secrets must be set for this action:

### AZURE_AD_TENANT_ID

The Tenant ID in which the Subscription exists.

### AZURE_AD_CLIENT_ID

The Client ID of the Service Principal used by Terraform.

Must have permission to write to the Terraform state storage account.

### AZURE_AD_CLIENT_SECRET

The Client Secret of the Service Principal.

### AZURE_SUBSCRIPTION_ID

The Subscription ID in which the Terraform state storage account exists.

### INFRACOST_API_KEY

The Infracost API key for calculating cost impact of the Terraform plan.

You can get a free API key or retrieve your existing one from <https://dashboard.infracost.io/> under **Org Settings**.

### TERRAFORM_PLAN_STORAGE_CONNECTION

A connection string to a storage account to use for the Terraform Plan.

It is used to upload and download Terraform plan.

To generate it, open the storage account and go to **Shared access signature**. Allow minimum:

* Allowed services: Blob
* Allowed resource types: Object
* Allowed permissions: Read, Write, Create

Sample connection string:

`BlobEndpoint=https://piacstatedatawewuwjwuwu.blob.core.windows.net/;QueueEndpoint=https://piacstatedatawewuwjwuwu.queue.core.windows.net/;FileEndpoint=https://piacstatedatawewuwjwuwu.file.core.windows.net/;TableEndpoint=https://piacstatedatawewuwjwuwu.table.core.windows.net/;SharedAccessSignature=sv=2021-21-21&ss=b&srt=o&sp=rwc&se=2025-25-25T01:01:01Z&st=2022-07-07T01:01:01Z&spr=https&sig=fbrddRr99ew6kfcgK855fJQSSdiN5Nsp23SAqDcHe0l%3D`

## Input Variables

This action has the following inputs:

### repo-token

The Action requires access to the calling repo. Pass it your github_token.

Example: `repo-token: ${{ github.token }}`

## Action Triggers

This action is designed to trigger on either a pull request or an issue comment.

When triggered by a pull request, a Terraform Plan is created.

When triggered by an issue comment, the action depend on what is found in the comment:

| Comment | Action                  |
| ------- | ----------------------- |
| /deploy | Deploy Request          |
| /scan   | Security Review Request |
| /debug  | Run Debugging BOT       |
