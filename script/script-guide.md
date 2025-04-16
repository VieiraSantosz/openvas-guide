<h1 align="center">

[![image](https://github.com/user-attachments/assets/23613c58-4849-4e12-8c82-4baa553f5595)](https://www.openvas.org/)

Script para Instalação do OpenVAS

</h1>

<h4 align="center">

Instruções para executar o script install_openvas.sh e o primeiro acesso à plataforma. 

</h4>

## Pré-Requisitos

Antes de executar o script, verifique se o seu servidor atende aos seguintes requisitos:

- **Sistema operacional:** Ubuntu e Debian
- **Mínimo de disco:** 32 GB
- **Mínimo de memória RAM:** 8 GB
- **Mínimo de CPU:** 4 CPU


## Execução do Script
**1. Atualizar o servidor**

Antes de executar o script, certifique-se de que o servidor está atualizado. Isso garante que os pacotes necessários sejam instalados corretamente.
```bash
sudo apt update && sudo apt upgrade -y
```

**2. Clone o repositório**

Clone o repositório onde o script de instalação está armazenado.
```bash
git clone https://github.com/VieiraSantosz/openvas-guide.git
```

**3. Navegar até o diretório do script**

Acesse a pasta onde o script foi clonado.
```bash
cd openvas-guide/script
```

**4. Conceder permissões para o script**

Antes de executar o script, é necessário garantir que ele tenha permissões de execução.
```bash
chmod +x install_openvas.sh
```

**5. Executar o script de instalação**

Agora, execute o script para iniciar a instalação do Grafana.
```bash
./install_openvas.sh
```

![image](https://github.com/user-attachments/assets/2589a0d3-4fbf-4b3b-903b-04a5ca431583)


Após a instalação, o script fornecerá o link de acesso à interface web. Guarde essa informação, pois você precisará dela para acessar a plataforma do OpenVAS.

![image](https://github.com/user-attachments/assets/53c8f038-64b7-46d6-a9b3-1b2c45860a92)


## Primeiro acesso à plataforma

**1. Acessar a interface web**

Depois que os serviços estiverem ativos, abra o navegador e acesse a interface web do OpenVAS utilizando o IP da sua máquina seguido da porta 9392.
```bash
http://<IP-do-Servidor:9392>
```

**2. Login inicial**

Ao abrir a interface, será exibida a tela de login. Use as credenciais padrão para acessar:
**Usuário:** admin
**Senha:** admin

![image](https://github.com/user-attachments/assets/58360927-e99a-4cd4-8026-2b755781ebb1)


**3. Após o Login**

Após o login, você terá acesso ao painel do OpenVAS. A partir daí, poderá explorar as funcionalidades da ferramenta, realizar varreduras e customizar conforme suas necessidades.

![image](https://github.com/user-attachments/assets/3eb18050-5048-433c-820f-f9a6f1896743)


## Solução de Problemas

Caso a instalação não tenha ocorrido conforme esperado, verifique o seguinte:
- **Falha na conexão com a internet:** Verifique se a sua conexão está funcionando corretamente e que o servidor consegue acessar os repositórios necessários para baixar as imagens Docker.
- **Acesso à interface web:** Se você não consegue acessar a interface web do OpenVAS, certifique-se de que a porta 9392 está aberta no firewall do servidor.
- **Problemas com Docker:** Confirme se o Docker está em execução com docker ps.
- **Containers não iniciam:** Containers não iniciam: Use o comando abaixo para ver os logs e identificar possíveis erros com docker compose logs.
