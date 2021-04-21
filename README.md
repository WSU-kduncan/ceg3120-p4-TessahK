# CEG3120 Project 4  
## Project overview  
This project focuses on containerizing our websites, setting up AWS CLI to create an ECR repository, and  
creating a Github workflow to push our image to ECR.  
### Run Project Locally  
Docker for desktop was installed from the official website. WSL2 is required which I already had installed before  
this download. The installation will also make sure Hyper-V windows features are enabled. Before I built the container  
I had to pick the correct image I wanted to use, in this case it was Apache2. To build the container, I had to create  
a Dockerfile. It must contain the correct image which is httpd:2.4. It must also specify that I am copying my html  
folder over to the one being used on the apache container. When the Dockerfile is complete the build command can be run The command I used was docker build -t apache-test. To run the container I built I ran the command docker run -d -p 5000:80 apache-test. To verify that the containerized website works I went to 127.0.0.1:5000.  
### Configure AWS CLI  
To install AWS CLI I had to use curl to download the zip file and save it to awscli2.zip. I then had to unzip the  
installer and install it with sudo ./aws/install. In order to authenticate with AWS I created a config and credentials  
file. The config file contains my AWS region and the type of output I would like from the console which is json.  
The credentials file is where I put the aws access key id as well as the secret access key.  
### Create ECR  
Now that the AWS CLI is properly configured I created my ECR repository. To do this I typed the command aws ecr  
create-repository --repository-name ceg3120/w078txk --region us-east-1  
### Configure Github Secrets  
After going to the repository for this project I went into settings. Here I could click on secrets which is where  
the access keys are stored. I created two secrets called AWS_ACCESS_KEY_ID and another called AWS_SECRET_ACCESS_KEY. Inside of these I pasted in each key.  
### Configure Github Workflow  
To create my workflow I started off with the sample template in the Project 4 repo. The only things I had to change  
were the AWS_REGION and ECR_REPOSITORY. I set these to us-east-1 and ceg3120/w078txk. I then pushed the file to Github. In my project repository I went to releases and created a new release to test the workflow. I named my release  
new release and gave it a version number of v1.0. Back in my actions section the workflow was triggered and was  
successful.

