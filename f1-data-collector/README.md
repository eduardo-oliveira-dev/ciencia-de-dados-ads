# F1 Data Collector

Um coletor de dados da Fórmula 1 usando a API OpenF1 e armazenamento em MongoDB.

## 📋 Descrição

Este projeto coleta dados de sessões, pilotos e voltas da Fórmula 1 através da API OpenF1 e armazena as informações em um banco de dados MongoDB. Inclui também uma interface web opcional através do MongoDB Express.

## 🚀 Funcionalidades

- Coleta de dados de sessões da F1
- Coleta de informações dos pilotos
- Coleta de dados das voltas
- Prevenção de dados duplicados
- Interface web para visualização dos dados (MongoDB Express)
- Containerização com Docker

## 🛠️ Tecnologias Utilizadas

- Python 3.x
- MongoDB
- Docker & Docker Compose
- API OpenF1
- MongoDB Express (interface web)

## 📦 Dependências

```
requests==2.31.0
pymongo==4.6.1
python-dotenv==1.0.0
```

## ⚙️ Configuração e Execução

### Método 1: Com Docker (Recomendado)

1. **Clone o repositório**
   ```bash
   git clone https://github.com/eduardo-oliveira-dev/ciencia-de-dados-ads.git
   cd ciencia-de-dados-ads/f1-data-collector
   ```

2. **Inicie os containers**
   ```bash
   docker-compose up -d
   ```

3. **Crie o arquivo .env**
   ```bash
   echo "MONGO_URI=mongodb://admin:senha123@localhost:27017" > .env
   ```

4. **Execute o coletor**
   ```bash
   python f1_data_coletor.py
   ```

### Método 2: Ambiente Local

1. **Crie e ative o ambiente virtual**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   # ou
   venv\Scripts\activate     # Windows
   ```

2. **Instale as dependências**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure o MongoDB** (certifique-se de que está rodando)

4. **Crie o arquivo .env**
   ```bash
   echo "MONGO_URI=mongodb://localhost:27017" > .env
   ```

5. **Execute o script**
   ```bash
   python f1_data_coletor.py
   ```

## 🔧 Configurações

### Variáveis de Ambiente

- `MONGO_URI`: String de conexão com o MongoDB

### Parâmetros Configuráveis (no código)

- `SESSION_KEY`: Chave da sessão específica
- `MEETING_KEY`: Chave do meeting/evento
- `YEAR`: Ano da temporada

**Configuração Atual:**
- GP Jeddah 2024 (SESSION_KEY = 9476, MEETING_KEY = 1230)

## 🌐 Acesso à Interface Web

Após iniciar o Docker Compose, acesse:
- **MongoDB Express**: http://localhost:8081
- **MongoDB**: mongodb://localhost:27017

### Credenciais MongoDB
- **Usuário**: admin
- **Senha**: senha123

## 📊 Estrutura dos Dados

### Collections MongoDB

1. **sessions**: Dados das sessões de corrida
2. **drivers**: Informações dos pilotos
3. **laps**: Dados das voltas

### Chaves Únicas

- **sessions**: `session_key`
- **drivers**: `session_key` + `driver_number`
- **laps**: `session_key` + `driver_number` + `lap_number`

## 📂 Estrutura do Projeto

```
f1-data-collector/
├── docker-compose.yml      # Configuração dos containers
├── f1_data_coletor.py     # Script principal de coleta
├── requirements.txt       # Dependências Python
├── README.md             # Este arquivo
└── .env                  # Variáveis de ambiente (criar)
```

## 🤝 Como Contribuir

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 🔗 Links Úteis

- [API OpenF1 Documentation](https://openf1.org/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [Docker Documentation](https://docs.docker.com/)