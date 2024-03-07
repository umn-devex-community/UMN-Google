# UMN-Google

## Update '2.0.1'

Updating to work with pwsh 7.4, OS agnostic between Windows and Linux OS. Testing on Ubuntu 22 LTS via WSL. Backwards compatible to powerShell 5.1 of existing cmdlets.

Cmdlet updates

Get-GOAuthTokenService now supports JSON files in powerShell major version 7. When collecting return, ensure you capture as string.
[string]$accessTokenJSON = Get-GOAuthTokenService -iss $iss -scope $scope -jsonPath $jsonPath

Get-GOAuthTokenUser has removed IE11 as this is no longer functional on modern operating systems. Replaced with selenium webdriver version 4.
Tested with Edge selenium webdriver - currently the webdriver is expecting this.
Requires GUI - will maybe get back around to selenium on Linux to pass credentials, but with MFA this is a per business solution.

Get-GOAuthIdTokenSelenium - added Edge selenium driver cmdlet. Leaving Get-GOAuthIdToken which uses IE still from the developer console.

Get-GOAuthTokenDevice - added a cmdlet when no webdriver or browser is available to the system. Generates Url to allow user to log in using any browser to get auth code needed to generate token.

### Google Group Management Added - service account must have manage to the Google Workspace to modify and read using Cloud Identity API

Add-gGroupMembership - add user by UPN to google group membership

Get-gGroupID - find group ID by name

Get-gGroupMembership - query all members by group ID

Remove-gGroupMembership - remove member by google group membership name - groups/iud/memberships/userID

Set-gSuiteGroupMembership - set bulk membership changes from an arrayList

New-gSuiteGroup - warning - most admins should not have the super user to be able to use this function.

## Update '1.2.12'

Added get-gAppScriptsProject, get-gAppScriptsProjectContent, and send-gAppsScriptFunction. The last function is designed to call functions stored in a Google App Scripts Standard Project. You need to make sure to publish 'Deploy as API Executable' and Enable API access to your project. Allows calling functions with or without parameters.

## Update '1.2.11'

Get-GOAuthTokenUser previously only retuned part of token response.  Update returns full response and adds alias to 'accesstoken' to maintain backwards compatability.

## Update '1.2.10'

Updated Get-GOAuthTokenService to accept a RSA object instead of building it within the function. Intended for use with KeyVaults and Automation.
Also added support to build the RSA object with a certificate object rather than file path, also intended for use with KeyVaults and Automation.

## Update '1.2.9'

Modify Get-GSheetData to set all empty properties of the returned object to an empty string instead of $null.
Previously any empty value in a row after the last value would be $null but empty values before the last value would be an empty string.
This makes the behavior consistent so empty values are always empty strings.

## Update '1.2.8'

Add function Get-GOAuthIdToken -- Function returns a Google ID Token for a user for a given Client ID

## Update '1.2.7'

Expand Get-GFilePermissions to get more details and get specific permissions if specified

## Update '1.2.6'

Add functions Get-GFileID and Get-GFile'
Get-GFileID with fetch the ID of any file in Drive that you have access to.  This can then be feed into other functions
Get-GFile can be used to download a file from Drive.  Future releases will support converting Google Docs to other formats as provided by the Google API

## Update '1.2.5'

Add function Remove-GSheetSheetRowColumn.  Removes one or more rows or columns

## Update '1.2.3'

Add function Set-GSheetDropDownList.  Sets data validation on cells in a column and creates drop down list for users to choose options you specify.

EXAMPLE: Set-GSheetDropDownList -accessToken $accessToken -startRowIndex 1 -endRowIndex 10 -columnIndex 9 -sheetName 'Sheet1' -spreadSheetID $spreadSheetID -inputMessage "Must be one of 'Public','Private Restricted','Private, Highly-Restricted'" -values @('Public','Private Restricted','Private, Highly-Restricted')

## Update '1.2.2'

Catch up notes. Module is now code signed.
Fixed plurality typo for remove-gfilepermissions id parameter.

## Update '1.1.1'

Added function to move google drive file.

## Update '1.1.0'

Organized all functions.
Added parameter listing to every function.
Updated help files for every function.
Distinguished between 'fileID' and 'spreadSheetID' -- these are the same, but require different API when taking certain actions.

## General Notes

Based of API docs https://developers.google.com/sheets/

Set-up: Create a project https://console.developers.google.com/apis/dashboard
Enable the API as needed such as Drive, Sheets, Cloud Identity
Each Service in google has its own API and needs to be enabled one by one for each you want to use.
Select the 3 bars in the upper left corner and choose API Manager, then click on Enable API
Select an appropriate Service
Create a Service Account

You'll need all this info to get to the point of being able to get accesstokens that all function require.

If you create a new sheet with the service account ONLY the service account will have access.  You'll need to call Set-GSheetPermissions to others or yourself if you want to be able to see it in the WebUI.
