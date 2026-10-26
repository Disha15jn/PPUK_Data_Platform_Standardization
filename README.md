# PPUK_Data_Platform_Standardization

naming convention for DPX
Anand Baptista Correia

Ashish kumar Bhatt
Disha Jain;
Sarang Patil
Hello Ashish,

 

Can you please verify below naming convention and also give ip ranges for each vent and subnets.

 

Internal Subscription:dpx-sub-dat-dev-gwc-int-001

Vnet:

dpx-dat-dev-int-gwc-vnet-001(/22)

Subnet:

dpx-dat-dev-int-gwc-snet-001(/25)  

dpx-dat-dev-int-gwc-snet-002(/25)

dpx-dat-dev-int-gwc-snet-003(/25)

dpx-dat-dev-int-gwc-snet-004(/25)

dpx-dat-dev-int-gwc-snet-005(/27)

dpx-dat-dev-int-gwc-snet-006(/27)

dpx-dat-dev-int-gwc-snet-007(/27)

 

Management Subscription: Sub name??

Vnet : dpx-<>-mgt-gwc-vnet-001(/22?)

Subnet:

dpx-zpa-dat-mgt-gwc-snet-002(/27)

dpx-whs-dat-mgt-gwc-snet-002(/27)

dpx-wco-dat-mgt-gwc-snet-003(/27)

Dpx-pve-inf-mgt-gwc-snet-004(27)

 

Thanks and regards,

Anand Correia

 


Please do not print this email unless it is absolutely necessary.

Ashish kumar Bhatt

Anand Baptista Correia
Disha Jain;
Sarang Patil;PPG T0 HUB Team
Hi Anand,

 

Here is the list of new Dev IPs as you requested.


Note : previously IPs are assigned twice, one Disha requested and then Tom W came and asked bigger range.

Now you are requesting one more different range of Subnets. I have allocated as per new request, but just check with Tom once before executing, if you have not.






Revised - CIDR Allocation for DEV - Databricks Project

 

 

 

No of Host

Vnet1

/22

10.130.252.0/22

1024

subnet1

/25

10.130.252.0/25

128

subnet2

/25

10.130.252.128/25

128

subnet3

/25

10.130.253.0/25

128

subnet4

/25

10.130.253.128/25

128

subnet5

/27

10.130.254.0/27

32

subnet6

/27

10.130.254.32/27

32

subnet7

/27

10.130.254.64/27

32

Spare

/27

10.130.254.96/27

32

Spare

/26

10.130.254.128/25

128

Spare

/25

10.130.255.0/25

128

Spare

/24

10.130.255.128/25

128

 

dpx -sub-dat-mgt-gwc-001 (New subscription) -10.130.192.0/21

dpx-dat-mgt-gwc-vnet-001 /24 (New Vnet) - 10.130.199.0/24
dpx-dat- whs-mgt-gwc-snet-001(/27) (new) - 10.130.199.128/27
dpx-wco-dat-mgt-gwc-snet-001(/27) (new) - 10.130.199.160/27
dpx-pve-inf-mgt-gwc-snet-001(27) (new) - 10.130.199.192/27
 



Range

CIDR

Hosts

Subscription

dpx -sub-dat-mgt-gwc-001

/21

10.130.192.0/21

2048

Vnet

dpx-dat-mgt-gwc-vnet-001

/24

10.130.199.0/24

256

Subnet1

dpx-dat- whs-mgt-gwc-snet-001

/27

10.130.199.128/27

32

Subnet2

dpx-wco-dat-mgt-gwc-snet-001

/27

10.130.199.160/27

32

Subnet3

dpx-pve-inf-mgt-gwc-snet-001

/27

10.130.199.192/27

32

Spare

/27

10.130.199.224/27

32

 

 

 

**********************************************

dpx-sub-inf-mgt-gwc-001 (Already created)

dpx-inf-mgt-gwc-vnet-001 (Already created)
dpx-zpa-inf-mgt-gwc-snet-001(/27) (new)
10.130.8.32/27 (use this new CIDR)          
 

 

 

 

 



Azure Resource

Format

Calandra Aligned Name

Subscription (in Application LZ)

<org>-sub-<asset shortname>-<environment>-<region>-<Workload classification><###>

dpx-sub-dat-prd-gwc-int-001

Resource Group (in Application LZ)

<Asset Shortname>-<App / Service name>-<Subscription shortname>-<Workload classification>-<region>-rg-<###>

dpx-dat-dbx-prd-int-gwc-rg-001

Resource Group (in Platform LZ)

 <Org Shortname>-<App / Service name>-<Subscription type>-<Subscription shortname>-<region>-rg-<###>

dpx-dat-zpa-mgt-gwc-rg-001

Vnet (in Application LZ)

<Asset Shortname>-Subscription shortname>-<Subscription type>-<region>-VNet-<###>

dpx-dat-dev-int-gwc-vnet-001

Vnet (in Platform LZ)

<Org Shortname>-<Subscription shortname>-<region>-VNet-<###>

dpx-inf-mgt-gwc-vnet-001

Subnet (in Application LZ)

<Asset Shortname>-<App/Service name shortname>-<Subscription shortname>-<Subscription type>-<region>-snet-<###>

dpx-dat-pex-dev-int-gwc-snet-001

Subnet (in Platform LZ)

<Org Shortname>-<App/Service name shortname>-<Subscription shortname>-<region>-snet-<###>

dpx-inf-zpa-mgt-gwc-snet-001

Storage Account

<Asset Shortname>-<App/Service name shortname>-<Subscription shortname>-<Subscription type>-<region>-st-<###>

dpxdlprdintgwcst001

Key Vault

<Asset Shortname><App/Service name shortname><Subscription shortname><Subscription type><region><kv><###>

dpxdlprdintgwckv001

Log Analytics Workspace

dpx-<asset>-mgt-<loc>-la-001

dpx-dat-mgt-gwc-la-001

 

 

Regarding Management Subscription, I had call with Sarang and ZPA ideally should seat in DPX Infra Management Subscription, rest subnets needs to be identified.
Once we have clarity on this, I will assign IPs.

 

Regards,

Ashish Bhatt



'
module "linux_vm" {
  for_each = var.linux_vms
  source   = "Azure/avm-res-compute-virtualmachine/azurerm"
  version  = "0.18.0"
 
  enable_telemetry = var.enable_telemetry
 
  # Basic VM configuration
  name                = each.value.vm_name
  location            = var.common_vars.location
  resource_group_name = module.rg[each.value.resource_group_key].name
 
  # VM sizing and configuration
  admin_username                      = each.value.admin_username
  disable_password_authentication     = each.value.disable_password_authentication
  admin_password                      = each.value.generate_admin_password ? random_password.linux_vm_admin[each.key].result : each.value.admin_password
  sku_size                           = each.value.vm_size
  zone                               = each.value.availability_zone
  os_type                            = "Linux"
 
  # SSH keys (provided or generated)
  admin_ssh_keys = concat(
    try(each.value.ssh_public_keys, []),
    each.value.generate_ssh_key ? [
      {
        public_key = tls_private_key.linux_vm_ssh[each.key].public_key_openssh
        username   = each.value.admin_username
      }
    ] : []
  )
 
  # OS configuration
  source_image_reference = each.value.source_image_id != null ? null : each.value.source_image_reference
  source_image_resource_id = each.value.source_image_id
 
  # Marketplace plan (required for CIS images)
  plan = try(each.value.plan, null)
 
  # OS Disk configuration
  os_disk = {
    caching              = each.value.os_disk.caching
    storage_account_type = each.value.os_disk.storage_account_type
    disk_size_gb         = each.value.os_disk.disk_size_gb
    name                 = "${each.value.vm_name}-osdisk"
  }
 
  # Data Disks configuration
  data_disk_managed_disks = {
    for disk_key, disk_config in each.value.data_disks : disk_key => {
      name                 = "${each.value.vm_name}-${disk_key}"
      caching              = disk_config.caching
      create_option        = disk_config.create_option
      disk_size_gb         = disk_config.disk_size_gb
      lun                  = disk_config.lun
      storage_account_type = disk_config.storage_account_type
    }
  }
 
  # Disable encryption at host
  encryption_at_host_enabled = false
 
  # Network interfaces configuration
  network_interfaces = {
    for nic_key, nic_config in each.value.network_interfaces : nic_key => {
      name                           = try(nic_config.name, "${each.value.vm_name}-nic")
      accelerated_networking_enabled = try(nic_config.accelerated_networking_enabled, false)
      ip_forwarding_enabled         = try(nic_config.ip_forwarding_enabled, false)
      ip_configurations = {
        for ip_key, ip_config in nic_config.ip_configurations : ip_key => {
          name                          = try(ip_config.name, "internal")
          private_ip_subnet_resource_id = each.value.subnet_key != null ? local.all_subnet_ids[each.value.subnet_key] : (each.value.existing_vnet_key != null && each.value.existing_subnet_key != null ? data.azurerm_subnet.existing["${each.value.existing_vnet_key}-${each.value.existing_subnet_key}"].id : null)
          private_ip_address_allocation = try(ip_config.private_ip_address_allocation, "Dynamic")
          private_ip_address            = try(ip_config.private_ip_address, null)
          public_ip_configuration = try(ip_config.public_ip_enabled, false) ? {
            name              = "${each.value.vm_name}-pip"
            allocation_method = "Static"
            sku               = "Standard"
          } : null
        }
      }
    }
  }
 
  # Managed Identity configuration
  managed_identities = {
    system_assigned = try(each.value.managed_identities.system_assigned, true)
    user_assigned_resource_ids = try(
      length(each.value.managed_identities.user_assigned_identity_keys) > 0 ?
      toset([for key in each.value.managed_identities.user_assigned_identity_keys :
        # Assume user managed identities are defined elsewhere or provided as resource IDs
        key]) :
      toset([]),
      toset([])
    )
  }
 
  # Extensions for Linux configuration
    extensions = merge(
      # Azure Monitor Agent Extension
      try(each.value.extensions.enable_azure_monitor, true) ? {
        azure_monitor_agent = {
          name                       = "AzureMonitorLinuxAgent"
          publisher                  = "Microsoft.Azure.Monitor"
          type                       = "AzureMonitorLinuxAgent"
          type_handler_version       = "1.25"
          auto_upgrade_minor_version = true
          automatic_upgrade_enabled  = false
          settings                   = jsonencode({})
        }
      } : {},
 
      # AAD SSH Login for Linux Extension
      try(each.value.extensions.enable_aad_login, true) ? {
        aad_login = {
          name                       = "AADSSHLoginForLinux"
          publisher                  = "Microsoft.Azure.ActiveDirectory"
          type                       = "AADSSHLoginForLinux"
          type_handler_version       = "1.0"
          auto_upgrade_minor_version = true
          automatic_upgrade_enabled  = false
          settings                   = jsonencode({})
        }
      } : {},
    )
 
  tags = merge(var.common_vars.tags, try(each.value.tags, {}))
 
  depends_on = [
    random_password.linux_vm_admin
  ]
}




linux_vms = {
 
  zscaler_server_01 = {
    resource_group_key ="zsc_rg"
    vm_name           = "ppgzsprdgwcvm01"
    vm_size           = "Standard_D4s_v3"
    admin_username    = "azadmin"
  
    # Password configuration
    generate_ssh_key                = true
    generate_admin_password         = false
    disable_password_authentication = false 
    key_vault_key                  = "zscaler_secrets_kv"
  
   
    # Networking - using new Linux VM subnet created in AVM
    subnet_key                     = "zscaler_subnet"       
  
    # Network interfaces 
    network_interfaces = {
      primary_nic = {
        name                           = "ppgzsprdgwcvm01-nic-01"
        accelerated_networking_enabled = false
        ip_forwarding_enabled          = false
        ip_configurations = {
          internal = {
            name                          = "ppgzsprdgwcvm01-ipconfig-01"
            private_ip_address_allocation = "Static"
            private_ip_address            = "10.128.98.68"
            public_ip_enabled             = false
          }
        }
      }
    }
  
    # Image configuration
    source_image_reference = {
      publisher = "zscaler"
      offer     = "zscaler-private-access"
      sku       = "zpa-con-azure"
      version   = "latest"
    }
 
    plan = {
      name = "zpa-con-azure"
      publisher = "zscaler"
      product   = "zscaler-private-access"
    }
  
    # Disk configuration
    os_disk = {
      name = "ppgzsprdgwcvm01-Zonal-LRS-Disk"
      caching              = "ReadWrite"
      storage_account_type = "Premium_LRS"
      disk_size_gb         = 100
    }
  
    # Monitoring and logging
    dcr_key                     = null
    log_analytics_workspace_key = "shared_law"
  
    # Identity
    managed_identities = {
      system_assigned = true
    }
 
    patch_mode            = "AutomaticByPlatform"
    patch_assessment_mode = "AutomaticByPlatform"
    reboot_setting        = "Never"
    bypass_platform_safety_checks_on_user_schedule_enabled = true
  
    # Extensions
    extensions = {
      enable_azure_monitor    = true
      enable_aad_login        = true
      enable_custom_script    = false
    }
   
    availability_zone = "1"
  }
}
 
 
just use config naming convention we can discuss
 
please make sure user can login via bastion on this vm
 
infzsprdgwcvm01
 
you can use above name
 
