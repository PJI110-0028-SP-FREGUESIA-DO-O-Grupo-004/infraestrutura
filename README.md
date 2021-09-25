# infraestrutura
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

Ao invés de instalar o aplicativo localmente, vamos utilizar o container oficial disponível [aqui](https://hub.docker.com/_/mysql)

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

O instalador pode ser contrado [aqui](https://dev.mysql.com/downloads/workbench/)
