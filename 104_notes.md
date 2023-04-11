# Az 104 Certification

## A Cloud Guru

### Cloud Shell

- Click on the shell icon in the tool bar.
- Select the languague (Bash/PWS)
- Click on Show advaced settings (select the type of the storage, region, resource group, etc.)
- Click on create.

### Az-CLI Commands

- az group \<help\>
- az vm \<help\>

```powershell
az vm create `
--resource-group <resourceGroupName> `
--location <location> `
--name <vmName> `
--image <osVersion> `
--admin-username <userName> `
--generate-ssh-keys `
--no-wait
```

### PowerShell Commands

- Get-AzResourceGroup *--> get information about resource groups (Output in JSON format)*
- Get-AzResource | Format-Table *--> Get all Azure resources in table format*
- Get-CloudDrive *--> Get information about the storage account and file share from Cloud Shell*

### Azure Resource Manager

ARM is the orchestraton layer for managing all the resources inside of the Azure Cloud. It can be used through the *CLI*, *Portal* and *Powershell*. ARM is the IaC tool in Azure, the file format template is JSON and has the following structure:

- **Parameters & Variables**: Used to pass information to the template.
- **Resources**: Used to define resources in the template.
- **Outputs **: Used to return outputs from the execution of the template.

#### Create a template json file

Search: Deploy Custom Template > Build your own templatein the editor > create or paste the json file content. Also provide a lever for scoping governance and security.

*Example:* <https://acloudguru-content-attachment-production.s3-accelerate.amazonaws.com/1642643575999-linuxVM.json>

### Suscriptions

The billing unit that we use to understand our cloud costs. A suscripttion contain resource groups and their associated resources.

#### Type of suscriptions

- Azure Plan (Enterprise agreement support & Pay-As-You-Go)
- Free Trial ()

#### Naming Conventions

They are named based on whether they are (Prod/Staging/Dev), following the Department or Team name that intends to use the subscription, and, then put the region of the business that wants to use the subscription.

### Management Group

---

## Udemy - KodaKloud

## Documentation

- [Azure IAM Course (ACG)](https://acloud.guru/overview/17e4d37f-5a2a-4840-81a7-c2884425c576?_ga=2.190879715.813804500.1625120551-737218096.1597620394)
- [Azure Storage Deep Dive (ACG)](https://learn.acloud.guru/course/17ee4dc4-6f8e-4411-b0e9-26bdd4b8936c/overview)
