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
