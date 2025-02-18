---
uid: pi-to-ocs-utility
---

# Run the PI to Data Hub Agent Configuration Utility

Use the PI to Data Hub Agent Configuration Utility to set up and configure AF server and Data Archive data sources before creating a data transfer. After installing or upgrading a PI to Data Hub Agent, use the utility to select a source AF server or Data Archive, view connection details, create AF and PI mappings, set data privacy settings, and register the agent. 

**Note:** A connection to AVEVA Data Hub with the post-installation utility cannot be established if the system time is not correct. Additionally, you will not be able to connect to AVEVA Data Hub if Internet Explorer Enhanced Security Configuration is enabled. For more information, see <xref:disable-ie-security>. 

The following table provides descriptions of the fields shown in the configuration utility. The image shows the AF server selected, but the fields are similar when a Data Archive server is selected.

![AF server details](../../images/af-details-refreshed.png)

| Field | Description                                                     |
| ----- | --------------------------------------------------------------- |
| Agent HostName  | Name of the host computer where the agent is installed. |
| Agent Description  | An optional name for the agent. |
| Agent Status  | Displays the agent's status. |
| Agent State  | Displays the agent's registration state. |
| Agent Version  | The installed PI to Data Hub Agent version. |
| Agent Service Account  | Type of agent service account. |
| PI to Data Hub Agent Settings ![Customize icon](../../images/agent-settings-icon.png) | Set data privacy options and assign an agent description. |
| Refresh Display ![Refresh icon](../../images/agent-refresh-icon.png) | Refresh the displayed agent and server information. |
| AF Server Name/Data Archive Server Name  | Source AF or Data Archive server name. |
| Alternate Display Name | An optional, alternate name for an AF or Data Archive server. | 
| AF Mapping/PI Mapping | The type of AF/PI mapping configured on the service account. |
| Connection Timeout | The time before the agent connection times out. |

## Open the PI to Data Hub Agent Configuration Utility

The PI to Data Hub Agent Configuration Utility opens after you install or upgrade a PI to Data Hub Agent. You can open the PI to Data Hub Agent Configuration Utility at any time to change server connections and other settings after initial setup. 

To open the PI to Data Hub Agent Configuration Utility:

1. Select **Start** > **AVEVA** > **PI to Data Hub Agent Configuration Utility**, and then select **Yes** to confirm.

1. Select **Connect to AVEVA Data Hub**.

   This opens a web browser for login. After successful authentication, return to the configuration utility. The namespace configuration view opens.

   ![namespace configuration](../../images/namespace-config.png)

1. Select a namespace from the **Data Hub Namespace** dropdown list.

1. (Optional) In the **Agent Description** field, enter a descriptive name for the agent.

1. (Optional) To display the hostname in the portal, select the **Opt-in to publishing PI to Data Hub Agent Hostname** option.

1. Select **Continue**.

## Add an AF server

Optionally, add an AF server to the utility to be able to use it in data transfers. The utility validates an AF server connection to ensure the version of PI Asset Framework (AF) installed on the AF server supports the features required for transfers.

To add an AF server:

1. Open the PI to Data Hub Agent Configuration Utility.

1. In the `PI to Data Hub Agent Configuration Utility` window, select the **AF** button.<!--Angela Flores 11/12/21 - I normally would not use button, but I can't tell from the screenshots what you actual need to select.-->

   **Note**: If a Data Archive server was added first, select **Add Asset Framework Server** on the left side of the window instead.

1. In the **AF Server Name** field, enter the name of the AF server, and then select **Add Server**.

   The utility displays the server details.

   **Note:** Once an AF server has been added, the utility scans the configured AF server for referenced Data Archives. As the utility finds Data Archives, they are shown in the **Detected Data Archives** list. You can select and add the desired Data Archive. You do not have to wait for the scan to complete. You can also select **Add Data Archive Server** on the left and manually enter the name of the Data Archive if you do not want to wait for the scan.

1. Select one of the Data Archives listed under `Detected Data Archives`, and then select **Add Selected Data Archive**.

   **Note:** You can select **Add Data Archive Server** on the left at any time to add a Data Archive before the scan completes.

1. Review the AF source server details to ensure they are correct:

   - AF server name, version, and ID
   - IP address
   - Connection status and timeout

1. (Optional) To add an alternate display name, select the pencil icon, type an alternate name, select **Set Display Name** and then select **Close**. AVEVA Data Hub stores the alternate display name instead of the actual AF server name. See [Usage of server names and alternate display names within AVEVA Data Hub](#usage-of-server-names-and-alternate-display-names-within-aveva-data-hub).

1. (Optional) To change the length of time the agent checks for a server connection before timing out, select the pencil icon next to **Connection Timeout**.

1. (Optional) To check that the connection to the AF server is working, select **Test Connection**.

1. (Optional) To delete a server connection, select **Remove Server**, then select **Remove AF Server** to confirm. 

1. To keep the current AF server configuration settings and restart the agent, select **Save**.

   **Note:** After you save the AF server configuration settings, you need to select a default Data Archive in PI System Explorer to resolve substitution references for AF element attributes.

## Usage of server names and alternate display names within AVEVA Data Hub

The AF server name, or its alternate display name, displays on the PI to Data Hub Agents page within AVEVA Data Hub and is referenced in the path of an asset's metadata, which is visible in Asset Explorer (`__Path`).

The Data Archive name, or its alternate display name, appears in the `PI to Data Hub Agents` page within AVEVA Data Hub, and is used in the StreamIds created by a transfer. StreamIds have the format `PI_[DataArchiveServerName]_[PIPointIDNumber]`.

**Note:** Setting an alternate display name for a Data Archive must be done *before* the initial start of a transfer. StreamIds are immutable. Once a stream is built, to change it you must delete all the original streams, configure the alternate display name, and restart the transfer.

The maximum character length for an AF server alternate display name is 63 and the maximum character length for the Data Archive alternate display name is 86. The difference is due to added information. Both fields start with a maximum of 100 characters because Asset Id and Stream Id have a 100-character limit. To form an Asset Id, the agent adds an underscore and a 36-character GUID to an AF server alternate display name, allowing 63 characters (100-37) for the alternate display name. To form a Stream Id, the agent prepends the Data Archive alternate display name with `PI_` and appends `_[PIPointIDNumber]` (maximum of 10 characters), allowing 86 characters (100-14) for the alternate display name.

## Select the default Data Archive in PI System Explorer

You need to specify the default Data Archive, also referred to as the default data server, for the PI System and PI AF database after setting an AF server. By default, PI AF databases inherit the PI AF Server's local default data server. See [Find the default Data Archive server](https://docs.aveva.com/bundle/pi-server-af-pse/page/1018897.html) for more information.

To select the default Data Archive:

1. Open PI System Explorer on the client machine.

1. Select **File** > **Server Properties**.

1. In the `PI AF Server Properties` window, select the data server from the **Default Data Server** dropdown list.

1. Select **Apply**, then select **OK** to save the selection.
 
1. Close PI System Explorer.  
 
## Create an AF mapping

You can assign an AF mapping to an AF identity. AF mappings enable a specific service account assigned to an AF identity in PI System Explorer to read and transfer AF element and AF attribute data. You can also edit mappings with the utility.

**Note:** The user account used to launch the utility must have permission to create mappings.

To create an AF mapping:

1. Open the PI to Data Agent Configuration Utility.

1. Select the pencil icon next to **AF Mapping**.
   
1. In the `Configure AF Mapping` window, select an identity and select **Create**.

  The AF mapping is created for the selected identity.
                                             
  **Note:** If an AF mapping has been created with another tool, a warning is displayed.
  
1. Select **Close** to return to the utility.

## Add a Data Archive

If you plan on transferring AF server data, we recommend you add an AF server first, because the PI to Data Hub Agent Configuration Utility will detect automatically the Data Archive servers that are referenced by AF server. This allows you to select the source Data Archive that contains the PI points you want to transfer. However, you can also add a Data Archive without adding an AF server.

**Note:** There is a one-to-one (1:1) Data Archive to PI to Data Hub Agent constraint for PI to Data Hub transfers. If your AF server references multiple Data Archives, only one Data Archive can be selected and configured for the transfer.  

The list of available Data Archive servers is based on the servers referenced by AF elements on the AF server you selected. If you are upgrading an agent, the PI to Data Hub Agent Configuration Utility maintains the previously selected Data Archive configuration.  

**Note:** If you are not adding an AF server, select the Data Archive icon on the first page of the PI to Data Hub Agent Configuration Utility.

To add a Data Archive:

1. Open the PI to Data Hub Agent Configuration Utility.

1. In the `PI to Data Hub Agent Configuration Utility` window, select the **Data Archive Server** button.

   **Note**: If an AF server was added first, select **Add Data Archive Server** on the left side of the window instead.
   
1. In the **Data Archive Server Name** field, enter the name of the Data Archive server, and then select **Add Server**.
   
   The Data Archive connection is added and details about the newly added Data Archive are displayed.

1. Review the following details for the Data Archive:
 
   - Server name, version, and server ID
   - IP address
   - Connection status and timeout
   
1. (Optional) To add an alternate name, select the **Alternate Display Name** pencil icon, type an alternate name, select **Set Display Name** and then select **Close**.

   **Note:** Setting an alternate display name for a Data Archive must be done *before* the initial start of a transfer. See [Usage of server names and alternate display names within AVEVA Data Hub](#usage-of-server-names-and-alternate-display-names-within-aveva-data-hub).

1. (Optional) To change the length of time the agent checks for a server connection before timing out, select the pencil icon next to **Connection Timeout (sec)**.

1. (Optional) To confirm that the connection to the Data Archive is working, select **Test Connection**.

1. (Optional) To remove the configured Data Archive, select **Remove Server**.

1. To retain the current Data Archive configuration, select **Save**.

## Create a PI mapping 

PI mappings enable access to data stored on a Data Archive by service accounts assigned to a PI identity. PI mappings can be created for a PI identity, user, or group. Accounts assigned to a PI identity can read and transfer PI point data to AVEVA Data Hub. For more information, see ["What are PI identities and mappings?"](https://docs.aveva.com/bundle/pi-server-install/page/1022322.html). You can also edit mappings with the utility.

**Note:** The user account used to launch the utility must have permissions to create mappings.

To create a PI mapping:

1. Open the PI to Data Hub Agent Configuration Utility.

1. Select the Data Archive server on the left side of the window.

1. Select the pencil icon next to **PI Mapping**.
 
   The `Configure Mapping` window opens.<!--AF 11/12/21 Why does PI Mapping have a screenshot, but AF mapping doesn't? Do we really need it?-->

   ![Configure Mapping dialog box](../../images/configure-mapping-window.png)

1. Select an identity for the PI mapping, then select **Create**.

   The PI mapping is created for the selected PI identity, PI group, or PI user.

   **Note:** If a PI mapping has already been created with another tool, a warning is displayed. 

1. Select **Close** to return to the utility, and then select **Save** in the utility.

## Set data privacy and edit an agent description

Use the PI to Data Hub Agent Settings to edit the descriptive name for the agent and to change the data privacy setting. This description appears where the agent is referenced and allows you to search by agent description. The data privacy setting controls whether the host name of a Data Archive is published and displayed in AVEVA Data Hub. By default, host names are not published. If you opt to have a host name published, it appears in the portal on the `PI to Data Hub Agents` page as shown below: 

![Agent description and hostname displayed in PI to Data Hub Agents page](../../images/pi-to-ocs-agents-hostname.png)

1. Open the PI to Data Hub Agent Configuration Utility.

1. To open the `PI to Data Hub Agent Settings` window, select the pencil icon to the right of **Agent Service Account**.

1. To publish the hostname, select the **Opt-in to publishing...** option under `Data Privacy`.

1. (Optional) In the **PI to Data Hub Agent Description** field, enter a descriptive name for the agent.

1. To save your selections, select **Ok**, and then select **Save** in the utility.

## List of agent states

After saving in the PI to Data Hub Agent Configuration Utility, it may take a few minutes for the PI to Data Hub Agent to register with AVEVA Data Hub. The table below lists the various states that may appear under **Agent State** in the PI to Data Hub Agent Configuration Utility.

| **State**                     | **Description**                                              |
| ----------------------------- | ------------------------------------------------------------ |
| Data Source Connection Issue  | Indicates the PI To Data Hub Agent cannot connect to the Data Archive. Some reasons for this status include the Data Archive is turned off, a firewall issue is preventing connections, or an incorrect name is configured for the Data Archive. For example, the agent is trying to connect to a machine that does not exist or was renamed. There may be additional reasons for this status. |
| Data Source Security Issue    | Indicates the Data Archive connection security settings need to be addressed. |
| Missing Configuration         | The Data Archive server has not been configured in the PI to Data Hub Agent. |
| Registration Failed           | Contact [AVEVA Customer Support](https://softwaresupport.aveva.com) for assistance. |
| Registering                   | The PI to Data Hub Cloud portion is creating the necessary resources for the PI to Data Hub Agent. |
| Shutdown                      | The last communication that the PI to Data Hub Cloud had with the agent was a shutdown message. |
