"# SPDCloud" 
# AWS

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
