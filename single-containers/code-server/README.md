# 🖥️ Code-Server (VS Code Web)

> **Categoria:** Dev Tools | **Tipo:** Single Container | **Porta Padrão:** 4277

Este diretório contém a configuração para rodar o **VS Code** diretamente no seu navegador. A imagem é construída sobre o Ubuntu 22.04 e configurada para rodar com um usuário não-root, garantindo mais segurança e compatibilidade com permissões de arquivos.

---

## 📦 1. Construindo a Imagem

Certifique-se de estar na pasta `single-containers/code-server` e execute:

```bash
docker build -t code-server .
```


## 🚀 2. Executando o Container
Para rodar o Code-Server com persistência de dados (garantindo que seus arquivos não sumam ao parar o container), utilize o comando abaixo:

```bash
docker run -d \
  --name code-server \
  -p 4277:4277 \
  -v "$(pwd)/projects:/home/ubuntu/projects" \
  code-server-local
  ```

## 🔗 Acesso
Após o deploy, o VS Code estará disponível em:
👉 http://localhost:4277

## ⚙️ Configuração (config.yaml)

O arquivo de configuração incluído define os seguintes parâmetros padrão:

* **Autenticação:** Desativada (`auth: none`) para acesso rápido local.
* **Criptografia:** HTTPS desativado (`cert: false`).
* **Rede:** Vinculado ao endereço `0.0.0.0` para permitir acesso externo ao container.

> **Nota:** Se for expor este serviço na internet, recomenda-se alterar a configuração de `auth` para `password` e definir uma senha no arquivo `config.yaml`.

## 🛑 Gerenciamento do Container

| Ação | Comando |
| :--- | :--- |
| **Parar** | `docker stop code-server` |
| **Iniciar** | `docker start code-server` |
| **Remover** | `docker rm -f code-server` |