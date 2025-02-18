---
uid: PItoDH
---

# PI to Data Hub

PI to Data Hub enables you to transfer on-premises data from Data Archive and Asset Framework (AF) to AVEVA Data Hub. PI to Data Hub also enables AVEVA PI Data Infrastructure – aggregate tag licensing model. With this licensing option, customers no longer need to worry about accurately estimating the count of PI tags needed at every PI Server installation. Instead, they can purchase PI tags in aggregate and be able to use more than the committed number of aggregate tags across any number of deployed PI Servers. PI to Data Hub Agent is required with every PI Server that is part of the aggregate tag model. The aggregate tag model is offered at three tiers of small (100,000 tags), medium (250,000 tags), and large (500,000 tags). These sizes denote the minimum number of aggregate tags to which a customer commits. At any time, the aggregate PI Server tag count may surpass this minimum number, and the customer will be able to pay for the additional tags on a daily rate. 

## PI to Data Hub architecture

PI to Data Hub enables you to use one PI to Data Hub Agent to connect and transfer your on-premises data to AVEVA Data Hub from one Data Archive and one optional Asset Framework (AF) server. The PI to Data Hub Agent creates and sends a transfer that contains the requested PI point data (metadata and PI events) and assets (AF elements and attributes) to AVEVA Data Hub. The transfer and all communication are encrypted with HTTPS. For customers on AVEVA PI Data Infrastructure - aggregate tag, the PI to Data Hub Agent sends license usage information from the connected Data Archive to AVEVA Data Hub.

### Restrictions of PI to Data Hub architecture

These are some restrictions to the PI to Data Hub architecture:

- The connecting AF server must reference the connected Data Archive. The list of available Data Archive servers is based on what servers are referenced by the AF elements selected in your transfer.

- Only one PI to Data Hub Agent can be installed on a given host computer.

- For a given Data Hub Namespace, only a single PI to Data Hub Agent is allowed to transfer data from a given Data Archive.  Attempting to register a second agent from a different host computer against the same Data Archive will fail. This restriction is intended to prevent excess load on a given Data Archive. One workaround for this restriction is to configure a transfer to a different namespace. Consider, however, that agents on different machines do not coordinate data collection, potentially causing more archives to be pulled into memory than if the same number of PI points were transferred with a single agent. 

- Open Id Connect (OIDC) is currently not supported for PI to Data Hub Agent connections to Data Archive or AF server.  

See also <xref:pi-to-ocs-limitations>.

## PI to Data Hub best practices

- Windows integrated security is recommended for connections to Data Archive. Alternatives, such as local Windows Accounts or PI trusts, can be used but they are not as secure as using Active Directory on a Windows Domain. For remote connections to Data Archive, using a dedicated domain account as the Run As user for the PI to Data Hub Agent service provides the finest granularity. The PI to Data Hub Agent Configuration Utility can configure PI mappings to Data Archive. If you want to use a different security mechanism, such as PI trusts, you can use a different tool to configure the PI trusts, such as PI System Management Tools. When OIDC connections are supported by the PI to Data Hub Agent, OIDC will provide a secure alternative to Windows integrated security.  

- For heavy workloads, install the PI to Data Hub Agent on a host computer that is separate from the Data Archive deployment.

- Keep the PI to Data Hub Agent software version up-to-date. The portal indicates when an agent is out of date and needs to be updated.

- Turn off compression only for PI points that do not update often. Turning compression off on a PI point instructs PI to Data Hub to collect the snapshot value rather than the most recently archived value for that PI point. If compression is left on for tags that update infrequently, there may be long delays before seeing data in AVEVA Data Hub.
