---
uid: PowerBIReleaseNotes
---

# Release notes

AVEVA Data Hub Power BI Connector 2.0.0.54

## Overview

The AVEVA Data Hub Power BI Connector allows AVEVA Data Hub Data Views to be imported into Power BI so the data can be visually analyzed or utilized in Power BI reports or dashboards.

The Power BI Connector can be installed on Windows Operating System installations of Power BI Desktop. The connector can also be used with the Power BI Service through installation of an On-premises Data Gateway. Data sets using AVEVA Data Hub Data Views can be configured for scheduled refresh in the Power BI Service to create and share dynamically updating Power BI dashboards with data from AVEVA Data Hub.

## Known issues

| Work item | Description |
|-----------|-------------|
| 248772    | When the same installer runs twice, the dialog appears offering the user the chance to uninstall the connector. If the user clicks on Uninstall option and then clicks on the **Back** button, the user is brought to a screen from which she did not start. The uninstall will work, however, if the user moves forward through the screens. |

## Known limitations

When loading a Data View which has multiple pages, the loading screen prints the JSON body of the call that is used to retrieve the pages of data.

When selecting a Data View from the navigation table which does not have default start and end index values defined, the name of the previous Data View persists on the page title even though the user navigated away from it.

## Setup

### Operating systems

Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2016, Windows Server 2019

### Other system requirements

Supported Microsoft Power BI versions:

- Microsoft Power BI Desktop 2.91.884.0 or later

- Microsoft Power BI On-premises Data Gateway 3000.89.6 or later

### Distribution kit files

The installer is released as a self-extracting executable file that contains:

- ADHDataviews.pqx

- ADHDataviews_LICENSE

### Installation and upgrade

#### Desktop installation

##### Before you install

- Power BI Desktop is installed

- User has Administrator rights on the local machine

##### Installation

The AVEVA Data Hub Power BI Connector installer will extract and install the connector for Power BI.

See the accompanying [AVEVA Data Hub Power BI Connector User Guide](xref:PowerBI) for detailed Desktop installation instructions.

#### On-premises Data Gateway installation

##### Before you install

- Microsoft Power BI On-premises Data Gateway is installed

- User has Administrator rights on the local machine

##### Installation

See the accompanying [AVEVA Data Hub Power BI Connector User Guide](xref:PowerBI) for detailed Desktop installation instructions.

### Uninstalling Power BI Connector

Remove the product using **Uninstall a program** in the Windows Control Panel for both Desktop and on-prem data gateway installations.

## Security information and guidance

### AVEVA's commitment

Because the PI System often serves as a barrier protecting control system networks and mission-critical infrastructure assets, AVEVA is committed to (1) delivering a high-quality product and (2) communicating clearly what security issues have been addressed. This release of AVEVA Data Hub Power BI Connector is the highest quality and most secure version of the  Power BI Connector released to date. AVEVA's commitment to improving the PI System is ongoing, and each future version should raise the quality and security bar even further.

### Vulnerability communication

The practice of publicly disclosing internally discovered vulnerabilities is consistent with the [Common Industrial Control System Vulnerability Disclosure Framework](https://ics-cert.us-cert.gov/sites/default/files/ICSJWG-Archive/ICSJWG_Vulnerability_Disclosure_Framework_Final_1.pdf) developed by the [Industrial Control Systems Joint Working Group (ICSJWG)](https://ics-cert.us-cert.gov/Industrial-Control-Systems-Joint-Working-Group-ICSJWG). Despite the increased risk posed by greater transparency, AVEVA is sharing this information to help you make an informed decision about when to upgrade to ensure your PI System has the best available protection.

For more information, refer to [Ethical Disclosure Policy (https://www.osisoft.com/terms-and-conditions/ethical-disclosure)](https://www.osisoft.com/terms-and-conditions/ethical-disclosure).

To report a security vulnerability, refer to [Report a Security Vulnerability (https://www.osisoft.com/terms-and-conditions/report-security)](https://www.osisoft.com/terms-and-conditions/report-security).

### Vulnerability scoring

AVEVA has selected the [Common Vulnerability Scoring System (CVSS)](https://www.first.org/cvss/v2/guide) to quantify the severity of security vulnerabilities for disclosure. To calculate the CVSS scores, AVEVA uses the [National Vulnerability Database (NVD)](https://nvd.nist.gov/vuln-metrics/cvss/v2-calculator?calculator&amp;.0) calculator maintained by the National Institute of Standards and Technology (NIST).  AVEVA uses Critical, High, Medium, and Low categories to aggregate the CVSS Base scores. This removes some of the opinion related errors of CVSS scoring. As noted in the [CVSS specification](https://www.first.org/cvss/specification-document), Base score range from 0 for the lowest severity to 10 for the highest severity.

### Overview of new vulnerabilities fixed or mitigated

This section is intended to provide relevant security-related information to guide your installation or upgrade decision. AVEVA is proactively disclosing aggregate information about the number and severity of AVEVA Data Hub Power BI Connector security vulnerabilities that are fixed in this release.

No security-related information is applicable to this release.

## Documentation overview

[AVEVA Data Hub Power BI Connector User Guide](xref:PowerBI): An introduction to AVEVA Data Hub Power BI Connector for the end user. This user guide provides the installation procedure and a usage tutorial on the product features.
