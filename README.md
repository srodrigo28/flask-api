
# 🐍 Flask API Master: Gestão de Tarefas & Analytics

> Uma API RESTful robusta construída em Python com Flask, focada em segurança, relacionamento de dados e agregação via banco de dados.

Este projeto é um sistema backend completo (Multitenant) onde os usuários podem se cadastrar, gerar tokens de acesso, registrar tarefas financeiras e visualizar resumos de gastos diários calculados diretamente no banco de dados.

---

## ✨ Funcionalidades

- **🔐 Autenticação JWT:** Proteção de rotas utilizando `flask-jwt-extended`.
- **🛡️ Criptografia de Senhas:** Hashes seguros gerados nativamente com `Werkzeug`.
- **🗄️ Relacionamento SQL:** Uso do `Flask-SQLAlchemy` para mapear relações de 1 para N (1 Usuário -> N Tarefas).
- **📊 Agregação de Dados:** Filtros avançados com `group_by` e `sum` para devolver relatórios analíticos prontos.
- **🏗️ Arquitetura Isolada:** Dados de um usuário jamais vazam para outro.

---

## 🛠️ Tecnologias Utilizadas

- **Python 3.10+**
- **Flask** (Microframework web)
- **Flask-SQLAlchemy** (ORM para o Banco de Dados)
- **Flask-JWT-Extended** (Gerenciamento de Autenticação)
- **SQLite** (Banco de dados relacional leve para desenvolvimento)

---

## 🚀 Como Executar o Projeto Localmente

**1. Clone o repositório:**
```bash
git clone [https://github.com/SEU-USUARIO/flask-api-master.git](https://github.com/SEU-USUARIO/flask-api-master.git)
cd flask-api-master
```

## 2. Crie e ative o ambiente virtual (Recomendado):
### No Windows
python -m venv venv
venv\Scripts\activate

### No Linux/Mac
python3 -m venv venv
source venv/bin/

### 3. Instale as dependências:
```
pip install flask flask-sqlalchemy flask-jwt-extended werkzeug
```
### 4. Rode a aplicação:
> * O banco de dados (banco.db) será criado automaticamente na primeira execução.
```
python app.py
```

## 📖 Documentação da API (Endpoints)
> * Todas as requisições que enviam dados devem possuir o cabeçalho:
Content-Type: application/json

### table area Método	Rota	Descrição	Requer Auth
POST	/register	Cria uma nova conta de usuário.	        ❌
POST	/login	Valida credenciais e retorna o Token JWT.	❌

> * Exemplo de Payload (/register e /login):
```
{
  "username": "rodrigo",
  "password": "senha_segura_123"
}
```

### Exemplo de Payload (POST /tasks):
```
{
  "title": "Manutenção da VPS",
  "description": "Configuração do Nginx e Docker",
  "date": "2026-03-02",
  "value": 150.
}
```

### Exemplo de Resposta (GET /tasks/summary):
```
{
  "user_id": "1",
  "daily_summary": [
    {
      "date": "2026-03-02",
      "tasks_count": 1,
      "total_value": 150.50
    }
  ]
}
```