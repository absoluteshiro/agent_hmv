# Funcionalidades e fluxos

## Painel

A página inicial apresenta métricas calculadas a partir dos registros existentes no banco. Os dados são carregados pelo endpoint de estatísticas do dashboard.

## Casos e acompanhamentos

O módulo de casos agrupa documentos e mensagens em um registro contínuo. Cada caso possui código sequencial, título, resumo, fornecedor, status, prioridade, pendências, próxima ação, valor e vencimento.

O localizador de casos tenta reutilizar um caso existente por correspondência de thread de e-mail, número de documento ou combinação de dados de fornecedor/documentos em casos ainda não concluídos. Se não encontrar correspondência, cria um novo caso.

Os estados previstos no código são `em_andamento`, `pendente`, `aguardando_resposta` e `concluido`. As prioridades previstas são `baixa`, `normal`, `alta` e `urgente`.

## Mensagens

A interface lista e-mails armazenados. Um resumo individual pode ser solicitado sob demanda; o resultado é salvo para reutilização. Há também uma rotina determinística que compara pares de mensagens e procura termos de fornecedor em comum para sugerir correlação.

## Documentos

O extrator usa `pdfplumber` para obter texto do PDF e expressões regulares para identificar campos conhecidos. A validação de identificadores fiscais e a conversão de moeda e datas são feitas por código, não por inferência livre da IA.

Os campos extraídos podem incluir tipo de documento, fornecedor, identificador fiscal, número, valores, datas, competência, referência contratual, centro de custo e conta contábil. A extração pode sinalizar necessidade de conferência quando campos importantes não são encontrados.

## Calendário

O calendário consulta os casos que possuem data de vencimento e os ordena cronologicamente.

## Auditoria

Eventos de autenticação, sincronização, processamento e outras ações são gravados em uma tabela de auditoria e exibidos na interface. A implementação registra eventos; a tabela não possui mecanismo técnico que a torne imutável contra alterações diretas no banco.

## Configurações

A aplicação permite alterar as credenciais do usuário autenticado e salvar preferências visuais no banco de dados.

## Lembretes e resumo diário

Há endpoints para criar, atualizar, excluir e listar lembretes, além de gerar e consultar resumos diários manualmente. O código consultado não contém os templates `reminders.html` e `daily_summary.html`, embora as rotas de página tentem carregá-los. Portanto, as páginas correspondentes não estão completas no pacote recebido. Também não foi identificada uma tarefa agendada que gere automaticamente o resumo às 17h.

## Sincronização

O botão/endpoint de sincronização atualmente aciona a base de cenários simulados armazenada localmente. A função de leitura do Gmail existe separadamente, mas precisa ser integrada ao fluxo de interface e ampliada para baixar e processar anexos caso esse seja o comportamento desejado.
