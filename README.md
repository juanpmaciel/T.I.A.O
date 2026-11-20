# T.I.A.O

Chatbot acadêmico de tricologia desenvolvido para a Faculdade Cruzeiro do Sul.
O projeto disponibiliza uma interface web em HTML/CSS/JavaScript e uma API Flask
que encaminha as mensagens ao modelo `llama-3.3-70b-versatile` da Groq.

## Estrutura do projeto

- `main.py`: inicia o servidor Flask na porta `5000`, serve o frontend e expõe a API.
- `core/prompt_mestre.py`: define o prompt de sistema P.T.R.F. usado pelo chatbot.
- `services/ia_service.py`: cria as chamadas ao modelo da Groq.
- `frontend/`: interface web (`index.html`, `style.css`, `script.js` e imagens).
- `requirements.txt`: dependências Python do projeto.

## Pré-requisitos

- Python 3
- Uma chave da API Groq

## Instalação

Na raiz do repositório, crie e ative um ambiente virtual e instale as dependências:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Configure a chave da Groq no ambiente antes de iniciar o servidor:

```bash
export GROQ_API_KEY="sua-chave"
```

Não confirme a chave da API no repositório.

## Execução

Execute a aplicação a partir da raiz do projeto:

```bash
python main.py
```

O servidor usa o modo de depuração do Flask e fica disponível em:

- Interface: `http://localhost:5000`
- Status: `http://localhost:5000/status`
- Chat: `POST http://localhost:5000/chat`

O endpoint `/chat` recebe JSON no formato abaixo:

```json
{
  "mensagem": "O que pode causar queda de cabelo?",
  "historico": []
}
```

## Testes e verificação

O repositório não possui atualmente uma suíte ou script de testes. Como
verificação mínima disponível, compile os arquivos Python e execute o servidor
em outro terminal:

```bash
python -m compileall main.py core services
python main.py
```

Com o servidor em execução, confirme o status com:

```bash
curl http://localhost:5000/status
```
