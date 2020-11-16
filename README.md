## SMD Agent Installation : Unattended mode via Ansible

The Solution Manager Diagnostics (SMD) component of SAP Solution Manager provides all functionality to centrally analyze and monitor a complete system landscape. Data Services can be monitored by the SMD server if an SMD Agent is installed. The SMD Agent gathers information for the SMD which can then be used for root cause analysis. Information collected and sent to the SMD server includes back-end server configurations and the location of server log files.

Data Services provides support for performance and availability monitoring through CA Wily Introscope in Solution Manager Diagnostics through an integration with the NCS library. The NCS library is installed automatically with Data Services.

The following table describes the components of SMD.

Component|Notes
---------|------
SAP Solution Manager|You must have Solution Manager 7.01 SP26 or later installed
SMD Agent|A local agent (DIAGNOSTICS.AGENT) that collects and sends the information to the SMD server. This agent must be downloaded and installed on each Job Server that you want to monitor. The Data Services installation does not install this agent for you.Information about installing and configuring the agent is available at: https://support.sap.comInformation.
CA Wily Introscope|An application performance management framework. Introscope Enterprise Server is part of Solution Manager. There is no need to perform a separate installation. For more information, see https://support.sap.com
SAPOSCOL|The SAP Operating System Collector provides operating system data to the SMD and Introscope.

All of these components are available for download from http://support.sap.com/swdc
