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
- Change bucket name and Dynamodb table name in ```version.tf``` file as per the bucket name and DynamoDB table created by you.
