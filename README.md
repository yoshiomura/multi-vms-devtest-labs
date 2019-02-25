# Deploy Multiple VMs on DevTest from Azure DevOps Pipelines
Template for DevTest Labs using DevOps artifacts for deploying apps to Multiple VMs in Labs.

## Prerequisites

### Setup Personal Access tokens (PAT)

The Artifact needs PAT and the token needs Build (Read) permission at least.

https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops

### Get Free DevTest Labs Task from Visual Studio Market Place

The template DevTest Labs exports needs the task for deployment from DevOps.

https://marketplace.visualstudio.com/items?itemName=ms-azuredevtestlabs.tasks

### Set Variables in Pipelines

In this ARM Template, these variables are used.

- newVMName
- userName
- password
- buildDefinitionName (your Build Pipeline Name)
- labName
- pathToScript (Script Path you execute on VM)
- personalAccessToken
- size (VM size)
- VMcounts
- vstsProjectUri (https://dev.azure.com/yourorg/yourproject)

## Set "Azure DevTest Labs Create VM" in your Pipeline.

Choose this template and set Template Parameters like below. It should be changed along with parameters in your template.

```
-newVMName '$(newVMName)' -userName '$(userName)' -password (ConvertTo-SecureString -String '$(password)' -AsPlainText -Force) -buildDefinitionName '$(buildDefinitionName)' -labName '$(labName)' -pathToScript '$(pathToScript)' -personalAccessToken (ConvertTo-SecureString -String '$(personalAccessToken)' -AsPlainText -Force) -size '$(size)' -VMcounts '$(VMcounts)' -vstsProjectUri '$(vstsProjectUri)'
```

