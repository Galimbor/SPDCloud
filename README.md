# SPD Cloud


## AWS

1. Primeiro devemos criar conta na plataforma, seguindo os seguintes passos:
- https://docs.aws.amazon.com/cloud9/latest/user-guide/setup-student.html
Vá para o site de login do AWS Educate, em https://www.awseducate.com/signin/.

Insira o endereço de e-mail e a senha que você usou para fazer login no Portal de aluno do AWS Educate e escolha Sign In (Fazer login).

Selecione Conta da AWS no banner de navegação superior.

Selecione Conta do AWS Educate Starter

2. Seguir tutorial 
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-django.html
- Criar ambiente virtual 
```virtualenv eb-virt```
- Ativar ambiente virtual
``` eb-virt\Scripts\activate```
- Instalar django
```pip install django```
- Verificar se django ficou corretamete instalado
```pip freeze```

## Criar projeto no django
1. Verificar que o ambiente virtual está ativado
2. Criar projeto, neste caso demos o nome de *SPDCloud*
```django-admin startproject SPDCloud```
3. Entrar na pasta e correr o servidor local
```python manage.py runserver```
4. Terminar servidor ```Ctrl+C```

# Configure your Django application for Elastic Beanstalk
## To configure your site for Elastic Beanstalk
1. Verificar que o ambiente virtual está ativado
2. Guardar as aplicações que estão instaladas no ambiente virtual num ficheiro *requirements.txt* para ser instaladas mais tarde no servidor
```pip freeze > requirements.txt```
3. Criar diretoria onde serão guardados os Scripts para configuração do servidor
```mkdir .ebextensions```
4. Criar ficheiro na diretoria ```~/SPDCloud/.ebextensions/django.config``` com o seguinte informação: (**Atenção:** O *WSGIPath* deverá estar correto)
```
option_settings:
  aws:elasticbeanstalk:container:python:
    WSGIPath: SPDCloud.wsgi:application
```
5. Desativar o ambiente virtual
```deactivate```


# Deploy your site with the EB CLI
1. To create an environment and deploy your Django application
```eb init ``
- Escolher regiao onde o servidor estará hospedado. No nosso caso escolhemos 16 *16) eu-west-2 : EU (London)*, por ser mais próximo de nós.
- Obter as credenciais de acesso. Aceder a *IAM* -> Users -> AddUser 
(aws-access-id)
- 
2. Criar um ambiente, neste caso criamos um ambiente de produção
```eb create SPDCloud-Production```
3. Verificar o estado do ambiente criado
```eb status``` ou ```eb open```
4. Caso tenhamos feito alguma atualização do código, devemos fazer **deploy**
```eb deploy```

```eb ssh``` conexão ao servidor

***SITE**: http://spdcloud-production.eba-mbmntigr.eu-west-2.elasticbeanstalk.com/


##  Azure
https://docs.microsoft.com/pt-pt/azure/app-service/tutorial-python-postgresql-app?tabs=bash%2Cclone
https://docs.microsoft.com/pt-pt/azure/app-service/quickstart-python?tabs=bash&pivots=python-framework-django
### Requirements
- Tenha uma conta Azure com uma subscrição ativa. Crie uma conta gratuita.
- Instale python 3.6 ou superior. ```py -3 --version```
- Instale o Azure CLI 2.18.0 ou superior, com o qual execute comandos em qualquer concha para provisões e configurar recursos Azure. ```az --version ``` e depois fazer login ```az login```
- Deploy para servidor, no nossa fizemos para spdcloud como app-name
```az webapp up --sku B1 --name <app-name>```
- Abrir a app
```http://<app-name>.azurewebsites.net```

***SITE**: http://spdcloud.azurewebsites.net/

> ## Google Cloud Platform

***SITE**: https://spd-multi-cloud-onboard-p2.ew.r.appspot.com/

