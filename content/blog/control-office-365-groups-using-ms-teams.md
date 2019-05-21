---
title: "Getting better control over Office 365 groups when using MS Teams"
date: 2019-05-21T00:00:57+01:00
draft: false
banner: "/img/blog/groupsteams/groupsteams0.png"
author: "Luc Marolt - MCSA Office 365"
categories: ["Office 365"]
tags: ["promo"]
---



## - <br> 

<p>Many of our customers are starting or continue to use Microsoft Teams as an effective company-wide collaboration tool. Most of these companies are encouraging their Office 365 users to set up their own MS Teams initiative, resulting sometimes in an unstructured array of Teams but implicitly also in a pile of (unwanted) Office 365 groups.
Every time a Team is created an Office 365 group with the same name is also created in the background. Imagine only the number of groups including the word “test”. To avoid this situation requires being more restrictive when it comes to crating new Teams or Office 365 groups in general.
 </p>

##### One fancy way of doing this can be as follows: <br>


* Create a new Security (not Office 365) Group called e.g. “Office 365 Group Creators” and add selected members
* Restrict the creation of Office 365 Groups to only members of this group. For this use the PowerShell script below “LimitO365GroupCreation.ps1”
* Create a simple SharePoint custom list with the fields required to create Office 365 Groups (Name, Description, Alias, etc.). Allow access for everyone
* Publish a MS Flow to that list that allows filling out the Group details by the end-user and then sends it to one or several approvers
* When approved an Office 365 Group Creator creates the Office 365 group that will be allowed for Team creation

<br>
Here is the challenge: <br>

* Only the Office 365 Group Creators can create new Teams
* But they can only use Office 365 Groups that they are an owner off
* For security reasons they cannot be permanent owners of those groups
* The Group Creator should only be a Group Owner for the duration of creating the Team
 

  <img class="img-fluid mt-3 mb-3" src="/img/blog/groupsteams/groupsteams1.png" />
 

 
To achieve this one of the Office 365 Group Creators launches the PowerShell script below “NewTeam.ps1”

* The script prompts for the necessary information
* Adds the user to the Group as an Ownero	Allows for manual Team Creation
* There is a snatch here: to create a new Team using PowerShell this can (for now) only be done using the Group ID. However, the Group ID (for now) cannot be obtained using PowerShell hence user interactivity of some kind is required
* Downgrades the user to a Group Member (Owners cannot be deleted from a Group)
* Removes the member from the Group

  <img class="img-fluid mt-3 mb-3" src="/img/blog/groupsteams/groupsteams2.jpg" />


  If you want to hear how we can assist you to make your Office 365 environment more productive simply contact Knut Skogvold on +47 90 09 50 88 or e-mail customer service in Point Taken.
  <br><br>

### PowerShell scripts:


#### LimitO365GroupCreation.ps1

    $GroupName = "Office 365 Group Creaters"
    $AllowGroupCreation = "False"

    Connect-AzureAD

    $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
    if(!$settingsObjectID)
    {
    	  $template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
        $settingsCopy = $template.CreateDirectorySetting()
       New-AzureADDirectorySetting -DirectorySetting $settingsCopy
       $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
    }

    $settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
    $settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

    if($GroupName)
    {
	    $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
    }

    Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

    (Get-AzureADDirectorySetting -Id $settingsObjectID).Values


#### NewTeam.ps1

    #Create credential object
    $credObject = Get-Credential
    #Import the Exchange Online ps session
    Write-Host "Connecting to Exchange online (ignore any warnings)" -ForegroundColor DarkCyan
    $ExchOnlineSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $credObject -Authentication Basic -AllowRedirection
    Import-PSSession $ExchOnlineSession
    Write-Host Connection successful! -ForegroundColor Green
    $User = Read-Host -Prompt 'What is your email address?'
    $GroupName = Read-Host -Prompt 'What is the Group Name? Use NO "quotes"!!'
    Write-Host Adding $User as a group owner now to $GroupName -ForegroundColor DarkCyan
    Write-Host This can take a few seconds... -ForegroundColor Yellow
    Add-UnifiedGroupLinks –Identity $GroupName –LinkType Members –Links $User
    Add-UnifiedGroupLinks –Identity $GroupName –LinkType Owners –Links $User
    Write-Host Create the Team and return here when finished -ForegroundColor Green
    Pause
    Write-Host Removing the user from the group again -ForegroundColor DarkCyan
    Remove-UnifiedGroupLinks –Identity $GroupName –LinkType Owners –Links $User -Confirm:$false
    Remove-UnifiedGroupLinks –Identity $GroupName –LinkType Members –Links $User -Confirm:$false
    Write-Host User removed from $GroupName! -ForegroundColor Green
    Write-Host Finished! -ForegroundColor Yellow
    Pause


<br><br>
Vil du vite mer?
<br><br>
Ta kontakt med Knut Skogvold på telefon 900 95 088 eller send en <br>
 <img class="card-img-top img-profil img-round mx-auto" src="/img/people/knut-round.jpg" style="float:right;">
<a href="kundeservice i pointtaken.no"  rel="nofollow" onclick="this.href='mailto:' + 'kundeservice' + '@' + 'pointtaken.no'">e-Post til kundeservice i Point Taken</a>
<br>
<br>


<br>
    <a class="btn btn-primary btn-full" href="/contact/" role="button">Vil du vite mer? Kontakt oss!</a>
<br>
<br>