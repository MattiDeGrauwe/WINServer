# Documentation

## All

- Elke server is geïnstalleerd in het Engels met een azerty invoer.
- Windows server 2016
- Install Windows Updates
- Install virtualbox guest additions

## dc01

- Installatie AD DS / DNS / DHCP
- DHCP scope 192.168.1.51 - 192.168.1.99 voor hosts
- Maak nieuwe gebruiker `Matti` aan in active Directory

## dc02

- toegevoegd aan domein matdeg.gent
- Installatie AD DS / DNS / DHCP
- DHCP scope 192.168.1.51 - 192.168.1.99 voor hosts

## mail

- [Cumulative Update 6 for Exchange Server 2016 (KB3177106)](https://www.microsoft.com/en-us/download/details.aspx?id=55520)

### Prerequisites exchange server 2016

- Install-WindowsFeature RSAT-ADDS
- Install-WindowsFeature NET-Framework-45-Features, RPC-over-HTTP-proxy, RSAT-Clustering, RSAT-Clustering-CmdInterface, RSAT-Clustering-Mgmt, RSAT-Clustering-PowerShell, Web-Mgmt-Console, WAS-Process-Model, Web-Asp-Net45, Web-Basic-Auth, Web-Client-Auth, Web-Digest-Auth, Web-Dir-Browsing, Web-Dyn-Compression, Web-Http-Errors, Web-Http-Logging, Web-Http-Redirect, Web-Http-Tracing, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Lgcy-Mgmt-Console, Web-Metabase, Web-Mgmt-Console, Web-Mgmt-Service, Web-Net-Ext45, Web-Request-Monitor, Web-Server, Web-Stat-Compression, Web-Static-Content, Web-Windows-Auth, Web-WMI, Windows-Identity-Foundation

- Install [Microsoft Unified Communications Managed API 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=34992), Core Runtime 64-bit in Mail Server.

- Prepare schema: .\setup /PrepareSchema /IAcceptExchangeServerLicenseTerms
- Prepare ad: .\setup /Preparead /IAcceptExchangeServerLicenseTerms /OrganizationName:"MATDEG"
- Prepare domain: .\setup /PrepareAllDomains /IAcceptExchangeServerLicenseTerms

### Configuratie exchange server 2016

- pdf chamillo gevolgd.
- mail kon niet verstuurd worden naar hotmail => oplossing: enkel HoGent netwerk laat dit toe (VPN)

### Installatie SQL server

- Install SQL server 2016 (first open 1433/TCP & 4022/TCP)

## deploy

- toegevoegd aan domein matdeg.gent
- SCCM version 1606

### Prerequisites sccm server 2016

- Install SQL server 2016 (first open 1433/TCP & 4022/TCP)
- Install Windows ADK 10
- Create System Management Container in the Domain Controller System
- Extend Active Directory Schema (dit gebeurt op de domain controller terwijl de andere aanstaat)
- Add IIS Server Role
- Install BITS and Remote Differential Compression features
- Install Windows Server Update Service
- Configurate WSUS
- Install-WindowsFeature Net-Framework-Core
- Install SCCM 2016

### Configuratie sccm server 2016

- Maak login aan voor gebruiker `Matti` (zie [deze](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/create-a-login) link)

- Distribution point properties: enable PXE boot (also for unknown computers)

## host

- Windows 10
- 1 internE netwerkkaart => krijgt IP van dc01
- Install Windows Updates
- Install virtualbox guest additions

### Software

- [Download SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)

## Keys

- Windows server 2016: PFNDC-CCYF2-TC9F7-4T7QM-DPF64
- Windows 2010: 2RWNB-4QGM4-QD4WQ-QV2RC-DDBP6

## Sources

- [SCCM 2016 video guide](https://www.windows-noob.com/forums/topic/15312-how-can-i-install-system-center-configuration-manager-version-1702-current-branch-on-windows-server-2016-with-sql-2016/)
- Active directory setup [guide](https://blogs.technet.microsoft.com/canitpro/2017/02/22/step-by-step-setting-up-active-directory-in-windows-server-2016/)
- Documentatie Dirk Thijs op www.chamilo.hogent.be
- https://technet.microsoft.com/en-us/library/dd894463(v=ws.10).aspx
