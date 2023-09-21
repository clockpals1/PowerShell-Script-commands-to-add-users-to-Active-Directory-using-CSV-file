# PowerShell-Script-commands-to-add-users-to-Active-Directory-using-CSV-file
PowerShell Script commands to add users to Active Directory using CSV file

This PowerShell script automates the creation of Active Directory (AD) users based on the data provided in a CSV file. 

Here's a summary of what it does:

Import Active Directory Module: 
It imports the Active Directory module, which is required for managing AD users and their attributes.

Define CSV File Path: 
It specifies the path to the CSV file containing user data. This CSV file should contain columns with user attributes like name, username, job title, department, etc.

Read CSV File: 
It uses the Import-Csv cmdlet to read the CSV file and stores the user data in the $userList variable.

User Creation Loop: 
It loops through each user's data in the CSV file and extracts attributes such as name, username, password, and contact information.

Password Check: 
It checks if a password is provided for each user. If a password exists, it converts it to a secure string.

Create AD User: 
It uses the New-ADUser cmdlet to create a new AD user with the extracted attributes, including the provided password (if available).

Logging: 
It provides feedback by writing messages to the console, indicating whether each user was created or skipped due to a missing or empty password.

Completion Message: 
It displays a message confirming the completion of the user creation process.

In summary, this script automates the creation of AD users, ensuring that each user is assigned the appropriate attributes and has a secure password if one is provided in the CSV file. It also handles cases where users might have incomplete data.




