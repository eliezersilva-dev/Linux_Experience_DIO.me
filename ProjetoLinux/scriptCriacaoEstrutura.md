## Descrição do Projeto

✔️ Neste projeto criaremos um script onde toda a infraestrutura de usuários, grupos de usuários, diretórios e permissões serão criadas automaticamente. Será realizado o upload do arquivo de script no GitHub para futuras reutilizações do script. Sendo assim, toda nova máquina virtual que for iniciada já estará pronta para uso quando o script for executado.

✔️ Definições:
- Excluir diretórios, arquivos, grupos e usuários criados anteriormente;
- Todo provisionamento deve ser feito em um arquivo do tipo Bash
Script;
- O dono de todos os diretórios criados será o usuário root;
- Todos os usuários terão permissão total dentro do diretório publico;
- Os usuários de cada grupo terão permissão total dentro de seu
respectivo diretório;
- Os usuários não poderão ter permissão de leitura, escrita e execução em diretórios de departamentos que eles não pertencem;
- Subir arquivo de script criado para a sua conta no GitHub.

📌 Diretórios:
- /publica
- /adm
- /ven
- /sec

📌 Grupos
- GRP_ADM
- GRP_VEN
- GRP_SEC

📌 Usuários/Grupos

| GRP_ADM | GRP_VEN | GRP_SEC |
|---------|---------|---------|
| carlos  | debora  | josefina |
| maria   | sebastiana | amanda |
| joao    | roberto |  rogerio |

🌟 Script:


sudo su -> entrar em modo super usuário

### - Excluir diretórios pertinentes
**cd /** -> navegar até raiz

**ls** -> listar diretórios e arquivos

**rm -Rf** -> excluir Recursivo Force - excluir diretórios pertinentes - no presente caso excluir adm, vend, sec e public

### - Excluir usuários e seus respectivos diretórios
**cat /etc/passwd** -> lista os usuários

**userdel -r 'nome'** -> excluir usuário mais seu diretório (-r), ex: userdel -r maria 

### - Excluir grupos
**cat /etc/group** -> consultar grupos

**groupdel 'nome'** -> excluir grupo, ex: groupdel GRP_ADM 

### - Após preparar o ambiente, criar o Script
**cd /script** -> acessar o diretório de Scripts 

**nano teste.sh** -> criar um arquivo de texto (nesse caso usando nano), o nome do texto deve conter a extensão 'sh'

### - O Script será escrito no documento de texto (nesse caso teste.sh)
**#!/bin/bash** -> espcificar que se trata de um arquivo bash

### - Criando os diretórios
**echo "Criando diretórios..."** -> echo imprime na tela o conteúdo entre aspas

**mkdir /publica**

**mkdir /adm**

**mkdir /ven**

**mkdir /sec**

### - Criando os grupos
**echo "Criando grupos de usuários..."**

**groupadd GRP_ADM**

**groupadd GRP_VEN**

**groupadd GRP_SEC**

#### - Criando os usuários
**echo "Criando usuários..."**

**useradd carlos -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_ADM** -> criando usuário, nome carlos, -m cria a pasta do usuário, -s cria um scrip no /bash, -p configura o password, -"nome grupo" especifica o grupo (é também possível especificar o grupo usando o comando usermod)

**useradd maria -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_ADM**

**useradd carlos -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_ADM**

**useradd debora -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_VEN**

**useradd sebastiao -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_VEN**

**useradd roberto -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_VEN**

**useradd josefina -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_SEC**

**useradd amanda -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_SEC**

**useradd rogerio -m -s /bin/bash -p $(openssl passwd - crypt senha123) -GRP_SEC**

### - Especificando permissões dos diretórios
**echo "Especificando permissões dos diretórios..."**

**chown root:GRP_ADM /adm** -> especificando root como dono do grupo e direcionando o grupo para o ser diretório específico

**chown root:GRP_VEN /ven**

**chown root:GRP_SEC /sec**

**chmod 770 /adm** -> definindo permissões pelo modelo 777 - root=7, usuário do diretório=7, demais usuário=0

**chmod 770 /ven**

**chmod 770 /sec**

**chmod 777 /publica**

**echo "Fim do script."**

**ctrl + o -> salvar**

**crtl + x -> sair**

### - Executando o Script
**ls -l** -> listar arquivos e diretórios, -l exibe detalhes

**chmod +x teste.sh** -> dando permissão do root para o execução do Script

**./teste.sh** -> executando o  Script

### - Checagem do resultado
**cat /etc/passwd** -> checar usuários

**cat /etc/group** -> checar grupos

**ls -l** -> checar permissões dos diretórios










