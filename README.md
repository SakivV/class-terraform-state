# Terraform State
 - Terraform requires some sort of database to map Terraform config to the real world. For example, when you have a resource resource "aws_instance" "foo" in your configuration, Terraform uses this mapping to know that the resource resource "aws_instance" "foo" represents a real world object with the instance ID i-abcd1234 on a remote system.
 - For mapping configuration to resources in the real world, Terraform uses its own state structure.
 - Terraform state can :
   - Local : On your on Machine
   - Remote : Store centrally e.g. S3 so that all team members can access it.
 - Terraform State commands:
   - terraform list
   - terraform show
   - terraform refresh
   - terraform plan (internally calls refresh)
   - terraform state
   - terraform force-unlock
   - terraform taint
   - terraform untaint
   - terraform apply target command

# Instructions
We will do practice on various Terraform state scenario. For these scenario, you need to create S3 bucket and DynamoDB table(table name can be anything) but partition_key name should *LockID*.
### Scenario 1 : Implement Backend without DynamoDB table.
1. In ```version.tf``` file , comment DynamoDB table and have only S3 bucket. Please note that you need to change bucket name as per bucket you created.
2. Clone this repo in separate folders on your machine. For example, Developer-A and Developer-B are performing actions. 
3. Try creating 2 EC2 instance , for example Developer-A create these instances.
4. Now imagine, business asks for number of EC2 instance should be 4. And now try performing this action from both folder like Developer-A and Developer-B performing same actions,making EC2 instance count to 4.
5. Observe the action performed on AWS Console. Expected output should have 6 EC2 instances which is not as per business requirement.
6. Clean your infrastructer with terraform destroy

### Scenario 2 : Implement Backend with DynamoDB table.
1. In ```version.tf``` file , uncomment DynamoDB table and have only S3 bucket. Please note that you need to change bucket name as per bucket you created.
2. Now repeate above scenario.
3. Either Developer-A or Developer-B will not able to perform operation if either of them performing operation. This is called Terraform State locking. This is useful in when we work in teams.

