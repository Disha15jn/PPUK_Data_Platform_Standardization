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
