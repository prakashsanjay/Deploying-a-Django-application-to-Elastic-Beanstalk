# Deploying-a-Django-application-to-Elastic-Beanstalk
Deploy Django App in AWS Elastic-Beanstalk

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

Now install Django

pip install django==4.0.6 

To verify that Django is installed, enter the following.
pip freeze
Django==4.0.6
	
now switch over to VS-Code 
now activate your virtual env
	
Create a Django project in your virtual envirionment

django-admin startproject ebdjango

Run your Django site locally with manage.py runserver

cd ebdjango
python3 manage.py runserver
In a web browser, open http://127.0.0.1:8000/ to view the site

Configure your Django application for Elastic Beanstalk

Activate your virtual environment.

pip freeze > requirements.txt

Create a directory named .ebextensions

mkdir .ebextensions

In the .ebextensions directory, add a configuration file named django.config with the following text.

option_settings:
  aws:elasticbeanstalk:container:python:
    WSGIPath: ebdjango.wsgi:application
    
    Deactivate your virtual environment with the deactivate command.
    deactivate
    
    Deploy your site with the EB CLI
    
    You've added everything you need to deploy your application on Elastic Beanstalk. Your project directory should now look like this.
    
    To create an environment and deploy your Django application
    Initialize your EB CLI repository with the eb init command.
    eb init -p python-3.8 django-app
    
   aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-2
Default output format [None]: json

eb create django-env
eb status

Open the settings.py file in the ebdjango directory. Locate the ALLOWED_HOSTS setting, and then 
add your application's domain name that you found in the previous step to the setting's value.

ave the file, and then deploy your application by running eb deploy.
eb deploy
eb open

If you do see your application running, then congratulations, you've deployed your first Django application with Elastic Beanstalk!






































	


