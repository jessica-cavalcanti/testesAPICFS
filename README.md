# 🧪 Automação de Testes de API — Documentação

Este projeto contém a automação de testes da API **Loja Virtual**, utilizando **Postman**, **Newman** e **GitHub Actions**.
Aqui você encontrará informações sobre:

* Os testes implementados
* Como configurar o ambiente
* Como rodar os testes localmente
* Como rodar os testes no CI (GitHub Actions)
* Como acessar o relatório gerado automaticamente

---

## 📂 **Tecnologias utilizadas**

* **Postman** — criação da coleção e dos ambientes
* **Newman** — executor CLI dos testes
* **Newman Reporter HTML Extra** — geração do relatório visual
* **Node.js** — ambiente necessário para o Newman
* **GitHub Actions** — execução automática dos testes e publicação do relatório

---

# 🧪 Testes Implementados

A automação cobre os principais fluxos da API de usuários:

### ✔️ **1. Criar usuário**

* Valida retorno **201**
* Garante que o usuário foi criado com ID único
* Testa diferentes valores dinâmicos para evitar duplicidade

### ✔️ **2. Buscar usuário por ID**

* Verifica **200 OK**
* Confirma que o ID retornado é o mesmo do usuário criado
* Confere estrutura do JSON retornado

### ✔️ **3. Login**

* Valida autenticação com usuário criado anteriormente
* Verifica retorno **200**
* Testa mensagem e token (se aplicável)

### ✔️ **4. Listar usuários**

* Valida retorno **200**
* Verifica se a lista não está vazia
* Garante estrutura consistente

---

# ⚙️ **Configuração do Ambiente**

### 1️⃣ Instalar o Node.js

Baixe aqui: [https://nodejs.org/](https://nodejs.org/)

Verifique se instalou corretamente:

```bash
node -v
npm -v
```

---

### 2️⃣ Instalar o Newman + HTML Extra

Na raiz do projeto, execute:

```bash
npm install -g newman newman-reporter-htmlextra
```

---

### 3️⃣ Arquivos necessários

O projeto contém:

```
📁 Loja Virtual.postman_collection.json
📁 baseUrl.postman_environment.json
```

A coleção contém todos os testes implementados.
O ambiente contém a variável `baseUrl` utilizada nas requisições.

---

# ▶️ Como Rodar os Testes Localmente

Na raiz do projeto, execute:

```bash
newman run "Loja Virtual.postman_collection.json" \
  -e "baseUrl.postman_environment.json" \
  --iteration-count 1 \
  -r cli,htmlextra \
  --reporter-htmlextra-export reports/index.html
```

Após executar:

📁 O relatório estará em:

```
reports/index.html
```

Abra o arquivo no navegador.

---

# 🤖 Execução via GitHub Actions (CI/CD)

Os testes são executados automaticamente **em todo push** no repositório.

O workflow:

1. Instala Node
2. Instala Newman
3. Executa os testes
4. Gera o relatório
5. Publica na **GitHub Pages**

### Trecho principal do workflow:

```yaml
- name: Run API Tests
  run: |
    mkdir -p reports

    newman run "Loja Virtual.postman_collection.json" \
      -e "baseUrl.postman_environment.json" \
      --iteration-count 1 \
      --delay-request 600 \
      -r cli,htmlextra \
      --reporter-htmlextra-export reports/index.html
```

---

# 🌐 Relatório Público — GitHub Pages

Após cada execução, o relatório atualizado fica disponível em:

👉 **[https://jessica-cavalcanti.github.io/testesAPICFS/](https://jessica-cavalcanti.github.io/testesAPICFS/)**

Sempre que o CI rodar, o relatório é automaticamente atualizado.

---

# 📝 Observações Importantes

* Testes repetidos podem gerar erros caso o backend não permita reutilizar o mesmo e-mail
* Por isso há geração dinâmica de dados (para evitar duplicidade)
* O CI sempre substitui o relatório anterior
---

# ✔️ Conclusão

Este projeto automatiza os testes principais da API Loja Virtual, permitindo:

* Execução local
* Execução automática no CI
* Relatório HTML publicado no GitHub Pages
* Validação de todos os fluxos principais de maneira repetível
