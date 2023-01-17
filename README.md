# Consumir_arquivo_xlsx
Esse Sistema em Django ira consumir arquivos no formato xlsx, colocando planilhas no banco de dados pelo sistema.

# Agenda_clinica
Agenda de uma clinica medica feita em Django, Rest framework 

## Preparando o ambiente
Instale o python;
Instale um IDE - editor de código (vs code, pycharm, etc)
Você pode criar uma pasta normalmente: clicando no botão direito do mause e em seguida clicar em novo e pasta.
Porém você também pode criar pelo terminal usando o seguinte codigo:
```python
mkdir nome_pasta
```
Após isso, digite:
```python
cd cliente_api
```
Criando ambiente virtual para os pacotes do projeto
Essa parte pode ser criado dentro do terminal/ cmd do IDE
Linux:
```python
virtualenv venv
. venv/bin/activate
```
Windows:
```python
pip install virtualenv
python -m venv env
env\Scripts\activate
```
Instalando o Django e e Django REST framework no ambiente virtual:
```python
pip install django
pip install djangorestframework
pip install markdown       
pip install django-filter  
```
Criando o projeto e a aplicação:
```python
django-admin startproject core .  
django-admin startapp nome_do_app
```
Configurando o settings.py: 
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
    'nome_do_app',
]
```
Ainda no settings.py mudaremos o idioma para português:
```python
LANGUAGE_CODE = 'pt-br'
```
No arquivo clientes/models.py definimos todos os objetos chamados Modelos, tem que apagar tudo dele e escrever o seguinte código:
```python
from django.db import models



class Dados_existentes(models.Model):
    NIVEL = (
    ('F', 'F'),
    ('M', 'M'))

   # numero_usuario = models.CharField(max_length=90,null=True)
   # idU = models.CharField(max_length=150)
    nome = models.CharField('Nome Cadastrado:',max_length=100,null=True)
    sobrenome = models.CharField('Sobre Nome:',max_length=150, blank=True,null=True)
    sexo = models.CharField(max_length=1, choices=NIVEL, blank=False, null=False, default='M')
    altura = models.CharField(max_length=20,null=True)
    peso = models.CharField(max_length=20,null=True)
    nascimento= models.DateField(null=True)
    bairro = models.CharField(max_length=150,null=True)
    cidade = models.CharField(max_length=200,null=True)
    estado = models.CharField(max_length=200,null=True)
    numero = models.CharField('nome',max_length=30,null=True)

    def __str__(self):
        return self.nome
    objects = models.Manager()
```
Em seguida usaremos o comando makemigrations, pois ele analisa se foram feitas mudanças nos modelos e, em caso positivo, cria novas migrações ( Migrations ) para alterar a estrutura do seu banco de dados, refletindo as alterações feitas:
```python
python manage.py makemigrations nome_do_app
```
