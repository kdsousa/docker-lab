# 🐳 Docker Lab

Este repositório é uma coleção organizada de configurações Docker para diversos ambientes. O objetivo é centralizar o provisionamento de serviços, ferramentas de desenvolvimento e stacks de infraestrutura de forma rápida e reprodutível.

---

## 🏗️ Organização do Projeto

O repositório está estruturado para diferenciar serviços isolados de arquiteturas complexas:

* **`./single-containers/`**: Contém `Dockerfiles` para builds customizados de ferramentas individuais.
* **`./stacks/`**: Contém arquivos `docker-compose.yml` para orquestrar múltiplos serviços que dependem entre si (bancos de dados, redes, volumes compartilhados).

---

## 🛠️ Ferramentas Catalogadas

Abaixo, a lista de serviços prontos para uso neste repositório:

| Categoria | Serviço | Tipo | Descrição |
| :--- | :--- | :--- | :--- |
| **Dev Tools** | Code-Server | Single | IDE VS Code via Browser. |
| **Dev Tools** | Code-Server-Jupyter | Single | IDE VS Code via Browser. |



---

## 🚀 Como Iniciar

### Usando Dockerfile (Single)
1. Acesse o diretório do serviço: `cd single-containers/nome-do-servico`
2. Build da imagem: `docker build -t nome-da-imagem .`
3. Execução: `docker run -d --name meu-container nome-da-imagem`

### Usando Docker Compose (Stacks)
1. Acesse o diretório da stack: `cd stacks/nome-da-stack`
2. Suba os serviços: `docker-compose up -d`

---

## ⚙️ Configurações e Segurança

1.  **Variáveis de Ambiente:** Muitos serviços utilizam arquivos `.env`. Nunca suba senhas reais para o repositório. Utilize arquivos `.env.example` como referência.
2.  **Volumes:** Os dados persistentes são geralmente mapeados para pastas locais ou volumes nomeados do Docker. Verifique a seção `volumes` no arquivo de configuração antes de iniciar.
3.  **Rede:** Stacks complexas utilizam redes internas do Docker para comunicação entre containers sem expor portas desnecessárias ao host.

---

## 📝 Requisitos Mínimos
* Docker Engine instalado.
* Docker Compose V2.

---
*Repositório mantido para fins de produtividade e estudos.*