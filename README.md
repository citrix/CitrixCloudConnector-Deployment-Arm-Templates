# Citrix Cloud Connector ARM Template

This template creates two Instance of [Citrix Cloud Connector](https://docs.citrix.com/en-us/citrix-cloud/citrix-cloud-connector.html) Virtual Machines, (A component with a collection of Windows services installed on Windows 2016 Server) within specfied Azure Resource Location.

The [Citrix cloud Connector](https://docs.citrix.com/en-us/citrix-cloud/citrix-cloud-connector.html) serves as a channel for communication between Citrix Cloud and your Resource Locations enabling cloud management without requiring any complex networking or infrastructure configuration such as VPNs or IPSec tunnels. This removes all the hassle of managing delivery infrastructure. It enables you to manage and focus on the resources that provide the value to your end users.

# Pre-Requisites

* Here are the pre-requisites before you invoke the template:
* Azure VNet	: Existing Azure VNet that will be passed as Parameter, to which the CloudConnector Machine is connected.
* private IP	: An unused IP that the CloudConnector Machine will be assigned to.
* Active Directory (AD): Join the machine to an AD domain that contains the resources and/or users for the assignment to service offerings (Active Directory schema versions 2008 R2 and later are supported).
* Existing AD Domain, DomainUserName and Domain Password used for joining Citrix Cloud Connector to AD Domain.
* Login to https://citrix.cloud.com/  
		*  Navigate to "Identity and Access Management".  		
		*  Click "API Access".		
		*  Enter a name for Secure Client and click Create Client.
		*  Once Secure Client is created, download Secure Client Credentials file.
		*  Note down :
                	id	=>	Passed as parameter for customerId.
               		Secret	=>	Passed as parameter for clientSecret.




# Click the button below to deploy

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fcitrix%2FCitrixCloudConnector-Deployment-Arm-Templates%2Fmaster%2FmainTemplate.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>


# Template parameters:

(Please refer to parameters.json to see sample parameter.)

| Name   | Description    |
|:--- |:---|
| vhdStorageType | Specifies the type of storage account, if being created. | 
| vhdStorageNewOrExisting | Specifies whether the storage account should be created or already exists. | 
| userImageContainerName | Specifies a storage container in the account specified by 'vhdStorageAccount' in which user images of XenApp 7.7 reside. | 
| machineSize | Specifies the size of the virtual machines (6). | 
| adminUsername | Specifies the name of the administrator for machines, Active Directory domain, NetScaler and XenApp. Exclusion list: 'admin','administrator'. Must be no more than 9 alphanumeric characters. | 
| adminPassword	| Specifies the password of the administrator for machines, Active Directory domain, NetScaler and XenApp. | 
| vnetName	|	VirtualNetwork Name in which the CloudConnector will be Installed.	|
| domainName | Specifies the name of the newly created Active Directory domain. | 
| domainUsername | Specifies the name Existing domain Username that will be used to Join Domain. | 
| domainPassword | Specifies the Existing domain Password for Domain User that will be used to Join Domain. | 
| domainControllerIp |	Private IP of Domain Controller, This is used to Join and Register CloudConnector to DomainController. |
| cloudConnectorIP-1 | Specify Private IP address that needs to be assigned for CloudConnector VM - 1 |
| cloudConnectorIP-2 | Specify Private IP address that needs to be assigned for CloudConnector VM - 2 |
| Customer | This is the customer ID available in the Citrix Cloud console on the API Access page (within Identity and Access Management). |
| clientID | Found on the API Access page. This is the secure client ID an administrator can create.|
| clientSecret | Found on the API Access page. This is the secure client secret available via download after a secure client is created. |
| ResourceLocationId | Specify a Name for a resourcelocation to be created on Citrix Cloud. |
| artifactsBaseUrl	| Specifies the base location of the child templates and desired state configuration scripts. |
| artifactsBaseUrlSasToken	|	Specifies the shared access signature token which provides access to the base artifacts location. |
| azureGov	| Specifies the shared access signature token which provides access to the base artifacts location. |
| customCloudConnectorScriptUri |	If there is custom Script that needs to run on Connector. |
| customCloudConnectorScriptArgs | If there any Arguments that needs to be passed to script. |