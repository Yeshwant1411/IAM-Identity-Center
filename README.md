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
