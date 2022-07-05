# DSO-ECS
Security DevSecOps pipeline with ECS Fargate

Clone the repository.
Create a bucket in the region you are deploying to use as the source code bucket.
Upload files in the environment directory directly to the new bucket.
Create a folder in the bucket called devsecops and upload anchore-build.zip and initial-commit.zip to devsecops.
Create a folder in the bucket called layers inside the devsecops folder and upload boto3.zip from the layers directory to that folder.

Create a stack using the container-devsecops-demo.yml template and use the bucketname of the bucket you just created as the DevSecOpsResourcesBucket Parameter.

Once everything has created then you will need to upload the app to the app repository created in codecommit.
Clone the codecommit repository "container-security-demo-app" to your local machine or cloud9 depending on what you want to use.
Make sure you are on branch development.
Copy across the contents of the application folder to the local development branch.
Commit the new files and push to development.
Create a pull request like:

aws --region eu-west-1 codecommit create-pull-request \
--title "Uploading new application" \
--description "Please Review" \
--targets repositoryName=container-security-demo-app,sourceReference=development,destinationReference=master

