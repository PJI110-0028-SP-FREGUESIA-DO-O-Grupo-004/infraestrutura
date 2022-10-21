# Infraestrutura
Esse repositório contém os scripts e configurações do ambiente que vamos usar no projeto.

# Software para ser instalado

## Anaconda

Anaconda é uma distribuíção python para Linux, Mac e Windows. A grande vantagem é a uniformização dos pacotes em diversas plataformas e a possibilidade de exportar o arquivo de configuração do ambiente pra replicar entre os integrantes do grupo.

O instalador atual para windows pode ser encontrado [aqui](https://repo.anaconda.com/archive/Anaconda3-2021.05-Windows-x86_64.exe).

## Docker

Docker é uma ferramenta que permite a execução de containers no seu computador. Cada container é um ambiente inteiro funcional, usado para empacotar tudo o que uma aplicação precisa prar executar.

Vamos rodar o MySQL localmente pelo docker, assim não precisamos nos preocupar com a instalação do banco, basta usar o container oficial do MySQL.

Instruções de instalação podem ser encontradas [aqui](https://docs.docker.com/desktop/windows/install/).

## MySQL

MySQL é o banco de dados que vamos utilizar.

Ao invés de instalar o aplicativo localmente, vamos utilizar o container oficial. A documentação detalhada pode ser encontrada [aqui](https://hub.docker.com/_/mysql), mas por agora é só seguir pro próximo passo.

Depois de instalado o docker iniciar pela primeira vez um servidor local é fácil, basta abrir o CMD e digitar:

```
docker run -p 3306:3306 --name servidor-mysql -e MYSQL_ROOT_PASSWORD=senha -d mysql:latest
```

Esse comando vai baixar a imagem do container da versão mais nova do MySQL, essa instancia vai ter o usuário root com a senha "senha" e vai mapear a porta 3306 do container para o seu windows, assim vocë poderá conectar na instancia do banco pelo MySQL Workbench.

Para iniciar o container em um outro dia ou depois de uma reinicialização do windows basta abrir o CMD e digitar:

```
docker start servidor-mysql
``` 

## MySQL Workbench

MySQL Workbench é uma IDE para manipular o banco de dados.

O instalador pode ser contrado [aqui](https://dev.mysql.com/downloads/workbench/).

Para se conectar no container local do MySQL use as seguintes configurações:

host: 127.0.0.1
username: root
password: senha

Conecte no MySQL e crie um banco de dados vazio com o seguinte comando SQL:

```
create database pi;
```

## VSCode

VSCode é a IDE que utilizaremos para editar os códigos.

O instalador para Windows pode ser encontrado [aqui](https://code.visualstudio.com/docs/?dv=win).

Na primeira execução o VSCode vai mostrar uma notificação perguntando se você quer instalar o pacote de tradução para o português, eu não recomendo.

O VSCode pode também mostrar uma notificação pedindo para instalar o Python da Microsoft, não precisamos disso pois estamos usando o Anaconda.

Depois de instalado adicione a extenção Python, que pode ser baixada [aqui](https://marketplace.visualstudio.com/items?itemName=ms-python.python).

É interessante também instalar a extenção GitLens, pra usar o Git de dentro do VSCode, ela pode ser baixada [aqui](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens).

## Git

Git é uma ferramenta para controle de versão, ele é inslado quando você criar o ambiente anaconda nos próximos passos :) .

# Criando o ambiente Anaconda

Com o tudo instalado podemos seguir para a criação do ambiente python onde vamos trabalhar.

Baixe o arquivo spec-file.txt deste repositório e execute o seguinte comando no Anaconda Prompt:

```
conda create --name pi --file spec-file.txt
```

Para acessar o ambiente depois, você digita no CMD:

```
conda activate pi
```

Por ultimo, mas não menos importante, precisamos instalar dois pacotes que só funciona via pip:
```
pip install flask_sqlalchemy
pip install mysqlclient
```


Pronto :)
