# 🚀 deploy-vercel-flaskapi

API desenvolvida com **Flask** e **scikit-learn** para realizar predições do modelo `load_iris`. O projeto demonstra o uso de autenticação via JWT, armazenamento de logs de predições em banco de dados SQLite, cache local e deploy para **Vercel**.

## 📦 Tecnologias

- Flask
- scikit-learn
- joblib
- SQLAlchemy
- JWT (PyJWT)
- Vercel (Deploy)
- SQLite

## 📁 Estrutura

```
.
├── api_modelo.py           # Código principal da API
├── modelo_iris.pkl         # Modelo treinado (joblib)
├── modelo.ipynb            # Notebook de criação e treinamento do modelo
├── predictions.db          # Banco de dados SQLite com histórico de predições
├── requirements.txt        # Dependências do projeto
```

## 🔐 Autenticação

- Endpoint `/login` fornece um token JWT.
- Utilize o token para acessar os endpoints `/predict` e `/predictions`.
- Header: `Authorization: Bearer <seu_token>`

Credenciais para testes:

```
username: admin
password: secret
```

## 📌 Endpoints

### `POST /login`

Gera um token de autenticação.

```json
{
  "username": "admin",
  "password": "secret"
}
```

---

### `POST /predict` (🔒 Requer Token)

Realiza uma predição com o modelo iris.

```json
{
  "sepal_length": 5.1,
  "sepal_width": 3.5,
  "petal_length": 1.4,
  "petal_width": 0.2
}
```

Resposta:
```json
{
  "prediction": 0
}
```

---

### `GET /predictions` (🔒 Requer Token)

Retorna histórico de predições.

Parâmetros opcionais:
- `limit` (padrão: 10)
- `offset` (padrão: 0)

---

## ▶️ Rodando localmente

```bash
pip install -r requirements.txt
python api_modelo.py
```

## 📜 Licença

MIT