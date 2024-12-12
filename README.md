# Monitoramento Automatizado do nginx no Ubuntu 20.04 LTS

## Sobre o projeto

A prática consiste na instalação do WSL (Subsistema do Windows para Linux) no Windows e na criação de uma instância Ubuntu 20.04 LTS. Inclui também a configuração de um servidor nginx, o monitoramento do status do serviço por meio de um script personalizado e a automação da execução deste script a cada 5 minutos. O script deve conter a data, hora, o nome do serviço, o status e uma mensagem personalizada de ONLINE ou OFFLINE. O objetivo é garantir a continuidade e a disponibilidade do serviço, registrando seu status em arquivos separados.

### Índice

1. [Pré-requisitos](#1-pré-requisitos)
2. [Ativação e configuração do WSL](#2-ativação-e-configuração-do-wsl)
3. [Instalação e Configuração do Ubuntu 20.04 LTS](#3-instalação-e-configuração-do-ubuntu-2004-lts)
4. [Instalação e configuração do nginx no Ubuntu](#instalação-e-configuração-do-nginx-no-ubuntu)
5. [Configuração dos arquivos de log](#configuração-dos-arquivos-de-log)
6. [Criação do script de monitoramento do status do nginx](#criação-do-script-de-monitoramento-do-status-do-nginx)
7. [Automatização da execução do script](#automatização-da-execução-do-script)

## 1. Pré-requisitos

- Windows 10 versão 2004 e superior ou Windows 11
- Ativação do WSL
- Ubuntu 20.04 LTS instalado no WSL
- Conhecimeto básico do terminal Linux

## 2. Ativação e configuração do WSL

Clique com o botão direito do mouse sobre o PowerShell ou o Prompt de Comando do Windows e selecione **"Executar como administrador"**.

Depois, execute o comando:

```powershell
wsl --install
```

Após executado o comando e terminado a instalação do WSL, reinicie o computador.

## 3. Instalação e Configuração do Ubuntu 20.04 LTS

Abra o PowerShell como administrador e execute o comando:

```powershell
wsl --install -d Ubuntu-20.04
```

Alternativamente, você pode abrir a Microsoft Store, buscar por "Ubuntu 20.04 LTS", clicar em adquirir e instalar a distribuição.

Terminado o processo de instalação do Ubuntu no WSL, você será solicitado a criar um nome de usuário e senha. Esta conta será o **usuário padrão e administrador da distribuição**, com permissões para executar comandos de super usuário (`sudo`).

## Instalação e configuração do nginx no Ubuntu

Abra o terminal do Ubuntu e execute o seguinte comando para garantir a instalação do pacote correto e sua versão mais recente:

```bash
sudo apt update
```

Após isso, instale o nginx:

```bash
sudo apt install nginx
```

Inicie e verifique o status do nginx:

```bash
sudo systemctl start nginx
```

```bash
sudo systemctl status nginx
```

Caso o nginx esteja rodando corretamente, o comando retornará uma saída como esta:

![Status do nginx Ativo](imgs/nginx_status.jpeg)

Você pode verificar se o nginx está funcional acessando a página padrão pelo navegador, por meio do IP ou digitando "localhost" na barra de endereços:

![Página Padrão do nginx](imgs/nginx_via_localhost.jpeg)

## Configuração dos arquivos de log

Antes de configurar o monitoramento, é necessário criar os arquivos de log para armazenar o status do serviço nginx. Execute os seguintes comandos para criar os arquivos de log:

```bash
sudo touch /var/log/nginx/nginx_online.log
```

```bash
sudo touch /var/log/nginx/nginx_offline.log
```

Para garantir que o script tenha permissão para escrever nestes arquivos, ajuste as permissões:

```bash
sudo chmod 664 /var/log/nginx/nginx_online.log /var/log/nginx/nginx_offline.log
```

Nesta configuração, apenas o proprietário e o grupo poderão ler e escrever nos arquivos, e outros usuários poderão somente lê-los.

Além disto, a pasta onde os arquivos de log estão armazenados deve ter as permissões configuradas de modo que o nginx possa modificar arquivos de log. Execute o seguinte comando para garantir que o nginx possa acessar a pasta e modificar arquivos:

```bash
sudo chmod 755 /var/log/nginx
```

## Criação do script de monitoramento do status do nginx

Primeiramente, crie um diretório dentro do seu diretório pessoal onde o script será armazenado. Para isso, execute o seguinte comando:

```bash
mkdir ~/scripts
```

Após isso, utilize um editor de texto para criar e editar o script. Utilizando o editor de texto `nano`:

```bash
nano ~/scripts/status_nginx.sh
```

## Automatização da execução do script

## Referências

- [Documentação do WSL](https://docs.microsoft.com/en-us/windows/wsl/)
- [Documentação do nginx](https://nginx.org/en/docs/)
