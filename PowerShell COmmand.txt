 # Import the Active Directory module
Import-Module ActiveDirectory

# Define the path to the CSV file
$csvPath = "C:\Users\Administrator\Desktop\Users.csv"

# Read the CSV file
$userList = Import-Csv $csvPath

# Loop through each user in the CSV and create an AD user
foreach ($user in $userList) {
    $userName = $user."User Name"
    $firstName = $user."First Name"
    $lastName = $user."Last Name"
    $displayName = $user."Display Name"
    $jobTitle = $user."Job Title"
    $department = $user."Department"
    $officeNumber = $user."Office Number"
    $officePhone = $user."Office Phone"
    $mobilePhone = $user."Mobile Phone"
    $fax = $user."Fax"
    $address = $user."Address"
    $city = $user."City"
    $state = $user."State or Province"
    $postalCode = $user."ZIP or Postal Code"
    $country = $user."Country or Region"
    $password = $user."Password"

    # Check if a password is provided
    if ($password -ne $null -and $password -ne "") {
        $securePassword = $password | ConvertTo-SecureString -AsPlainText -Force

        # Create the AD user
        New-ADUser -Name $displayName -GivenName $firstName -Surname $lastName -SamAccountName $userName -DisplayName $displayName -Title $jobTitle -Department $department -Office $officeNumber -OfficePhone $officePhone -MobilePhone $mobilePhone -Fax $fax -StreetAddress $address -City $city -State $state -PostalCode $postalCode -Country $country -AccountPassword $securePassword -Enabled $true

        Write-Host "User '$displayName' created."
    } else {
        Write-Host "User '$displayName' skipped due to missing or empty password."
    }
}

Write-Host "User creation completed."
 
