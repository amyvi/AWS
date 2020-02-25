# Creating a simple auto-scaling group using AWS Console

For this example, I have create my own AMI image in order to use in my auto-scaling group.

1. Go to - EC2 -> Auto Scaling group
2. Click on Create Auto Scaling Group
3. Click on Create Launch Configuration
4. Select AMI - Instance Type - Configuration Details 
Name:
IAM Role: 
5. Add Storage - Security Group - Preview - Create Launch Configuration
6. Proceed without a key pair (since my iamrole and instance is set for SSM)

Create Auto Scaling Group
1. Create name
2. Add subnet
3. Select desired capacity, min and max
3. The rest are defaults 
4. Then create

Once created, aws will instantly create the number of desired instance you have stated in the Auto Scaling Group.
- Just click on refresh button to see the new instance
- Or you can navigate on the instances tab to check
- Once you have terminated the instance and the condition does not satisfy the number of instance, aws will autoscale on the desired capacity.

If you decide to delete the ASG, the instance corresponding to the ASG will automatically be deleted.
