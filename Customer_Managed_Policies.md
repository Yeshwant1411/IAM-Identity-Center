# Creating Custom Permissions using IAM

To create a policy in AWS that allows a user to only read EC2 instances, you need to define a policy that grants permission for "Describe" actions but not any actions that modify or create instances.

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances",
        "ec2:DescribeInstanceStatus",
        "ec2:DescribeImages",
        "ec2:DescribeRegions",
        "ec2:DescribeAvailabilityZones"
      ],
      "Resource": "*"
    }
  ]
}

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
