# Azure Deployment What-If Action

GitHub Action that previews the effects of your Azure infrastructure changes before its deployment by running an [ARM template deployment what-if operation](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-what-if?tabs=azure-powershell).

## When to use

The action is particularly useful on Infrastructure as Code Continuous Integration (CI) workflows, where you can provide detailed information of how Azure resources will change if you deploy the ARM template. The action doesn't make any changes to existing resources.

## Getting Started

### Prerequisites

If your GitHub Actions workflows are running on a [self-hosted runner](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners):

- [Azure CLI](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/install#azure-cli) 2.20.0 or later installed

### Example Usage

#### **Preview changes with a parameters file**

```yml
steps:
  - name: Preview changes
    uses: Azure/deployment-what-if@v1.0.0
    with:
      subscription: '<subscription ID>'
      resourceGroup: '<resource group name>'
      templateFile: azuredeploy.json # main.bicep
      parametersFile: parameters.json
```

#### **Preview changes with additional parameters**

```yml
steps:
  - name: Preview changes
    uses: Azure/deployment-what-if@v1.0.0
    with:
      subscription: '<subscription ID>'
      resourceGroup: '<resource group name>'
      templateFile: azuredeploy.json # main.bicep
      additionalParameters: key1=value key2=value keyN=value
```

> Note: `parametersFile` and `additionalParameters` can be used together.

### Inputs

| Name | Description | Required |
| --- | --- | --- |
| `subscription` | Subscription ID | true |
| `resourceGroup` | Resource group name | true |
| `templateFile` | ARM template (`.json`) or Bicep (`.bicep`) file | true |
| `parametersFile` | Parameters file for the ARM template or Bicep | false |
| `additionalParameters` | Additional parameters to be applied on the ARM template or Bicep. Multiple parameters should be separated by spaces. | false |

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

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
