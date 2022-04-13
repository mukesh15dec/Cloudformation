# CloudFromation Training - 

# Below CLI commands are used to create/update/delete CF stack. You can also do using AWS Console howveer, I would highly recommed to use CLI. USING this way only you can create your CI/CD Pipeline.  

#aws cloudformation create-stack --stack-name Iamuser --region us-east-1 --capabilities CAPABILITY_NAMED_IAM --template-body file://"Iam_user.yml"
#aws cloudformation delete-stack --stack-name Iamuser
#aws cloudformation update-stack --stack-name Iamuser --capabilities CAPABILITY_NAMED_IAM --template-body file://"Iam_user.yml"
#aws cloudformation validate-template --template-body file://New_Bucket.yml   - To validate 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# IAM LAB  : In this LAB, you will :
    * you will create an IAM user, a new group, attach group to created user.
    * you will attach managed "ReadOnly" Policy to the user. you can do alos for group but not covered in this template. 
    * In the last, you will create Tag for user.

# Homework :
    * Update template to create access key & secret key
    * update template to create user password << Note - don't keep password in your template >>
  
# File Name :         Iam_user.yml   
                  
--------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------

# S3 LAB 
The AWS::S3::Bucket resource creates an Amazon S3 bucket in the same AWS Region where you create the AWS CloudFormation stack.
To control how AWS CloudFormation handles the bucket when the stack is deleted, you can set a deletion policy for your bucket. You can choose to retain the bucket or to delete the bucket.
 - Delete stack and check bucket - Bucket will not be deleted as **DeletionPolicy: Retain**

  #S3_Bucket.yml
    * Create a new S3 Bucket called "noram2lab-dev" , look for Tag & value to find stack set information 
    * delete stack and check Bucket, bucket will not be deleted
    * Remove **DeletionPolicy: Retain**  properties and re-do same work . In this time Bucket will be deleted. 

 #S3_Bucket_4_webHosting.yml:    Creating an Amazon S3 bucket for website hosting and with a DeletionPolicy
    This Template creates a bucket as a website. The AccessControl property is set to the canned ACL PublicRead (public read permissions are required for buckets set up for website hosting). Because this bucket resource has a DeletionPolicy attribute set to Retain, AWS CloudFormation will not delete this bucket when it deletes the stack. The Output section uses **Fn::GetAtt:** to retrieve the WebsiteURL attribute and DomainName attribute of the S3Bucket resource.

  - A new bucket with default name will be created since you have not mentioned Bucket Name 
  - Public accessable bucket 
  - Fn::GetAtt in the output 
  - uses **!Join:**

# Instance Scheduler LAB 