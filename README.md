# IAM– Identity Access Management in Cloud
## AIM

## IAM Working Overview

This repository provides a comprehensive overview of Identity and Access Management (IAM), focusing on its purpose, components, and implementation practices in cloud and enterprise environments. The aim is to educate developers, system admins, and security teams on IAM essentials and offer a hands-on guide for setting up and managing IAM policies.

## Introduction
Identity and Access Management (IAM) is a framework of policies, technologies, and practices designed to manage digital identities and control access to resources. IAM helps ensure the right individuals have the right access to resources at the right time. It is crucial for securing sensitive data and resources in any organization, especially those operating in a cloud environment.
Objectives

•	To understand the purpose and benefits of IAM
•	To learn about the core components of IAM
•	To gain hands-on experience setting up and managing IAM policies
•	To explore best practices for enhancing security through IAM

## Prerequisites

Before diving into IAM, you should have a foundational understanding of:

•	Cloud Services (AWS, Azure, Google Cloud)
•	Basic Networking and Security Concepts
•	Programming (Python, Bash, or any language preferred for API interactions)
•	Version Control (Git for managing this project)

## Core Components of IAM

IAM encompasses several core components that work together to provide secure access management:

•	Identities: Represent users, roles, or services accessing resources. Identities can be internal users, external partners, or applications.
•	Policies: Define permissions for each identity, specifying what actions they can perform on which resources.
•	Roles: Enable resource-specific permissions that can be assumed by users or services, allowing temporary access as needed.
•	Authentication: The process of verifying an identity, typically through credentials such as passwords or tokens.
•	Authorization: Determines what an authenticated identity can access or modify, enforced through policies.

## IAM Best Practices

1.	Use the Principle of Least Privilege: Limit permissions to the minimum necessary.
2.	Enable Multi-Factor Authentication (MFA): Protect against unauthorized access.
3.	Implement Role-Based Access Control (RBAC): Group permissions by roles to simplify management.
4.	Regularly Audit and Monitor Access Logs: Stay aware of access patterns and detect suspicious activities.
5.	Rotate and Manage Access Keys Carefully: Reduce risks by rotating keys frequently.

## Setup Guide

1.	Configure IAM Roles and Policies

•	Step 1: Create an IAM role with specific permissions for your users or applications.
•	Step 2: Attach policies to roles, limiting permissions according to your needs.
•	Step 3: Test access by assuming roles and attempting various actions.

2.	Enable Multi-Factor Authentication (MFA)

•	Step 1: Go to your IAM console and select your user account.
•	Step 2: Choose "Security credentials" and follow instructions to enable MFA.

3.	Set Up Identity Federation

•	Step 1: Configure identity providers (IdP) like SAML or OpenID Connect for single sign-on.
•	Step 2: Map IdP roles to IAM roles for seamless access control.

4.	Monitor and Audit with CloudTrail

•	Step 1: Enable logging of all IAM activity using services like AWS CloudTrail.
•	Step 2: Regularly review logs to ensure compliance with security policies.

## Examples

Here are a few basic examples of IAM commands and scripts:
•	Creating a User:
aws iam create-user --user-name NewUser
•	Attaching a Policy to a User:
aws iam attach-user-policy --user-name NewUser --policy-arn arn:aws:iam::aws:policy/ReadOnlyAccess
•	Creating an Access Key for a User:
aws iam create-access-key --user-name NewUser

## Lab Overview:
This lab provisions the following IAM resources for you to explore:
● Three users:
user-1,user-2, and user-3
● Three groups: with the following policies:
o S3 Support:
Read-Only access to Amazon Simple Storage Service (Amazon S3).
o EC2 Support:
Read-Only access to Amazon Elastic Compute Cloud (Amazon EC2).
o EC2 Admin: Ability to View ,Start, and Stop EC2 instances

![image](https://github.com/user-attachments/assets/0689c04a-a85c-4e9b-833c-e126db1fdb2a)

You might receive error messages when performing actions beyond the steps provided in this lab guide. The lab
relies on IAM, which limits your access to the services authorized for use in the lab. The error messages will not
impact your ability to complete the lab.
Icon key
Various icons are used throughout this lab to call attention to different types of instructions and notes. The following
list explains the purpose for each icon:
● Caution: Information of special interest or importance (not so important to cause problems with the
equipment or data if you miss it, but it could result in the need to repeat certain steps).
● Consider: A moment to pause to consider how you might apply a concept in your own environment or to
initiate a conversation about the topic at hand.
● Expected output: A sample output that you can use to verify the output of a command or edited file.
● File contents: A code block that displays the contents of a script or file you need to run that has been precreated for you.
● Learn more: Where to find more information.
● Note: A hint, tip, or important guidance.
● Task complete: A conclusion or summary point in the lab.
● Warning: An action that is irreversible and could potentially impact the failure of a command or process
(including warnings about configurations that cannot be changed after they are made).

## Start lab
1. To launch the lab, at the top of the page, choose Start Lab.
Caution: You must wait for the provisioned AWS services to be ready before you can continue.
2. To open the lab, choose Open Console .
You are automatically signed in to the AWS Management Console in a new web browser tab.
## Warning: Do not change the Region unless instructed.
## Common sign-in errors
## Error: Choosing Start Lab has no effect

In some cases, certain pop-up or script blocker web browser extensions might prevent the Start Lab button from
working as intended. If you experience an issue starting the lab:
● Add the lab domain name to your pop-up or script blocker’s allow list or turn it off.
● Refresh the page and try again.

## Task 1.1: Explore IAM users, groups, and policies
In this task, you explore the IAM users and groups that we created for you.
3. At the top of the AWS Management Console, in the search bar, search for and choose IAM.
4. In the left navigation pane, choose Users.
The list below containers the existing users:
o user-1
o user-2
o user-3
5. Choose the user-1 link.
The summary page for user-1 opens, with the Permissions tab displayed. Notice that user-1 does not have any permissions.
6. Choose the Groups tab.
Note: user-1 does not belong to any groups.
7. Choose the Security credentials tab.
In the Console sign-In section, note that user-1’s Console password is enabled.
8. In the left navigation pane, choose User groups.
The list below contains the existing groups:
o EC2-Admin
o EC2-Support
o S3-Support
9. Choose the EC2-Support group name link.
10. In the summary page for the EC2-Support group, choose the Permissions tab.
This group has a managed policy associated with it - AmazonEC2ReadOnlyAccess. Managed policies are pre-built
policies (built either by AWS or by your administrators) that can be attached to IAM users and groups. When
updated, all users and groups associated with the policy inherit the changes to that policy.
11. Expand the Plus icon to expand the contents of AmazonEC2ReadOnlyAccess.
A policy defines the actions allowed or denied for specific AWS resources. This policy grants permission to list and
describe information about EC2, Elastic Load Balancing, Amazon CloudWatch, and Auto Scaling. Support role
policies commonly restrict access to a read-only level, without the ability to modify AWS resources.
The list below outlines the basic structure of an IAM policy:
o Effect indicates whether to Allow or Deny the permissions.
o Action specifies the API calls allowed to an AWS service (such as cloudwatch:ListMetrics).
  Resource defines the scope of entities covered by the policy rule (i.e., a specific Amazon S3 bucket, Amazon EC2 instance, or
12. In the left navigation pane, choose User groups.
13. Choose the S3-Support group name link.
14. Choose the Permissions tab.
15. Expand the Plus icon to expand the contents of AmazonS3ReadOnlyPolicy.
The S3-Support group has the AmazonS3ReadOnlyAccess policy attached. This policy has permissions to get and list resources from Amazon S3.
16. In the left navigation pane, choose User groups.
17. Choose the EC2-Admin group name link.
This group differs slightly from the other two groups. Instead of a managed policy, it has an inline policy, a policy
assigned to one discrete user or group, and typically used to apply permissions for one-off situations.
18. Choose the Permissions tab.
19. Expand the Plus icon to expand the contents of EC2-Admin-Policy.
This policy grants permission to view (describe) information about Amazon EC2 resources, start and stop instances, and describe CloudWatch alarms.
## Task 1.2: Manage users and groups
In this task, you work with the users and groups, enabling permissions to support a business scenario.
You can ignore any “not authorized” errors that appear during this task caused by limited permissions in your lab
account. The error messages will not impact your ability to complete the lab.
## Business scenario
Your company’s use of Amazon Web Services grows over time. The company uses many Amazon EC2 instances
and a significant amount of Amazon S3 storage. You want to grant access to new staff members based on their job
functions, as shown in the table.

![image](https://github.com/user-attachments/assets/cd60101c-302c-4c1b-a235-2b9f976cca7d)

## Add user-1 to the S3-Support group
You recently hired user-1 into a role to provide support for Amazon S3. You want to add them to the S3-
Support group to inherit the necessary permissions in the attached AmazonS3ReadOnlyAccess policy.
20. In the left navigation pane, choose User groups.
21. Choose the S3-Support group name link.
22. In the Users tab, choose Add users .
23. Select user-1.
24. At the bottom of the screen, choose Add users.
Expected output: Users added to this group
In the Users tab, under the Users in this group section, the list should now include user-1.
## Add user-2 to the EC2-Support group.
You hired user-2 for a role to provide support for Amazon EC2.
25. Repeat the steps you used for user-1 to add user-2 to the EC2-Support group.
26. Confirm user-2 is part of the EC2-Support group.
## Add user-3 to the EC2-Admin group
You hired user-3 as your Amazon EC2 administrator.
27. Repeat the steps you used for user-1 to add user-3 to the EC2-Admin group.
28. Confirm user-3 is part of the EC2-Admin group.
## Review user and group assignments
29. In the left navigation pane, choose User groups.
Each Group should have a 1 in the Users column to denote the number of users in each group.
If you do not have a 1 beside each group, revisit the preceding instructions to ensure that each user belongs to a
group, as shown in the table in the Business Scenario section.
Congratulations! You have successfully explored and managed IAM users, groups, and policies.

## Task 2: Use the IAM sign-in URL
In this task, you test the permissions of each IAM user.
## Task 2.1: Locate and access the IAM sign-in URL
30. In the left navigation pane, choose Dashboard.
In the AWS Account section, on right side of the dashboard, locate the Sign-in URL for IAM users in this
account URL. The URL format appears as follows:
https://123456789012.signin.aws.amazon.com/console
31. Use this link to sign in to the AWS account you are currently using.
32. Copy the IAM users sign-in link to a text editor.
You need this link to sign in later, testing each user.

## Task 2.2: Log in with different IAM users
33. In your browser, open a private window, as follows:
If you are using Firefox, do the following:
o In the upper-right corner, choose the Open application menu icon and choose New Private Window.
If you are using Chrome, do the following:
o In the upper-right corner, choose the Customize and Control Google Chrome ellipsis icon and choose New incognito window.
If you are using Edge, do the following:
o In the upper-right corner, choose the Settings and more ellipsis icon and choose New InPrivate window.
If you are using Internet Explorer, do the following:
o On the Tools menu, choose InPrivate Browsing.
34. Paste the IAM users sign-in link you copied earlier into the private window, and press Enter.
You will now sign in as user-1, your new Amazon S3 storage support person.
Sign in as user-1.

35. In the sign-in screen, use the following information:
● IAM user name:
user-1
● Password: Paste the value of UserPassword located to the left of these instructions.
● Press Enter.
36. At the top of the AWS Management Console, in the search bar, search for and choose S3.
37. From the S3 dashboard, choose the link for the bucket that has s3bucket in its name.
To the left of these instructions, you can also find the name of your S3 bucket. A bucket with awslabs-resources in
its name might also be present, along with an error. This is normal. You do not have access to this bucket.
Because your user is part of the S3-Support group in IAM, the user has permission to view a list of Amazon S3
buckets and the contents of the s3bucket.
Next, test whether user-1 has access to Amazon EC2.
38. At the top of the AWS Management Console, in the search bar, search for and choose EC2.
39. Locate your current region in the upper right side of the EC2 console. Verify this region is the same as
the Region value in the left side pane of these instructions. If not, navigate to the Region where your lab
launched, as follows:
● Choose the drop-down arrow at the top of the screen, to the left of user-1 drop-down in the top bar.
● Select the Region value that matches the value of Region to the left of these instructions.
40. In the left navigation pane, in the Instances section, choose Instances.
You should receive an error message: You are not authorized to perform this operation.
You cannot see any instances. This is because your user has not been assigned any permissions to use Amazon EC2.
Next, you sign in as user-2, your Amazon EC2 support person.
41. In the AWS Management Console, sign out user-1 by following these steps:
o At the top of the screen, choose user-1.
o Choose Sign out.
## Sign in as user-2
42. Paste the IAM users sign-in link (the one you copied to your text editor earlier) into your private window
and press Enter.
43. In the sign-in screen, use the following information:
o IAM user name:
user-2
o Password: Paste the value of UserPassword located to the left of these instructions
o Press Enter.
44. At the top of the AWS Management Console, in the search bar, search for and choose EC2.
45. Navigate to the Region where your lab launched (if you are not currently in that Region), as follows:
o Choose the drop-down arrow at the top of the screen, to the left of user-2 drop-down in the top bar.
o Select the Region value that matches the value of Region to the left of these instructions.
46. In the left navigation pane, in the Instances section, choose Instances.
You can view an Amazon EC2 instance because you have read-only permissions. However, you cannot make any
changes to Amazon EC2 resources. You should see a single running EC2 instance.
47. Make sure that the EC2 instance is selected, by choosing the checkbox beside the instance.
48. On the Instance state menu, choose Stop instance.
49. In the Stop instance? window, choose Stop.
Close the error message by clicking the X in the top of the red error window, on the right side.
Next, check to see if user-2 can access Amazon S3.
51. At the top of the AWS Management Console, in the search bar, search for and choose S3.
The S3 console should return an empty list of buckets because user-2 does not have permission to use Amazon S3.
Note that the Copy ARN, Empty, Delete, and Create options provide no access to those features.
Sign in as user-3
52. Sign in as user-3, your Amazon EC2 administrator.
53. In the AWS Management Console, sign out user-2, as follows:
o At the top of the screen, choose user-2.
o Choose Sign out.
54. Paste the IAM users sign-in link into your private window and press Enter.
55. Sign in with the following:
o IAM user name:
user-3
o Password: Paste the value of UserPassword located to the left of these instructions
o Press Enter.
56. At the top of the AWS Management Console, in the search bar, search for and choose
EC2.
57. Navigate to the Region where your lab launched (if you are not currently in that Region), as follows:
o Choose the drop-down arrow at the top of the screen, to the left of to the left of user-3 drop-down in
the top bar.
o Select the Region value that matches the value of Region to the left of these instructions.
58. In the left navigation pane, in the Instances section, choose Instances.
As an EC2 administrator, you should have permission to stop the Amazon EC2 instance.
59. Make sure that the EC2 instance is selected.
60. On the Instance state menu, choose Stop instance.
61. In the Stop instance? window, choose Stop .
The instance will enter the stopping state and shut down.
62. Close your private window.
successfully used the IAM sign-in URL, logged in with different users, and tested the access level of each user.

## Lab complete
● Explore IAM Users and Groups
● Inspect IAM policies applied to groups
● Follow a real-world scenario that adds users to groups and explores group permissions
● Locate and use the IAM sign-in URL
● Experiment with policies and service access

## End lab
Follow these steps to close the console and end your lab.
63. Return to the AWS Management Console.
64. At the upper-right corner of the page, choose AWSLabsUser, and then choose Sign out.
65. Choose End Lab and then confirm that you want to end your lab.

## Additional resources
● For more information about IAM , see AWS Identity and Access Management Documentation.
● For more information about AWS Training and Certification, see http://aws.amazon.com/training/.

## Result
IAM is a foundational aspect of security in cloud environments, helping control and monitor access to resources effectively. By following best practices and regularly auditing IAM configurations, organizations can maintain robust access control, protecting their digital assets from unauthorized access.
