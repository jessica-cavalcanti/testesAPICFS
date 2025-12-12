# Automação de Testes de API (Postman + Newman + GitHub Actions

# 🧪 Automação de Testes de API — Serverest.dev  
Automação desenvolvida como parte do desafio técnico para testar a API RESTful de gerenciamento de usuários disponibilizada pela plataforma **Serverest.dev**.

A suíte de testes foi construída utilizando **Postman**, com execução automatizada via **Newman** e integração contínua através do **GitHub Actions**. Relatórios HTML são gerados automaticamente a cada execução da pipeline.

---

## 🚀 Tecnologias Utilizadas

- **Postman** – Criação das requisições e scripts de teste  
- **Newman** – Executor de coleções Postman via linha de comando  
- **newman-reporter-htmlextra** – Relatório HTML completo  
- **GitHub Actions** – Pipeline de CI  
- **Node.js 18** – Ambiente para rodar Newman  

---

## 📌 Funcionalidades Testadas

A API permite:

- Criar usuários  
- Listar usuários  
- Buscar usuário por ID  
- Editar usuário  
- Excluir usuário  
- Login  

A coleção contém testes para:

| Funcionalidade | Testes realizados |
|---------------|------------------|
| Login | Login com dados válidos |
| Criar usuário | Criação com sucesso e validação de campos |
| Buscar por ID | Validação da consulta e do ID retornado |
| Editar usuário | Atualização de dados e validações |
| Deletar usuário | Exclusão e retorno esperado |
| Listar usuários | Lista retornada e quantidade mínima |
| Email duplicado | Validação de retorno HTTP 400 |

---


