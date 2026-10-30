# API e rotas

As rotas abaixo foram identificadas em `app/main.py`. As rotas de API exigem sessão válida, salvo o endpoint de lembretes pendentes, que retorna uma lista vazia quando não há sessão.

## Páginas web

| Método | Caminho | Descrição |
|---|---|---|
| GET | `/login` | Tela de autenticação. |
| POST | `/login` | Valida credenciais e cria sessão. |
| GET | `/logout` | Encerra sessão. |
| GET | `/` | Dashboard. |
| GET | `/casos` | Página de casos. |
| GET | `/emails` | Página de mensagens. |
| GET | `/documentos` | Página de documentos. |
| GET | `/calendario` | Página de vencimentos. |
| GET | `/auditoria` | Página de auditoria. |
| GET | `/configuracoes` | Página de configurações. |
| GET | `/lembretes` | Página prevista para lembretes; template ausente no pacote analisado. |
| GET | `/resumo-diario` | Página prevista para resumos; template ausente no pacote analisado. |

## Endpoints JSON

| Método | Caminho | Descrição |
|---|---|---|
| GET | `/api/dashboard/stats` | Métricas do painel. |
| POST | `/api/sync/run` | Executa a sincronização simulada atual. |
| GET | `/api/cases` | Lista casos; aceita filtros de status e busca. |
| GET | `/api/cases/{case_id}` | Detalhes do caso, documentos e mensagens vinculados. |
| GET | `/api/emails` | Lista mensagens armazenadas. |
| GET | `/api/emails/{email_id}/summary` | Obtém ou gera resumo individual. |
| GET | `/api/emails/correlations` | Sugere correlações entre mensagens. |
| GET | `/api/documents` | Lista documentos extraídos. |
| GET | `/api/calendar` | Lista casos com vencimento. |
| GET | `/api/audit-logs` | Consulta eventos recentes de auditoria. |
| POST | `/api/settings/change-credentials` | Altera login e senha do usuário autenticado. |
| GET | `/api/reminders` | Lista lembretes. |
| POST | `/api/reminders` | Cria lembrete. |
| PATCH | `/api/reminders/{reminder_id}` | Atualiza campos de lembrete. |
| DELETE | `/api/reminders/{reminder_id}` | Exclui lembrete. |
| GET | `/api/pending-reminders` | Lista lembretes vencidos/ativos para aviso. |
| GET | `/api/daily-summaries` | Lista resumos diários salvos. |
| POST | `/api/daily-summaries/generate` | Gera e salva resumo diário manualmente. |
| GET | `/api/settings/ui-config` | Consulta preferências visuais. |
| POST | `/api/settings/ui-config` | Salva preferências visuais. |

## Observações

- A autenticação usa cookie de sessão `HttpOnly`.
- O cookie foi configurado para uso em HTTP local; isso precisa ser revisto antes de qualquer implantação com HTTPS ou acesso remoto.
- Não foi gerada uma especificação OpenAPI independente nesta documentação; o FastAPI pode expor a documentação interativa padrão quando o servidor está em execução.
