# Infraestutura como código: 
## Script de provisionamento de um servidor web (Apache)

📌Este script será para automatizar o provisionado de um servidor web. Um servidor web é um software e hardware que usa HTTP (Hypertext Transfer Protocol) e outros protocolos para responder a solicitações de clientes feitas pela World Wide Web. O principal trabalho de um servidor da web é exibir o conteúdo do site por meio do armazenamento, processamento e entrega de páginas da web aos usuários.

✔️Comandos:

Criar uma pasta de script e dentro dela criar um arquivo txt para editar o script

mkdir script2

cd /script2/

nano script-iac.sh

✔️Script:

**#!/bin/bash**

echo "Atualizando o servidor..."

apt-get update

apt-get upgrade -y

apt-get install apache2 -y

apt-get install unzip -y


echo "Baixando e copiando os arquivos da aplicação..."

cd /tmp

wget https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip -> aplicação(site) que será executado no servidor

unzip main.zip

cd linux-site-dio-main

cp -R * /var/www/html/

✔️Comando:

Concedendo permissão de execução

chmod +x sript-iac.sh
