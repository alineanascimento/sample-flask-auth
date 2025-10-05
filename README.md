# 🔐 Sample Flask Auth

Aplicação simples de autenticação desenvolvida com **Flask**, **Flask-Login** e **Flask-SQLAlchemy**, utilizando **MySQL** como banco de dados.  
O projeto implementa rotas básicas de **CRUD de usuários** com autenticação via sessão.

---

## 📁 Estrutura do Projeto

```

sample-flask-auth/
│
├── models/
│   └── user.py           # Modelo da tabela de usuários
│
├── app.py               # Arquivo principal da aplicação Flask
├── database.py           # Configuração da conexão com o banco de dados
├── docker-compose.yml    # (Opcional) Configuração do ambiente Docker
├── requirements.txt      # Dependências do projeto
└── README.md             # Este arquivo 😎

````

---

## ⚙️ Tecnologias Utilizadas

- **Flask** → Framework principal da aplicação  
- **Flask-SQLAlchemy** → ORM para integração com o banco MySQL  
- **Flask-Login** → Controle de login e sessão de usuário  
- **PyMySQL** → Driver de conexão com MySQL  
- **Werkzeug** → Utilitário interno do Flask para autenticação  
- **Cryptography** → Suporte à criptografia e segurança

---

## 📦 Instalação e Execução

### 1️⃣ Clone o repositório
```bash
git clone https://github.com/alineanascimento/sample-flask-auth.git
cd sample-flask-auth
````

### 2️⃣ Crie o ambiente virtual

```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

### 3️⃣ Instale as dependências

```bash
pip install -r requirements.txt
```

### 4️⃣ Configure o banco de dados

No arquivo `appy.py`, edite a URI conforme suas credenciais MySQL:

```python
app.config['SQLALCHEMY_DATABASE_URI'] = "mysql+pymysql://root:admin123@127.0.0.1:3306/flask_crud"
```

Crie o banco no MySQL:

```sql
CREATE DATABASE flask_crud;
```

### 5️⃣ Execute a aplicação

```bash
python appy.py
```

A aplicação será executada por padrão em:
👉 `http://127.0.0.1:5000`

---

## 🔑 Endpoints Principais

### 👤 Criar usuário

**POST** `/user`

```json
{
  "username": "aline",
  "password": "12345"
}
```

**Resposta**

```json
{
  "message": "Dados cadastrados com sucesso."
}
```

---

### 🔐 Login

**POST** `/login`

```json
{
  "username": "aline",
  "password": "12345"
}
```

**Resposta**

```json
{
  "message": "Autenticado com sucesso"
}
```

---

### 🚪 Logout

**GET** `/logout`

> 🔒 Requer usuário autenticado

**Resposta**

```json
{
  "message": "Logout realizado com sucesso"
}
```

---

### 📄 Ler usuário

**GET** `/user/<id_user>`

> 🔒 Requer login

**Exemplo:**
`GET /user/1`

**Resposta**

```json
{
  "username": "aline"
}
```

---

### ✏️ Atualizar senha

**PUT** `/user/<id_user>`

> 🔒 Requer login

```json
{
  "password": "nova_senha"
}
```

**Resposta**

```json
{
  "message": "Usuário 1 atualizado com sucesso."
}
```

---

### ❌ Deletar usuário

**DELETE** `/user/<id_user>`

> 🔒 Requer login
> ❗ Não é permitido deletar o próprio usuário logado.

**Resposta**

```json
{
  "message": "Usuário 2 deletado com sucesso."
}
```

---

## 🧩 Dependências

| Biblioteca       | Versão |
| ---------------- | -----: |
| Flask            |  2.3.0 |
| Flask-SQLAlchemy |  3.1.1 |
| Flask-Login      |  0.6.2 |
| Werkzeug         |  2.3.0 |
| PyMySQL          |  1.1.0 |
| Cryptography     | 41.0.7 |

---

## 💡 Melhorias Futuras

* Hash de senha com **bcrypt**
* Templates HTML com **Flask-WTF**
* Autenticação JWT
* Integração com **Docker Compose** completa
