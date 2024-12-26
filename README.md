# IAM-Identity-Center
It is used to be called AWS Single Sign On or SSO.

It provides a Single login across:

-All AWS accounts (Leveraging AWS Organizations)

-It works with cloud based applications like Salesforce, Box, Microsoft 365 etc.,

-We can use same login for EC2 instances running Windows.

-As well as other SAML 2.0 enabled applications.

Can use multiple isentity poviders such as Active Directory, Okta, the built-in IAM store and more.

With 'Regular' IAM:
Lets say for example we have three AWS accounts Dev, Test, Prod.
If we need to switch between those accounts throughout our day, then basically we need to log into each one of them seperately and also we have to manage access key ID's and secret access keys sperately as well, it is tiresome work. 
![Screenshot from 2024-12-26 14-21-33](https://github.com/user-attachments/assets/62c309c4-cbbe-49f5-9d62-17da90616125)

With IAM 'Identity Center':
There will be a seperate login page just a Single login, no matter how many accounts or application you have, it will lists all the accounts if we have configured other applications such as Microsoft 365, Salesforce etc.,
![Screenshot from 2024-12-26 14-34-48](https://github.com/user-attachments/assets/3d7b3224-4b7c-4645-80d3-6142b56616e3)

So we are goin to login to the page and it will take us to the Access Portal, where it will lists all the accounts.
![Untitled design](https://github.com/user-attachments/assets/2f8cbde1-5899-4920-b1b1-a3ba816b0931)

The recommended way to do Identity and access management through IAM Identity Center in AWS, it reduces complexity and it gives better visibility because it integrates with cloudtrail and can do audits on Single Sign On access.

To create an IAM Identity Center (AWS SSO) with the permission sets for EC2 Full Access, S3 Full Access, and EC2 Instance Connect, follow these steps:

1. Set Up AWS IAM Identity Center (AWS SSO)

   Navigate to IAM Identity Center:

   Go to the AWS Management Console.

   In the search bar, type IAM Identity Center or SSO, and select it.

   Set up IAM Identity Center:

   If this is your first time, click on Enable IAM Identity Center. You will be prompted to select a directory for users.

   Follow the prompts to enable IAM Identity Center with your AWS organization’s identity source. You can choose AWS SSO as your identity source or connect to an external identity provider
   (e.g.,Active Directory, Okta, etc.).

  ![Screenshot from 2024-12-26 15-07-14](https://github.com/user-attachments/assets/b7c144f9-44d2-49f2-b3ce-0271372cf2cb)
 

2. Create the User rudraawsidentity

   Once IAM Identity Center is enabled, follow these steps to create a new user:

   Navigate to Users:

   In the IAM Identity Center console, go to the Users tab under User Management.

   Create User:

   Click Add user.

   Enter the username.

   Choose the Identity Store (either AWS SSO or an external identity provider).

   Click Next and set up any attributes for the user (e.g., email, name).

   Choose the appropriate user type (if using AWS SSO, users can be created without email addresses).

   Create User and Assign to Groups:

   Skip assigning to a group (for now) and click Next.

   Finish:Review and create the user. You can optionally configure MFA at this stage.

   Once the user is created, you'll be able to assign the necessary permission sets.

3. Create Permission Sets

   Navigate to Permission Sets:

   In the IAM Identity Center console, go to Permission sets under the AWS Access Management section.

   Create Permission Set for EC2 Full Access:

   Click Create permission set.

   Select the EC2 Full Access policy from the built-in policies (or create a custom policy if needed).

   Set the permission set’s name (e.g., EC2 Full Access).

   Review and create the permission set.

   Create Permission Set for S3 Full Access:

   Again, click Create permission set.

   Select the S3 Full Access policy from the built-in policies (or create a custom policy).

   Set the permission set’s name (e.g., S3 Full Access).

   Review and create the permission set.

   Create Permission Set for EC2 Instance Connect:

   Click Create permission set.

   Select the EC2 Instance Connect policy from the built-in policies (or create a custom policy).

   Set the permission set’s name (e.g., EC2 Instance Connect).

   Review and create the permission set.

4. Assign Permission Sets to the User rudraawsidentity

   Now that the permission sets are created, you can assign them to your user.

   Navigate to User Assignments:
   
   In the IAM Identity Center console, go to Assignments under AWS Access Management.
   
   Assign Permission Sets:
   
   Click Assign users.
   
   Choose the user rudraawsidentity from the list.
   
   Click Next.
   
   Select the permission sets you created:
   
   EC2 Full Access
   
   S3 Full Access
   
   EC2 Instance Connect

   Choose the AWS Account where these permissions should apply. You can assign the permissions to all accounts or specific accounts.
   
   Click Next and then Assign.

5. Test Access

   Login as the User:

   To test the configuration, you can log in as the user rudraawsidentity via the AWS SSO portal (or the respective identity provider).
   
   Ensure the user can access the EC2, S3 services, and use EC2 Instance Connect functionality.
