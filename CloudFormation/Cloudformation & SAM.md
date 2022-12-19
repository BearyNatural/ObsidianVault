run by Jain, Akhil

https://drive.corp.amazon.com/folders/aws-support-training/premium-support-content/Live%20Learning%20Lab%20Material

download CLI for SAM from above link

go into isengard account

code-star - can use
cloud 9
- create environment
	- name serverless-demo-workshop
	- ec2 instance, linux, t2
- opens up what appears to be visual studio for the respository;
	- [use the terminal to interact with SAM enviorment]
		- sam --version
		- sam init
		- 1, 1, N, 11, 1, 1, N, ap1demo
	- for further clarification on the code see AWS SAM white papers 
	- ls
	- cd apiDemo/
	- sam build
	- sam deploy --guided
		- apidemo, enter, Y , enter, enter, Y, enter, enter, enter
		- build starts
		- Y
		- once deployed grab the helloworld output value for the webpage
		- go to lambda function hello world go have a look at the code and the cloud watch logs tif somethign goes wrong
		- open cloudformation service
			- check out the apidemo template
		- back to cloud9 and in the app.js file change hello world to hello {name} - save 
		- sam build
		- sam deploy - Y
		- check the output page again
		- sam sync --stack-name apidemo --watch - Y
		- ^C to stop sync
		- ls
		- mc template.yaml template.yaml.old
		- copy new yaml into the template spot
		- sam build
		- sam deploy
		- go back to console & refresh and check cloud formation
		- duplicate the app.js file copy new content into old file
			- in new app.js file
			- open package .json
			- at end of line 10 create new line
			- insert "uuid": "^8.3.2" - this line made the build fail
		- and sam deploy failed to deploy the dynamoDB and therefore caused an internal so now the site isn't working :( so sad)
		- sam pipeline init --bootstrap
			- 1, 5, 2, sam-app, e, e, 1, sam-app-dev-stack, 2, sam-app-repo
		- aws codecommit create-repository --repository-name sam-app-repo
		- check cloudformation for progress
		- git config --global [with the output not the http]
		- git config --global user.name 'adf'
		- git config --global user.email 'adf@email.com'
		- create new file under sam-workshop .gitignore - it'll say it already exists
		- at the bottom of the file
			- .aws-sam/build
		- git init -b main 
		- git add . 
		- git commit -m "Initial commit"
		- git status
		- git branch
		- git remote add origin [with cloneurl from the repo]
		- git push -u origin main
	- sam deploy -t codepipeline.yaml --stack-name api-pipeline-stack --capabilities=CAPABILITY_IAM
	- in app.js
		- add from code pipeline
	- git add . 
	- git commit -m "function change" 
	- git push
	- check code pipeline


![[Pasted image 20221216110444.png]]
Template functions

![[Pasted image 20221216110634.png]]
Functin Join i.e. bootstrap script for ec2 instance