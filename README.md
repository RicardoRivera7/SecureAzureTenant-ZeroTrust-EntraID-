# SecureAzureTenant-ZeroTrust-EntraID-

<h1>Secure Azure Tenant(Zero Trust & Entra ID)</h1>


<h2>Description</h2>
Using Microsoft Azure and Entra ID, the goal is to create groups of users (Employees, Admins) then setting Role Based Acess Controls, and conditional access controls such as Multifactor Authentication. We will then test these controls by signing into different accounts to see if they work as intended.
<br />

<h2>Prerequisites</h2>
- <b>Make a Microsoft Azure Account: https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account </b>
- <b>Download Microsoft Authenticator App on your phone (This will be needed for MFA) </b> 


<h2>Software Used</h2>

- <b>Microsoft Azure (using free subscription) </b>

<h2>Environments Used </h2>

- <b>Microsoft Azure</b>
- <b>Microsoft Entra ID (using free trial for Microsoft Entra ID P2) </b> 

<h2>Links</h2>

-[Azure Free Subscription](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account)
<br/>
-[To Cancel your Entra ID PD 2 Trial](https://admin.cloud.microsoft/?#/subscriptions/assets/)
<br/>
<br/>
<br/>




<h1>Azure Virtual Machine Setup:</h1>

<p align="left">

<h2>Setting Up Users and Groups</h2>

Go to the Azure portal at the homepage and click on "Microsoft Entra ID" (or search for it) <br/>
At the top of the Overview page click "Add", then "New User" -> "Create New User" <br/>
Here we will make an employee user first, so under "User principal name" enter something like employee1 <br/>
Under "Display name" enter something like employee1 or employee-john <br/>
Make sure in the passwordd section you copy and save that password somewhere, this will be needed to login later <br/>
<img src="https://i.imgur.com/s9cQ4qx.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>
Click "Review + Create" then "Create" again <br/>
You now have your first employee user! Now go to "add" and create another new user <br/>
This time we're making the admin, so under "User Principal name" enter something like Admin or Admin1 <br/>
Do the same for display name <br/>
Remeber to save the password for this account too <br/>
<img src="https://i.imgur.com/weglirO.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

Click the blue "Review + Create" button <br/>
Then click the blue "Create" button <br/>
Refresh the page and you should see your resource group there! <br/>
<em>Note: don't mind the other resource groups you see in my screenshot, those were just for fun, you will only have the one you made</em> <br/>
<img src="https://i.imgur.com/78dmS0D.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

<h2>Creating a Vritual Network</h2>



</p>
