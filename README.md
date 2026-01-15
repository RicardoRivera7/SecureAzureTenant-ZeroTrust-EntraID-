<h1>Secure Azure Tenant(Zero Trust & Entra ID)</h1>


<h2>Description</h2>
Using Microsoft Azure and Entra ID, the goal is to create groups of users (Employees, Admins) then setting Role Based Acess Controls, and conditional access controls such as Multifactor Authentication. We will then test these controls by signing into different accounts to see if they work as intended.
<br />

<h2>Architecture Summary</h2> 
<b> 
Users and Admins are created and added to groups <br/>
Entra ID iss ussed to authenticate users attempting to login <br/>
Conditional Access policies enforce MFA <br/>
Azure Role-Based Access Control restricts access at the resource group level <br/>
Sign-in logs are used to validate and audit access decisions  <br/>
<br/>
<br/>

Bonus: A Break-Glass-Admin is created, it does not need MFA and is used in emergencies when services and functions are not working such as MFA itself </b> <br/>


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

Now let's make sure Authenticator and SMS is enabled <br/>
On the left menu select "security" then click "Authentication" methods <br/>
Check to see if both SMS and Microsoft Authenticator are enabled <br/>
If not, click on the option (Ex: SMS) and toggle the "Enable" slider to on (blue) <br/>
<em>Note: don't mind the other resource groups you see in my screenshot, those were just for fun, you will only have the one you made</em> <br/>
<img src="https://i.imgur.com/zbXYz16.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Now we need to create conditional access policies <br/>
Go back to the "Security" page and click on "Conditional Access" <br/>
Note: for the following steps you may need the Entra ID P2 trial <br/>
Click on "Create New policy" <br/>
For name pick something like "Require MFA for All Users" <br/>
Click on "Users" and select "All Users" <br/>
In the section click on "exclude" and Choose the Break-Glass-Admin user <br/>
Click on "Target Resources" and select "All Resources" <br/>
Click on "Grant", make sure "grant access" is selected and click on the "require multifactor authentication" <br/>
At the bottom make sure "Enable Policy" is ON <br/>
<img src="https://i.imgur.com/OoCqhoW.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Let's head back to the main Azure Page <br/>
Search for and click on "resource group" <br/>
Name it something like Test or Lab <br/>
Click Create <br/>
<img src="https://i.imgur.com/ez3bbJp.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Now let's set read and contribute permissions for each group <br/>
Click on the resource you just created <br/>
On the left side click on "Access Control (IAM)" <br/>
At the top click on "Add" and then "Add role assignment" <br/>
Search for "Reader" and click on it <br/>
At the top select "Members" section <br/>
Click the blue "+ Select members" text <br/>
Choose your Employees Group <br/>
Click "Review + Assign" <br/>
<img src="https://i.imgur.com/yoDudfH.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>


Now let's create another new role assignment <br/>
Click the "Privileged administrator roles" section <br/>
Select "Contributor" and go the the "Members" section <br/>
Add the Admins Group as the member <br/>
Click "Review + Assign" <br/>
<img src="https://i.imgur.com/niOqRxr.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>




<h2>Testing Employees and Admins</h2>

We've set all the users and policies in place, we can begin testing them (Note: feel free to add more users to either group if you want) <br/>
Go to your Entra ID main page, and on the left menu click on "Users" <br/>
Look for the user you want to login to and copy the name under "User Principal Name" <br/>
<img src="https://i.imgur.com/32EVqN4.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Open a new incognito window and navigate to the azure portal page: https://portal.azure.com <br/>
Enter the name you copied earlier and the password you saved <br/>
Now you will be required to use the Microsoft Authenticator app to verify your identity <br/>
After that you will be prompted to enter a new password, go through the rest of the setup steps <br/>
Once done you should be logged in as the user you chose <br/>
<img src="https://i.imgur.com/oZRTfAB.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Let's check to see if our other policies such as Reader and Contributer are working <br/>
If you are signed in as employee you should only have Reader permissions and can't create new things <br/>
To test this go to "Resource Groups" or "Virtual Machines" <br/>
At the top you should see a message and in there it says "Code:AccessDenied" <br/>
This means our employee Reader policy is working! <br/>
<img src="https://i.imgur.com/lqem0XB.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>


Now let's test the Admin user <br/>
Login to the Admin account doing the same setup steps you had to for the employee account <br/>
To test this go to "Resource Groups" or "Virtual Machines" <br/>
You should be able to view the resource groups that are available and create a new resource group (same thing with the virtual machines) <br/>
<img src="https://i.imgur.com/iu82rrh.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

<h2>Checking the Sign-in logs</h2>

On your main account head back to the Entra ID home page <br/>
On the left menu, under "Monitoring" click "Sign-in logs" <br/>
Here you can see your users under "user principal name" or "users" <br/>
You can see whether or not your conditional access policies were successful under "conditional access" with a success or Failure <br/>
(Note: if your status under "status" was interupted, this was most likely during your inital new login process so failure for the conditional access is expected) <br/>
<img src="https://i.imgur.com/hK7QFnw.png" height="80%" width="80%" alt="EntraID"/>
<br/>
<br/>

Bonus: Don't forget to make sure to test your Break-Glass-Admin by logging into it, to test it works make sure when you login that MFA is not required and that you can create resoruce groups!

</p>
