<h1>Secure Azure Tenant(Zero Trust & Entra ID)</h1>


<h2>Description</h2>
Using Microsoft Azure and Entra ID, the goal is to create groups of users (Employees, Admins) then setting Role Based Acess Controls, and conditional access controls such as Multifactor Authentication. We will then test these controls by signing into different accounts to see if they work as intended.
<br />

<h2>Prerequisites</h2>
- <b>Make a Microsoft Azure Account: https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account </b> <br/>
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
<img src="https://i.imgur.com/s9cQ4qx.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>
Click "Review + Create" then "Create" again <br/>
You now have your first employee user! Now go to "add" and create another new user <br/>
This time we're making the admin, so under "User Principal name" enter something like Admin or Admin1 <br/>
Do the same for display name <br/>
Remeber to save the password for this account too <br/>
<img src="https://i.imgur.com/weglirO.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Click the blue "Review + Create" button then click the "Create" button <br/>
We will create one more user, this user will be for admin emergencies only so that things like MFA aren't needed in case there are issues with services or functions like that <br/>
Create a new user and for both name fields name them Break-Glass-Admin <br/>
Make sure you save the password somewhere and create the user <br/>
<br/>
<br/>

Now we will create some groups, an Employees group and an Admin group <br/>
Click on "Add" and click on "Group" <br/>
Make sure "Group Type" is security <br/>
For the group name enter Employees <br/>
Under the members section click on the blue text that sasys "No members selected" <br/>
Add your employee user and click "Create" <br/>
<img src="https://i.imgur.com/G7nq1eW.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Now let's create the admin group <br/>
Create a new group and Make sure "Group Type" is security <br/>
Name the group Admins or something similar <br/>
Add your Admin user and Break-Glass-Admin user <br/>
<img src="https://i.imgur.com/V0wbwBa.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>



Now let's make sure MFA and SMS is enabled <br/>
On the left menu select "security" then click "Authentication" methods <br/>
Check to see if both SMS and Microsoft Authenticator are enabled <br/>
If not, click on the option (Ex: SMS) and toggle the "Enable" slider to on (blue) <br/>
<em>Note: don't mind the other resource groups you see in my screenshot, those were just for fun, you will only have the one you made</em> <br/>
<img src="https://i.imgur.com/zbXYz16.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>


Now we need to create conditional access policies <br/>
Go back to the "Security" page and click on "Conditional Access" <br/>
Note: for the following steps you may need the Entra ID PD 2 trial <br/>
Click on "Create New policy" <br/>
Click on "Users" and select "All Users" <br/>
In the section click on "exclude" and Choose the Break-Glass-Admin user <br/>
Click on "Target Resources" and select "All Resources" <br/>
<em>Note: don't mind the other resource groups you see in my screenshot, those were just for fun, you will only have the one you made</em> <br/>
<img src="https://i.imgur.com/zbXYz16.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>




<h2>Creating a Vritual Network</h2>



</p>
