# Veyn — Assistente pessoal

O **Veyn** é uma aplicação web local para organizar e analisar mensagens, documentos e acompanhamentos administrativos. O projeto combina uma interface web, uma API em Python, armazenamento SQLite e recursos opcionais de IA executados localmente por meio do Ollama.

> **Escopo:** este repositório contém documentação técnica do Veyn. O conteúdo foi revisado para não reproduzir credenciais, tokens, dados operacionais, identificadores internos ou informações confidenciais. Não adicione arquivos de configuração local, bancos de dados, documentos ou dados reais.

## Funcionalidades identificadas

- Painel inicial com indicadores do banco de dados.
- Cadastro e acompanhamento de casos, com status, prioridade, pendências e próxima ação.
- Listagem de mensagens sincronizadas, resumo individual sob demanda e identificação simples de assuntos correlacionados.
- Extração determinística de campos de PDFs, incluindo tipo de documento, fornecedor, número, valores e datas.
- Calendário de vencimentos.
- Registro de eventos de auditoria.
- Autenticação por usuário e senha, sessões persistidas no SQLite e alteração de credenciais.
- Personalização de alguns elementos visuais.
- Estrutura de lembretes e resumos diários na API; as respectivas páginas HTML não estão presentes no pacote analisado.
- Integração opcional com Gmail por OAuth em escopo de somente leitura.
- Integração opcional com Ollama para classificação, síntese e resumos.

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Backend / API | Python, FastAPI, Uvicorn |
| Interface | HTML, CSS e JavaScript servido pelo FastAPI |
| Persistência | SQLite |
| Extração de PDF | pdfplumber |
| Autenticação | argon2-cffi (Argon2) e sessões próprias |
| IA local | Ollama via HTTP local |
| E-mail | Gmail API e OAuth 2.0 (opcional) |

## Início rápido

O projeto foi entregue com um script de inicialização para Windows. Consulte [Instalação e execução](docs/INSTALACAO.md) antes de executar em uma instalação nova.

Na configuração original, o servidor é iniciado em `127.0.0.1` na porta `8000`, e a interface é acessada em `http://127.0.0.1:8000`.

## Documentação

- [Visão geral e arquitetura](docs/ARQUITETURA.md)
- [Funcionalidades e fluxos](docs/FUNCIONALIDADES.md)
- [Banco de dados](docs/BANCO_DE_DADOS.md)
- [Instalação e execução](docs/INSTALACAO.md)
- [Operação e manutenção](docs/MANUTENCAO.md)
- [API e rotas](docs/API.md)
- [Segurança, privacidade e limitações](docs/SEGURANCA_E_LIMITACOES.md)

## Estado e escopo desta documentação

Esta documentação foi elaborada por inspeção estática dos arquivos de código fornecidos. O sistema não foi executado nem submetido a testes funcionais neste processo. Recursos descritos como implementados correspondem à presença de código; isso não significa homologação ou garantia de funcionamento em ambiente novo.

Consulte [Segurança, privacidade e limitações](docs/SEGURANCA_E_LIMITACOES.md) para recomendações gerais antes de qualquer implantação fora do computador local.
