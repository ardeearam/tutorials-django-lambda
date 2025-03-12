```
mkdir tutorial-django-lambda
cd tutorial-django-lambda
python3 -m venv venv
source venv/bin/activate

pip install django
pip freeze > requirements.txt

django-admin startproject app
cd app
python manage.py runserver  #Visit http://127.0.0.1:8000/

pip install --upgrade setuptools
pip install zappa
pip freeze > ../requirements.txt

zappa init

aws configure sso

zappa deploy dev   

#Code modifications:
# app/settings.py 
#  - Add generated domain to ALLOWED_HOSTS
#  - Add 'app' to INSTALLED_APPS
# app/views.py - Create
# Add path('', include('app.urls')),  to app/urls.py
# Add app/templates/app/home.html for added oomph. Update app/views.py accordingly

zappa update dev

#Optional: fancy domain name
#Prerequisites - you have a public Route53 hosted zone
# zappa_settings.json 
# - Add "domain" entry
# - Add "certificate_arn" entry - See AWS Certificate Manager to get the CRN
zappa certify

# app/settings - Add domain to ALLOWED_HOSTS. 
zappa update dev    #deploy the change in ALLOWED_HOSTS
```


 