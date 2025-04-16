<h1 align="center">

[![image](https://github.com/user-attachments/assets/23613c58-4849-4e12-8c82-4baa553f5595)](https://www.openvas.org/)

Guia de Instalação do OpenVAS

</h1>

<h4 align="center">

Instruções para a instalação do OpenVAS e o primeiro acesso à plataforma.

</h4>

## Pré-Requisitos

Antes de iniciar a instalação, verifique se o seu servidor atende aos seguintes requisitos:

- **Sistema operacional:** Ubuntu e Debian
- **Mínimo de disco:** 32 GB
- **Mínimo de memória RAM:** 8 GB
- **Mínimo de CPU:** 4 CPU


## Instalação do Docker

**1. Atualizar o servidor**

Antes de iniciar a instalação, certifique-se de que o servidor está atualizado. Isso garante que os pacotes necessários sejam instalados corretamente.
```bash
sudo apt update && sudo apt upgrade -y
```

**2. Adicionar a chave GPG oficial do Docker**

Essa chave é usada para verificar a autenticidade dos pacotes baixados do repositório oficial do Docker.
```bash
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

**3. Adicionar o repositório do Docker**

Adiciona o repositório oficial do Docker à lista de fontes do apt para que os pacotes possam ser instalados corretamente.
```bash
echo \
   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
   $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

**4. Instalar o Docker e seus plugins**

Com o repositório adicionado, você pode instalar o Docker Engine e os plugins necessários para utilizar o Docker Compose.
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```
**Nota**: Verifique se o serviço do Docker está ativo com **sudo systemctl status docker**.


## Instalação do OpenVAS

**1. Baixar o projeto OpenVAS**

Nesta etapa, você irá preparar o ambiente local criando uma pasta específica para o OpenVAS e baixando o arquivo docker-compose.yml, responsável por definir os serviços do OpenVAS via Docker.
```bash
mkdir openvas
cd openvas
curl -f -L https://greenbone.github.io/docs/latest/_static/docker-compose-22.4.yml -o docker-compose.yml
```

**2. Configurar o projeto OpenVAS**

Este comando substitui o IP padrão (127.0.0.1) pelo IP real da sua máquina. Isso é necessário para que os serviços possam ser acessados de fora do container.
```bash
sed -i "s|127.0.0.1|$(hostname -I | awk '{print $1}')|g" docker-compose.yml
```

**3. Iniciar os serviços do OpenVAS**

Agora que tudo está configurado, você pode iniciar os serviços do OpenVAS. O Docker irá baixar as imagens necessárias e levantar os containers definidos.
```bash
docker compose up -d
```

![image](https://github.com/user-attachments/assets/027f7ff1-90d1-4468-b01b-5ab530f3ebd6)

**Nota:** O processo pode levar alguns minutos na primeira execução, pois o Docker precisará baixar as imagens e realizar a configuração inicial. Aguarde até que todos os serviços estejam ativos.


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



