# Banco de dados

## Tecnologia e acesso

A persistência utiliza SQLite em um arquivo local. O caminho é definido pela configuração da aplicação. As conexões habilitam chaves estrangeiras e o modo WAL, com timeout para reduzir conflitos de concorrência. O gerenciador `db_session()` confirma a transação quando termina sem erro e executa rollback em caso de exceção.

## Tabelas identificadas

| Tabela | Finalidade |
|---|---|
| `users` | Usuários e hashes de senha. |
| `sessions` | Sessões autenticadas e respectivos vencimentos. |
| `audit_logs` | Eventos de auditoria. |
| `cases` | Casos e seus dados de acompanhamento. |
| `documents` | Metadados e campos extraídos dos documentos. |
| `emails` | Metadados, conteúdo armazenado, resumos e vínculos das mensagens. |
| `sync_history` | Histórico de execuções de sincronização. |
| `system_config` | Configurações persistidas, incluindo preferências visuais. |
| `reminders` | Lembretes e pendências. |
| `daily_summaries` | Resumos diários salvos. |

## Relacionamentos principais

- `sessions.user_id` referencia `users.id` e é removido em cascata quando o usuário é excluído.
- `documents.case_id` referencia `cases.id`; ao excluir um caso, o vínculo do documento é definido como nulo.
- `emails.case_id` referencia `cases.id`; ao excluir um caso, o vínculo do e-mail é definido como nulo.
- `reminders.case_id` referencia `cases.id`; ao excluir um caso, o vínculo do lembrete é definido como nulo.

## Índices

O esquema cria índices para status, vencimento e identificador fiscal dos casos; vínculo dos documentos; identificador de mensagem; e data da auditoria.

## Inicialização e evolução

`init_db()` cria as tabelas e índices que ainda não existem. Também verifica algumas colunas da tabela de mensagens e as adiciona quando ausentes. Não há, no material recebido, um sistema formal de migrações versionadas.

## Backup

O banco pode conter dados pessoais e operacionais. Faça cópias em local privado e protegido, preferencialmente com o servidor parado ou usando um procedimento compatível com SQLite/WAL. **Não envie o banco para o GitHub** — mesmo em repositório privado. O banco deve ser tratado como dado operacional, separado do código e da documentação.
