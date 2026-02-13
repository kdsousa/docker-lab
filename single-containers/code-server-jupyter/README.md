# 🖥️ Code-Server com Jupyter

> **Categoria:** Dev Tools | **Tipo:** Single Container | **Porta Padrão:** 8080

Este diretório contém a configuração para rodar o **VS Code** no navegador com suporte nativo a **Jupyter Notebooks**, permitindo a execução de células de código e visualização de dados diretamente pela interface web.

---

## 📦 1. Construindo a Imagem

Certifique-se de estar na pasta `single-containers/code-server-jupyter` e execute:

```bash
docker build -t code-server-jupyter .
```


# 🚀 2. Executando o Container
Para garantir que seu progresso e notebooks sejam salvos e que o container reinicie automaticamente, utilize o comando abaixo:
```
docker run -d \
  --name code-server-jupyter \
  --restart always \
  -p 8080:8080 \
  -v "/home/ubuntu/notebooks:/home/ubuntu/notebooks" \
  code-server-jupyter
```

### 🔗 Acesso
Após iniciar, acesse no seu navegador:
👉 **http://localhost:8080**

---

## ⚙️ Configuração (config.yaml)
O arquivo de configuração incluído define os seguintes parâmetros:

* **Autenticação:** Desativada (`auth: none`).
* **Criptografia:** HTTPS desativado (`cert: false`).
* **Porta:** 8080.

---

## 🛑 Gerenciamento do Container

| Ação | Comando |
| :--- | :--- |
| **Parar** | `docker stop code-server-jupyter` |
| **Iniciar** | `docker start code-server-jupyter` |
| **Remover** | `docker rm -f code-server-jupyter` |