# Operação e manutenção

## Inicialização e encerramento

1. Abra o Prompt de Comando na pasta do projeto.
2. Execute `iniciar.bat`.
3. Acesse `http://127.0.0.1:8000` no mesmo computador.
4. Para encerrar, pressione `Ctrl+C` na janela em que o servidor está rodando.

## Banco de dados e cópias de segurança

O arquivo SQLite e a pasta de armazenamento podem conter conteúdo operacional. Mantenha backups criptografados e fora do repositório Git. Teste periodicamente a restauração em uma cópia separada.

Não inclua em backup compartilhado ou em commits os arquivos locais de configuração, tokens OAuth ou credenciais. Se precisar migrar o ambiente para outro computador, configure as credenciais novamente no destino.

## Diagnóstico inicial

| Sintoma | Verificação sugerida |
|---|---|
| Porta já ocupada | Confirme se outra instância do servidor está em execução ou ajuste a porta na configuração local. |
| IA não responde | Confirme se o Ollama está ativo e se os modelos configurados estão disponíveis. |
| Erro de banco bloqueado | Feche ferramentas externas que estejam mantendo uma transação ou bloqueio no arquivo SQLite e reinicie o processo com segurança. |
| Falha na integração Gmail | Verifique a instalação das bibliotecas Google e refaça o fluxo OAuth local, sem compartilhar os arquivos de credenciais. |
| Template não encontrado | Confira se o HTML correspondente existe em `app/templates/`. No pacote analisado, os templates de lembretes e resumo diário estão ausentes. |

## Arquivos e pastas importantes

- `app/`: código da aplicação.
- `app/templates/`: páginas HTML.
- `app/static/`: recursos estáticos, como CSS.
- `app/backup/`: cópias antigas de módulos; confirme diferenças antes de reutilizar.
- `armazenamento/`: conteúdo processado e arquivos de teste/entrada; não deve ser versionado.
- `.venv/`: ambiente virtual local; deve ser recriado em cada máquina.

## Atualizações

Antes de atualizar o código:

1. Faça backup privado do banco e dos documentos necessários.
2. Leia as alterações e confirme se o esquema do banco mudou.
3. Atualize dependências em ambiente de teste.
4. Execute os testes disponíveis e valide login, painel, sincronização simulada e leitura de PDFs.
5. Só então substitua a versão em uso.

O pacote recebido contém scripts de teste pontuais, mas não uma suíte automatizada abrangente.
