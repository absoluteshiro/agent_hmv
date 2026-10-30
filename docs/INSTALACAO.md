# Instalação e execução

> Este guia descreve uma instalação Windows baseada nos arquivos recebidos. O pacote não contém um `requirements.txt`; as versões abaixo foram identificadas no ambiente virtual incluído no ZIP e devem ser validadas em uma instalação limpa.

## Pré-requisitos

- Windows 10 ou 11.
- Python compatível com as dependências do projeto (o histórico do projeto registra Python 3.14.x).
- Ollama instalado, caso queira usar os recursos de IA local.
- Acesso à internet apenas para instalar pacotes e, opcionalmente, configurar a integração Google.

## Preparar o ambiente Python

Abra o Prompt de Comando na pasta raiz do projeto e execute:

```cmd
py -3.14 -m venv .venv
.\.venv\Scripts\python.exe -m pip install --upgrade pip
.\.venv\Scripts\python.exe -m pip install fastapi uvicorn pdfplumber argon2-cffi
```

Para habilitar a integração opcional com Gmail:

```cmd
.\.venv\Scripts\python.exe -m pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
```

As versões encontradas no ambiente virtual enviado foram: FastAPI 0.162.0, Uvicorn 0.54.0, pdfplumber 0.11.10, argon2-cffi 25.1.0 e bibliotecas Google API 2.201.0 / 0.4.4 / 1.5.0, respectivamente. Essas versões são uma referência do ambiente recebido, não uma garantia de compatibilidade futura.

## Configuração local

A aplicação lê parâmetros locais por meio do módulo `app/config.py`. Os valores de configuração e quaisquer credenciais devem permanecer fora do controle de versão. Não copie valores de arquivos locais de configuração para esta documentação ou para o repositório.

O projeto inclui um arquivo de inicialização `iniciar.bat`, que usa o Python do ambiente `.venv` e inicia o Uvicorn no endereço local `127.0.0.1`, porta `8000`.

## Inicializar o banco

O ciclo de inicialização do próprio FastAPI chama `init_db()` automaticamente. Há também um utilitário separado para inicialização do banco; antes de usá-lo em uma instalação nova, revise o fluxo de criação do usuário inicial descrito em [Segurança e limitações](SEGURANCA_E_LIMITACOES.md).

## Iniciar

```cmd
iniciar.bat
```

Abra no navegador:

```text
http://127.0.0.1:8000
```

Para encerrar, volte à janela do Prompt de Comando e pressione `Ctrl+C`.

## Ollama

Para recursos de IA, inicie o Ollama e obtenha localmente os modelos configurados em `app/config.py`. O projeto possui parâmetros separados para o modelo de triagem rápida e para o modelo de análise. Os nomes podem ser ajustados pela configuração local.

## Integração Gmail (opcional)

A integração usa OAuth 2.0 e escopo de somente leitura. Os arquivos de credenciais e tokens OAuth devem ser criados/configurados localmente e mantidos fora do Git. Não os inclua em commits, issues ou documentação.

## Dependências ausentes

Não foi encontrado um arquivo `requirements.txt` no pacote analisado. Recomenda-se criar e manter um manifesto de dependências versionado, após validar uma instalação limpa, para reproduzir o ambiente com segurança.
