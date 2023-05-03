# Exercise 1- Secure administration and management

## Task 1: Network Health - New 

Azure Monitor Network Insights provides a comprehensive and visual representation through topologies, of health and metrics for all deployed network resources, without requiring any configuration. It also provides access to network monitoring capabilities like Connection Monitor, flow logging for network security groups (NSGs), and Traffic Analytics.

1. Navigate to Azure portal. Using the search bar, search for **Monitor (1)** and **select (2)** it from the suggestions.

   ![](images/a3.png)

1. From the sidebar, select **Networks** from Insights.

   ![](images/a4.png "search gateway")
   
1. On the **Network health** tab, you can customize the resource health and alerts view by using filters like **Subscription**, **Resource Group**, and **Type** and you can use the search box to search for resources and their associated resources. For example, a public IP is associated with an application gateway. A search for the public IP's DNS name will return both the public IP and the associated application gateway.

   ![](images/a5.png "search gateway")

1. In this, each tile represents a resource type. The tile displays the number of instances of that resource type deployed across all selected subscriptions. It also displays the health status of the resource.

   ![](images/a12.png "search gateway")

1. You can click on any resource to select the resource view, The resource view helps you visualize how a resource is configured. The resource view is currently available for **Azure Application Gateway**, **Azure Virtual Network**, and **Route table**. For example, for Application Gateway, you can access the resource view by selecting the Application Gateway resource name in the metrics grid view. You can do the same thing for Azure Virtual Network, and route table.

   ![](images/a6.png "search gateway")

1. Once you opened the resources, the **Metrics** look like this in the grid view.

   ![](images/a13.png "search gateway")

## Task 2: Network Topology - New 

The topology capability of Azure Network Watcher enables you to view all of the resources in a virtual network, the resources associated to resources in a virtual network, and the relationships between the resources. In this task, you'll view resources in a Microsoft Azure virtual network, and the relationships between the resources.

1. Navigate to Azure portal. Using the search bar, search for **Network Watcher (1)** and **select (2)** it from the suggestions.

   ![](images/cafinfa1.jpg)

1. From the sidebar, select **Topology** from monitoring.

   ![](images/cafinfa2.jpg "search gateway")

1. Select the **default subscription (1)**, **JumpVM-RG (2)** for Resource group, and **vnet (3)** for virtual network in the Toplogy tab.  

   ![](images/cafinfa3.jpg "search gateway")

1. Now, you'll be able to **visualize (1)** the Virtual network topology and understand how different network resources such as virtual machines, subnets, virtual network gateways, and other network components are interconnected and how they communicate with each other. You can also the download the toplogy by clicking on **Download topology (2)**.

   ![](images/cafinfa4.jpg "search gateway")

## Task 3: Secure Access via Bastion Host - New

In this task, we are demonstrating how you are able to connect to VMs in an environment without configuring a public IP on the VMs.

1. Navigate to Azure portal. Using the search bar, search for **Virtual networks (1)** and **select (2)** it from the suggestions.

   ![](images/a14.png "search gateway")

1. Select the **vnet** from the list.

   ![](images/a15.png "search gateway")

1. From the sidebar, select **Subnets** from Settings.
   
   ![](images/a16.png "search gateway")

1. You will see that **AzureBastionSubnet** is already present in the subnets, If you want to see the subnet configuration then you can click on the AzureBastionSubnet subnet and explore on this.

   ![](images/a17.png "search gateway")

1. Now Using the search bar, search for **Virtual machines (1)** and **select (2)** it from the suggestions.

   ![](images/a18.png "search gateway")

1. Select the **JumpVM-<inject key="DeploymentID" enableCopy="false" />** from the list.

   ![](images/a19.png "search gateway")

1. On the Virtual Machine page, go to the **Overview (1)** tab and click on **Connect (2)** then select **Bastion (3)**.
 
    ![](images1/connect.png)
 
1. On the Bastion page, follow the below-mentioned instructions to connect to the Virtual Machine using Bastion:
 
    - **Username**: Enter **demouser (1)**
    - **Authentication Type**: Select **Password (2)** from the drop-down
    - **Password**: Enter **<inject key="JumpVM Admin Password" enableCopy="true"/> (3)**
    - Click on **Connect (4)**
 
    ![](images1/bastionconnect.png)
 
1. Now, you will be redirected to a new tab where the Bastion VM is opened. If you see the pop-up **See text and images copied to the clipboard**, click on **Allow**.
 
    ![](images1/allowpopup.png)



## Task 4: Prepare the Network Watcher monitoring environment and NSG Flow – New

Network Watcher provides several features to monitor and diagnose network performance issues. We will create NSG flow logs that will provide detailed information about the network traffic that passes through your NSG.They capture information such as source and destination IP addresses, source and destination ports, protocol, and action taken (allow or deny) by the NSG. This information can be used for troubleshooting network connectivity issues, monitoring and analyzing network traffic patterns, and detecting potential security threats.

1. Navigate to Azure portal. Using the search bar, search for **Resource group (1)** and **select (2)** it from the suggestions.

   ![](images/cafinfra5.jpg)

1. Select the **JumpVM-rg** from the list.

   ![](images/cafinfra6.jpg)

1. From the list of resources, select the Network Security Group named **JumpVM-<inject key="DeploymentID" enableCopy="false" />-nsg**.

   ![](images/cafinfra7.jpg)

1. In the sidebar, select **NSG flow logs** from the Monitoring menu.

   ![](images/cafinfra8.jpg)

1. Click on the **create** button.

   ![](images/cafinfra9.jpg)

1. In the Create a flow log page, select the **default subscription (1)** in the drop down and click on **Select resource (2)**.

   ![](images/cafinfra10.jpg)

1. In the Select network security group page, select **JumpVM-<inject key="DeploymentID" enableCopy="false" />-nsg** **(1)** and click on **Confirm selection (2)**.

   ![](images/cafinfra11.jpg)

1. For the Instance details, Provide the following details and click on **Next: Configuration> (4)**

   - **Subscription**: select **default subscription (1)** from the drop down.
   - **Storage account**: select **nsglogs<inject key="DeploymentID" enableCopy="false" />** from the drop down.
   - **Retention (days)**: **30 (3)**

   ![](images/cafinfra12.jpg)  

1. In the Configuration page, leave everything as default and click on **Review + create (2)**.

   ![](images/cafinfra13.jpg)  

1. In the Create page, click on the **Create** button and wait till the deployment completion.

   ![](images/cafinfra14.jpg)  

1. Navigate to Azure portal. Using the search bar, search for **Resource group (1)** and **select (2)** it from the suggestions.

   ![](images/cafinfra5.jpg)

1. Select the **JumpVM-rg** from the list.

   ![](images/cafinfra6.jpg)

1. From the list of resources, select the Network Security Group named **JumpVM-<inject key="DeploymentID" enableCopy="false" />-nsg**.

   ![](images/cafinfra7.jpg)

1. From the sidebar, select **Diagnostic settings (1)** and click on **+ Add diagnostic setting (2)**.

   ![](images/cafinfra15.jpg)

1. In the Diagnostic settings page, provide the following details and click on **save (6)**.

   - **Diagnostic setting name**: **NSG_Flow_Logs (1)**
   - **Logs> Category groups**: check the **allLogs (2)** checkbox.
   - **Destination details**: select the **Archeive to a storage account (3)** checkbox. Make sure the **default subscription (4)** is selected for subscription and **nsglogs<inject key="DeploymentID" enableCopy="false" /> (5)** for storage account.

   ![](images/cafinfra16.jpg)







 