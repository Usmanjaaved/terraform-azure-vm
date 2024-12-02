# Terraform Azure Virtual Machine Module

This Terraform module simplifies the process of provisioning an Azure Virtual Machine with custom configurations. It allows users to specify various parameters such as VM size, disk type, and image details to meet their specific requirements.

## Features
- Easy deployment of Azure Virtual Machines.
- Configurable VM size and storage options.
- Integration with existing network interfaces.
- Support for Ubuntu operating system images.

## Usage

```hcl
module "azure_vm" {
  source                  = "git@github.com:Usmanjaaved/terraform-azure-vm.git"

  vm_name                 = "example-vm"
  location                = "East US"
  resource_group_name     = "example-rg"
  network_interface_ids   = ["<network_interface_id>"]
  vm_size                 = "Standard_B2ms"
  disk_type               = "Standard_LRS"
  admin_username          = "adminuser"
  admin_password          = "Password123!"
  ubuntu_publisher        = "Canonical"
  ubuntu_offer            = "UbuntuServer"
  ubuntu_sku              = "18.04-LTS"
  ubuntu_version          = "latest"
}
```

## Input Variables

| Name                   | Description                                        | Type     | Default           | Required |
|------------------------|----------------------------------------------------|----------|-------------------|----------|
| `vm_name`              | The name of the Virtual Machine.                  | `string` | n/a               | Yes      |
| `location`             | The Azure region where the VM will be deployed.   | `string` | n/a               | Yes      |
| `resource_group_name`  | The name of the resource group to use.            | `string` | n/a               | Yes      |
| `network_interface_ids`| List of network interface IDs to associate.       | `list`   | n/a               | Yes      |
| `vm_size`              | The size of the Virtual Machine.                  | `string` | `Standard_B2ms`   | No       |
| `disk_type`            | The storage type for the VM's OS disk.            | `string` | `Standard_LRS`    | No       |
| `admin_username`       | The administrator username for the VM.            | `string` | n/a               | Yes      |
| `admin_password`       | The administrator password for the VM.            | `string` | n/a               | Yes      |
| `ubuntu_publisher`     | The publisher of the Ubuntu image.                | `string` | `Canonical`       | No       |
| `ubuntu_offer`         | The offer of the Ubuntu image.                    | `string` | `UbuntuServer`    | No       |
| `ubuntu_sku`           | The SKU of the Ubuntu image.                      | `string` | `18.04-LTS`       | No       |
| `ubuntu_version`       | The version of the Ubuntu image.                  | `string` | `latest`          | No       |

## Outputs

| Name           | Description                            |
|----------------|----------------------------------------|
| `vm_id`        | The ID of the created Virtual Machine. |
| `public_ip`    | The public IP address of the VM.       |
| `private_ip`   | The private IP address of the VM.      |

## Prerequisites
- An existing Azure resource group.
- Network interfaces already created and available in Azure.

## Example Scenario
For deploying a Virtual Machine named `example-vm` in the `East US` region within a resource group named `example-rg`:

1. Ensure you have created the required network interfaces in Azure.
2. Use the example `Usage` code provided above, replacing `<network_interface_id>` with your network interface ID.
3. Apply the Terraform configuration to deploy the VM.

## Support
For issues or feature requests, please open an issue on the [GitHub repository](https://github.com/Usmanjaaved/terraform-azure-vm/issues).

