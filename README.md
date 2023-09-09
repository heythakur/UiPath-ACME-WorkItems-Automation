# ACME Work-Items Automation using RE Framework

This project is designed to automate the processing of work items in the ACME system using the UiPath Robotic Enterprise Framework. It streamlines the tasks of logging in, fetching work items, processing them, and updating their status, all while utilizing UiPath Orchestrator's queue and folder management.

## Prerequisites

Before you begin, make sure you have the following:

- [UiPath Account](https://cloud.uipath.com/portal_/cloudrpa)
- [UiPath Studio](https://download.uipath.com/UiPathStudioCommunity.msi) installed on your machine.
- Access to [UiPath Orchestrator](https://www.uipath.com/platform-trial) with appropriate permissions to create folders and queues.



## How to Use

Follow these 3 simple steps to use this project:

1. Make a folder named `ACME` in UiPath Orchestrator within your account.
2. Create a queue named `workItem` in the `ACME` folder in Orchestrator.
3. Open the [Main.xaml](Main.xaml) file of this project, 'RE_for_ACME', in UiPath Studio using the same account in which the queue and folder were created. Then, run the project.



## How It Works

### 1. Initialize Process

- **InitiAllSettings:** Loads configuration data from the [Config.xlsx](Data/Config.xlsx) file and from assets.
- **GetAppCredential:** Retrieves credentials from Orchestrator assets or local Windows Credential Manager.
- **InitiAllApplications:** Opens and logs in to applications used throughout the process.
  - This workflow invokes [AcmeLogin](Framework/Custom/AcmeLogin.xamlAcmeLogin.xaml) to log in if not already logged in. 
  - It also invokes [FetchWorkItem.xaml](Framework/Custom/FetchWorkItems.xaml) to fetch Work-Items and push it into Orchestrator Queue.

### 2. Get Transaction Data

- **GetTransactionData:** Fetches transactions from an Orchestrator queue defined by `Config("OrchestratorQueueName")` or any other configured data source.

### 3. Process Transaction

- **Process:** Processes the transaction and invokes other workflows related to the specific automation process.
    - This workflow processes the transaction and invokes [ProcessQueueItem.xaml](Framework/Custom/ProcessQueueTransactions.xaml) to process the each Transactions of Queue.

- **SetTransactionStatus:** Updates the status of the processed transaction (Orchestrator transactions by default): Success, Business Rule Exception, or System Exception.

### 4. End Process

- **CloseAllApplications:** Logs out and closes applications used throughout the process.




## Documentation

Additional documentation and instructions can be found in the [Documentation](Documentation) folder of this project.



## Credits

This project is built on the UiPath Robotic Enterprise Framework template and follows best practices for robotic process automation.

## License

[![MIT License](https://img.shields.io/badge/License-MIT-red.svg)](LICENSE.txt)



## Project Made by

Thakur Dutt

## About Me

I am a passionate programmer, who's learning every day and excited about the world of programming and development. This project has given me an opportunity to enhance my skills and gain practical experience.

## Connect with me

**Email:** duttthakur444@gmail.com

<p align="left">

<a href="https://linkedin.com/in/thakur-dutt-179b79155" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="thakur-dutt-179b79155" height="30" width="40" /></a>
<a href="https://github.com/heythakur" target="blank"><img align="center" src="https://rawcdn.githack.com/rahuldkjain/github-profile-readme-generator/888aff31e1d26dd2a6acf6afebbc34970aeb0118/src/images/icons/Social/github.svg" height="30" width="40" /></a>
<a href="https://twitter.com/th4kurdutt" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/twitter.svg" alt="th4kurdutt" height="30" width="40" /></a>
</p>
<br>

Feel free to reach out if you have any questions, suggestions, or opportunities to collaborate!
