# Deploying-a-Django-application-to-Elastic-Beanstalk
## Steps To Deploy Django App in AWS Elastic-Beanstalk

Prerequisites



Python 3.7 or later

pip

virtualenv

awsebcli (https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html)

AWS CLI (https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

*Set up a Python virtual environment* 

create one folder where you can create a project & virtual environment

cd Documents

mkdir AWS-elasticBeanstalk

now install the virtual enviornment in that folder

sudo apt install -y python3-venv
python3 -m venv myenv

Activate virtual environment.

source myenv/bin/activate

Notice that the prefix now included (myenv). This lets you know that the environment is active.

![Capture](https://user-images.githubusercontent.com/23288656/183277219-52640b42-52db-42d7-849c-2fa180ed9c75.PNG)


Now install Django

pip install django==4.0.6 

To verify that Django is installed, enter the following.
pip freeze
Django==4.0.6
	
now switch over to VS-Code & activate your virtual env
	
Create a Django project in your virtual envirionment

django-admin startproject ebdjango

This command creates a standard Django site named ebdjango with the following directory structure.

![cap-2](https://user-images.githubusercontent.com/23288656/183277346-cea36e2f-0670-4308-bfa6-84b13b2e9f01.PNG)



Run your Django site locally with manage.py runserver

cd ebdjango

python3 manage.py runserver

In a web browser, open http://127.0.0.1:8000/ to view the site


![Capture-8000](https://user-images.githubusercontent.com/23288656/183277130-e78cb34f-f8d7-47c7-bd1f-3d3976017f8b.PNG)


## Configure your Django application for Elastic Beanstalk

Activate your virtual environment in VS Code project workspace terminal 
enter command to see all your required dependancy installed or not

pip freeze > requirements.txt

Next Create a directory named .ebextensions

mkdir .ebextensions

In the .ebextensions directory, add a configuration file named django.config with the following text.


![Screenshot from 2022-08-06 23-31-48](https://user-images.githubusercontent.com/23288656/183279554-f5eafe89-ed8d-4abf-bc7e-fc7203cfb471.png)

    
  ## You've added everything you need to deploy your application on Elastic Beanstalk. Your project directory should now look like this

![Screenshot from 2022-08-06 23-34-46](https://user-images.githubusercontent.com/23288656/183277441-272458a6-0149-4417-87f9-b3a2bcb9ddee.png)

# Note- We didn't create git repo yet so do not worry if .gitignore not in your project folder

Now before AWS configure we need to create an access keys so for that switch over to IAM service in AWS console and follow below steps to create an access keys

IAM--> Users---> Existing User---->Security Credentials--> Create Access Keys
---> copy both your access keys & save it in your local PC

enter below command in your terminal

 aws configure
 
AWS Access Key ID [None]: ENTER_YOUR_ACCESS_KEY_ID

AWS Secret Access Key [None]:ENTER_YOUR_SECRET_ACCESS_KEY

Default region name [None]: ENTER_YOUR_DEFAULT_REGION

Default output format [None]: json

## Create an environment and deploy your Django application
 Initialize your EB CLI repository with the eb init command.
 
 eb init -p python-3.8 django-app

 eb create django-env

 eb status

![Screenshot from 2022-08-06 23-52-02](https://user-images.githubusercontent.com/23288656/183278253-80aa91ff-bf66-4996-b59b-141bcdbb0179.png)


Open the settings.py file in the ebdjango directory. Locate the ALLOWED_HOSTS setting, and then 
add your application's cname value save the file, and then deploy your application by running below commands

eb deploy

eb open

If you do see your application running, then congratulations, you've deployed your first Django application with Elastic Beanstalk!

![Screenshot from 2022-08-06 23-54-17](https://user-images.githubusercontent.com/23288656/183276990-6f8eb85e-5c97-4a30-a56d-3dd4f0d935a0.png)

## Now Switch over to AWS console and open AWS Elastic Beanstock Service you can see app's Environment , Health , URL etc


![new](https://user-images.githubusercontent.com/23288656/183279236-7c97f437-20b9-4cff-afda-17cd03744842.PNG)


![Capture-eb](https://user-images.githubusercontent.com/23288656/183279163-276a7a3e-d75a-4f36-89d0-41e987cf9a6a.PNG)


## Links to know more about this deployment

https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-django.html

Youtube Link

https://youtu.be/lid-aICtbCI

## *Note--- Feel free to make changes I will merge your commit into main if any deployment steps missing in this Readme.md*

Thanks & Regards

Happy Learning :blush: :+1:









































	


