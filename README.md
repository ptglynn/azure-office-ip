This is a modification of the great work already done by groovy-sky (original links below). It has been modified to download/extract the public IP addresses associated with Azure services (https://docs.microsoft.com/en-us/azure/virtual-network/service-tags-overview)

The routine **get_service_endpoints(self)** has been added. It uses the distribution URL provided by Microsoft to identify the JOSN-formatted file containing service endpoint IP addresses, downloads it, and parses it into a JSON array.

The routine **export_locally(self,prepend_value='')** has been modified. It processes the JSON array and dumps the list of IP addresses associated with each service into an eponymously-named file.

The rest of the code functions identically and updates a **publicly-accessible** static webpage hosted in an Azure storage account with a list of .txt files containing the public IP addresses associated with the service.

Additional notes:

- The use of the storage firewall in azure breaks the deployment and function
- The instructions for deploying provided by groovy-sky will also work for this function
- A Terraform version of the base infrastructure can be found here: https://github.com/ptglynn/azure-functions/tree/master/python-function
- The function works for Azure Public, Government, China, and Germany. Simply edit __init__.py and enable the desired region prior to deployment

### From original source README.md

This repository contains a Python Function App, which collects Azure/Office 365 IP addresses. Exact instruction how-to run it is available [here](https://github.com/groovy-sky/azure/tree/master/func-parse-cloud-00#introduction).

![](https://raw.githubusercontent.com/groovy-sky/azure/master/images/func-az-ip/az_time_func.png)
