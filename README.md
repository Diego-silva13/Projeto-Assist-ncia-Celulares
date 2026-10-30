
# Sistema de Assistência Técnica de Celulares

Sistema web para gerenciamento de uma assistência técnica de celulares. A aplicação permite controlar clientes, aparelhos, serviços e agendamentos de reparos, com autenticação de usuários e integração com banco de dados MySQL.

## Funcionalidades

- **Autenticação:** login e encerramento de sessão.
- **Controle de acesso:** páginas e operações protegidas por sessão.
- **Clientes:** cadastro, consulta, edição, exclusão e busca.
- **Aparelhos:** cadastro, consulta, edição e exclusão de aparelhos vinculados aos clientes.
- **Agendamentos:** criação, consulta, atualização de status e exclusão.
- **Serviços:** consulta dos serviços disponíveis e seus valores.
- **Validações:** verificação de CPF, IMEI, campos obrigatórios e registros duplicados.
- **Segurança:** senhas e CPFs armazenados com hash bcrypt e consultas SQL parametrizadas.
- **Sessão:** expiração automática após 30 minutos.

## Tecnologias utilizadas

- **Python 3.10+**
- **Flask 3.0.3**
- **MySQL 8+**
- **mysql-connector-python 9.0.0**
- **bcrypt 4.2.0**
- **HTML5**
- **CSS3**
- **JavaScript**

## Requisitos

Antes de executar o projeto, instale:

- Python 3.10 ou superior.
- MySQL 8 ou superior.
- pip (gerenciador de pacotes Python).

## Como executar

Os comandos abaixo consideram o Windows e o terminal aberto na pasta do projeto.

### 1. Criar o ambiente virtual

```bash
python -m venv venv
```

### 2. Ativar o ambiente virtual

No Windows:

```bash
venv\Scripts\activate
```

### 3. Instalar as dependências

```bash
pip install -r requirements.txt
```

### 4. Criar o banco de dados

Com o MySQL em execução, importe o arquivo `assistencia_db.sql`.

Caso o comando MySQL esteja disponível no terminal:

```bash
mysql -u root -p < assistencia_db.sql
```

Esse script cria o banco `assistencia_db`, suas tabelas e registros iniciais.

**Atenção:** o script SQL remove e recria o banco `assistencia_db`. Não execute se houver dados que deseja preservar.

### 5. Configurar a conexão

Configure as variáveis de ambiente conforme os dados do seu MySQL.

Exemplo no PowerShell:

```powershell
$env:DB_HOST="localhost"
$env:DB_PORT="3306"
$env:DB_USER="root"
$env:DB_PASSWORD="SUA_SENHA"
$env:DB_NAME="assistencia_db"
$env:SECRET_KEY="sua-chave-secreta"
```

### 6. Testar a conexão

```bash
python testar_conexao.py
```

### 7. Executar o sistema

```bash
python app.py
```

Depois, acesse pelo navegador:

http://localhost:5000

## Usuários para teste

O banco de dados possui usuários cadastrados para demonstração:

| Perfil | Usuário | Senha |
|---|---|---|
| Administrador | admin | admin123 |
| Técnico | carlos | carlos123 |
| Atendente | ana | ana12345 |

## Estrutura do projeto

```text
sistema_celulares_flask_desafio/
│
├── app.py
├── rotas.py
├── autenticacao.py
├── db.py
├── clientes.py
├── aparelhos.py
├── agendamento.py
├── assistencia_db.sql
├── requirements.txt
├── testar_conexao.py
├── ROTEIRO.md
│
├── templates/
│   ├── login.html
│   ├── principal.html
│   ├── clientes.html
│   ├── aparelhos.html
│   └── agendamentos.html
│
└── static/
    ├── app.js
    └── style.css
```

## API

O sistema disponibiliza rotas para operações e consultas:

| Método | Rota | Descrição |
|---|---|---|
| POST | /api/login | Realiza login |
| POST | /api/logout | Encerra sessão |
| GET | /api/me | Consulta usuário autenticado |
| GET | /api/teste-conexao | Testa conexão com banco |
| GET | /api/clientes | Lista clientes |
| POST | /api/clientes | Cadastra clientes |
| GET | /api/aparelhos | Lista aparelhos |
| POST | /api/aparelhos | Cadastra aparelhos |
| GET | /api/agendamentos | Lista agendamentos |
| POST | /api/agendamentos | Cadastra agendamentos |
| GET | /api/servicos | Lista serviços |

As operações de edição e exclusão utilizam os métodos `PUT` e `DELETE`.

## Testes

O arquivo `ROTEIRO.md` contém orientações para testar as funcionalidades do sistema, incluindo login, cadastros, edições, exclusões, validações e agendamentos.

## Segurança

O projeto utiliza mecanismos de segurança, como:

- Hash bcrypt para senhas e CPFs.
- Consultas SQL parametrizadas.
- Controle de acesso por sessão.
- Expiração automática de sessão.

**Observação:** este projeto foi desenvolvido para fins de estudo. Para utilização em produção, é necessário revisar as configurações de segurança, credenciais e ambiente de execução.

---

Desenvolvido como projeto de estudo de desenvolvimento web utilizando Python, Flask e MySQL.
