# 🛡️ Nexus-Auth: Identity & Access Management System

O **Nexus-Auth** é um sistema de segurança desenvolvido em Python que simula um ambiente real de **IAM (Identity and Access Management)**. O projeto foca em dois pilares fundamentais da segurança da informação: **Autenticação** e **Autorização**.

## 🚀 Tecnologias Utilizadas
- **Linguagem:** Python 3
- **Segurança:** SHA-256 Hashing (via `hashlib`)
- **Arquitetura:** RBAC (Role-Based Access Control)

## 🛠️ Como Funciona
O sistema não armazena senhas em texto puro. Ele utiliza o algoritmo **SHA-256** para gerar hashes únicos, garantindo que mesmo se o banco de dados for exposto, as senhas originais permaneçam protegidas.

A autorização é baseada em **Roles (Cargos)**, onde o sistema verifica o nível de privilégio do usuário antes de permitir a execução de ações sensíveis, como abrir cofres ou deletar logs.

## 🏁 Como Executar
1. Certifique-se de ter o Python instalado.
2. Clone o repositório.
3. Execute o comando:
   ```bash
   python src/main.py

---

### 2. `docs/logic.md` (Sua documentação técnica)
Crie este arquivo dentro da pasta `docs`. Ele prova que você entende a teoria por trás do código.
```markdown
# 🧠 Lógica do Sistema

## 1. Hashing (Autenticação)
Para a segurança das credenciais, utilizamos o **SHA-256**. Diferente da criptografia comum, o hash é uma função unidirecional. 
- **Entrada:** Senha digitada pelo usuário.
- **Processamento:** `hashlib.sha256(password.encode()).hexdigest()`
- **Resultado:** Uma string de 64 caracteres que é comparada com o valor armazenado.

## 2. RBAC - Controle de Acesso Baseado em Cargos
A estrutura de autorização utiliza um mapeamento de dicionários:
- `cargos_usuarios`: Vincula o `Username` a uma `Role`.
- `permissoes_roles`: Vincula a `Role` a uma `List` de permissões permitidas.

Esta arquitetura permite que o sistema seja escalável. Se precisarmos de um novo cargo (ex: "Gerente"), basta adicioná-lo ao dicionário de permissões sem alterar a lógica principal do código.
