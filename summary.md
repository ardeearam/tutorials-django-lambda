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
# Add generated domain to app/settings.py
# Add path('', include('app.urls')),  to app/urls.py
zappa update dev

#Optional: fancy domain name
zappa certify 
```


 