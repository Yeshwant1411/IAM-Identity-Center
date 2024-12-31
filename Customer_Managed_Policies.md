# Creating Custom Permissions using IAM

### To create a policy in AWS that allows a user to only read EC2 instances, you need to define a policy that grants permission for "Describe" actions but not any actions that modify or create instances.

![Screenshot from 2024-12-31 06-53-28](https://github.com/user-attachments/assets/e732bf87-9a7c-4f3b-b578-0f8cd6c46e97)


Explanation:

  Action: Specifies the EC2 actions the user is allowed to perform. Here, we're allowing "Describe" actions (e.g., DescribeInstances, DescribeInstanceStatus, etc.) which give   read-only access to information about instances and related resources.
  Effect: The effect is set to Allow, meaning the actions listed will be permitted.
  Resource: We specify "*" to indicate that the user can perform these actions on all EC2 instances in the account.

Steps to implement this:

   1.Create a custom IAM policy:
        Go to the IAM console in AWS.
        Under "Policies", click on "Create policy".
        Select the "JSON" tab and paste the policy above.
        Review and name the policy, then create it.

   2.Attach the policy to the IAM user/group:
        Go to the IAM console and select the user or group you want to grant this access.
        Under the "Permissions" tab, click "Add permissions" and choose "Attach policies directly".
        Search for your custom policy, select it, and click "Next: Review" to apply the changes.

This policy will grant the user read-only access to EC2 instances without allowing any modification or creation of instances.

### To modify the policy so that it only applies to a specific EC2 instance (e.g., a Jenkins server), you need to adjust the Resource field in the policy. Instead of granting permissions for all EC2 instances ("Resource": "*"), you will specify the ARN (Amazon Resource Name) for the specific instance.
Steps to get the ARN of the Jenkins EC2 instance:

  Go to the EC2 dashboard in the AWS Management Console.
  Find the instance you want to apply the policy to (in this case, the Jenkins server).
  Copy the Instance ID of the Jenkins server (e.g., i-0abcd1234efgh5678).
  The ARN for an EC2 instance is in this format:

arn:aws:ec2:<region>:<account-id>:instance/<instance-id>

For example, if your instance ID is i-0abcd1234efgh5678 in the us-west-2 region, the ARN would look like:

  arn:aws:ec2:us-west-2:123456789012:instance/i-0abcd1234efgh5678

Modified Policy for Specific EC2 Instance (Jenkins Server):

![Screenshot from 2024-12-31 06-59-55](https://github.com/user-attachments/assets/f9be66cd-8380-456e-a77f-3cfd8fcf9e04)


Explanation of the Changes:

  Resource: The Resource field now specifies the ARN of the Jenkins EC2 instance. Replace "arn:aws:ec2:us-west-2:123456789012:instance/i-0abcd1234efgh5678" with the actual      ARN of your Jenkins EC2 instance.
  The policy grants the user read and write permissions only on that specific EC2 instance, not on any other instance in your AWS account.

Steps to Implement This Policy:

  1. Create the IAM Policy:
        Go to the IAM console in AWS.
        Under Policies, click on Create policy.
        Select the JSON tab and paste the modified policy provided above.
        Replace the ARN (arn:aws:ec2:us-west-2:123456789012:instance/i-0abcd1234efgh5678) with the ARN of your Jenkins EC2 instance.
        Review and name the policy, then click Create policy.

   2. Attach the Policy to the IAM User/Group:
        Go to the IAM console and select the user or group you want to assign the permissions to.
        Under the Permissions tab, click Add permissions.
        Choose Attach policies directly.
        Search for your custom policy, select it, and click Next: Review to apply the changes.

This will restrict the permissions to only the Jenkins server instance, preventing the user from performing any actions on other EC2 instances in your account.
