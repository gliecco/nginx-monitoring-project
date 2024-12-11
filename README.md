# Automação no Linux para monitoramento de um servidor Nginx

## Sobre o projeto
A prática consiste na instalação do WSL (Subsistema do Windows para Linux) no Windows e na criação de uma instância Ubuntu 20.04 LTS. Inclui também a configuração de um servidor Nginx, o monitoramento do status do serviço por meio de um script personalizado e a automação da execução deste script a cada 5 minutos. O script deve conter a data, hora, o nome do serviço, o status e uma mensagem personalizada de ONLINE ou OFFLINE. O objetivo é garantir a continuidade e a disponibilidade do serviço, registrando seu status em arquivos separados.

### *Índice*
1. [Pré-requisitos](#1-pré-requisitos)
2. [Ativação e configuração do WSL](#2-ativação-e-configuração-do-wsl)
3. [Instalação e Configuração do Ubuntu 20.04 LTS](#3-instalação-e-configuração-do-ubuntu-2004-lts)
4. [Instalação e configuração do Nginx no Ubuntu](#instalação-e-configuração-do-nginx-no-ubuntu)
5. [Configuração dos arquivos de log](#configuração-dos-arquivos-de-log)
6. [Criação do script de monitoramento do status do serviço Nginx](#criação-do-script-de-monitoramento-do-status-do-serviço-nginx)
7. [Automatização da execução do script](#automatização-da-execução-do-script)

## 1. Pré-requisitos
- Windows 10 versão 2004 e superior ou Windows 11
- Ativação do WSL
- Ubuntu 20.04 LTS instalado no WSL 
- Conhecimeto básico do terminal Linux

## 2. Ativação e configuração do WSL
Clique com o botão direito do mouse sobre o PowerShell ou o Prompt de Comando do Windows e selecione **"Executar como administrador"**. 

Depois, execute o comando:

```
wsl --install
```
Após executado o comando e terminado a instalação do WSL, reinicie o computador.
## 3. Instalação e Configuração do Ubuntu 20.04 LTS
Abra o PowerShell como administrador e execute o comando:

```
wsl --install -d Ubuntu-20.04
```

Alternativamente, você pode abrir a Microsoft Store, buscar por "Ubuntu 20.04 LTS", clicar em adquirir e instalar a distribuição.

Terminado o processo de instalação do Ubuntu no WSL, você será solicitado a criar um Nome de Usuário e Senha. Após criar um nome de usuário e senha, essa conta será o **usuário padrão e administrador da distribuição**, com permissões para executar comandos de super usuário (`sudo`).


## Instalação e configuração do Nginx no Ubuntu

## Configuração dos arquivos de log

## Criação do script de monitoramento do status do Nginx

## Automatização da execução do script
## Referências

- [Documentação do WSL](https://docs.microsoft.com/en-us/windows/wsl/)
- [Documentação do Nginx](https://nginx.org/en/docs/)
