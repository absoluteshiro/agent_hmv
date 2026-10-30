# Segurança, privacidade e limitações

## Cuidados com o repositório

Este repositório pode ser público. Por isso, mantenha nele apenas código e documentação que possam ser compartilhados. Não versione:

- arquivos `.env` ou outros arquivos de configuração local;
- credenciais OAuth, tokens, senhas ou chaves;
- bancos SQLite, arquivos WAL/SHM ou backups;
- documentos, PDFs, anexos, e-mails ou dados operacionais;
- dados reais de usuários, fornecedores ou instituições;
- ambiente virtual, caches e arquivos compilados.

A documentação descreve a estrutura e o comportamento geral observados no pacote analisado, sem reproduzir valores de credenciais, tokens, dados de exemplo ou identificadores internos.

## Recomendações gerais de segurança

- Utilize credenciais próprias e mantenha-as fora do controle de versão.
- Armazene segredos em configuração local protegida ou em um gerenciador de segredos apropriado.
- Proteja o banco SQLite e a pasta de armazenamento, pois podem conter dados pessoais ou operacionais.
- Mantenha cópias de segurança fora do repositório e teste a restauração periodicamente.
- Antes de habilitar acesso remoto, revise autenticação, sessões, proteção CSRF, HTTPS, cookies e permissões.
- Não exponha diretamente o servidor de desenvolvimento à internet.

## Limitações funcionais observadas

1. **Integração de e-mail:** a rotina de leitura da caixa de entrada e o fluxo de sincronização acionado pela interface ainda não estão totalmente integrados.
2. **Anexos:** o fluxo atual não realiza o download e processamento completo de anexos na sincronização real.
3. **Páginas incompletas:** foram identificadas rotas para algumas páginas cujos respectivos arquivos de interface não estavam presentes no pacote analisado.
4. **Resumo diário:** existe geração manual; não foi identificada execução automática agendada.
5. **Dependências:** não foi encontrado um manifesto completo e versionado de dependências no pacote analisado.
6. **Testes:** existem verificações pontuais, mas não uma suíte automatizada abrangente.

## Acesso remoto

O projeto foi analisado como aplicação local. Para disponibilizá-lo em outra rede ou pela internet, planeje uma solução com autenticação reforçada, HTTPS, VPN ou túnel privado, cookies seguros, proteção CSRF e revisão das permissões. Alterar apenas o endereço de escuta do servidor não é suficiente para torná-lo seguro.

## Escopo da revisão

A revisão foi estática: leitura do código e dos arquivos de estrutura fornecidos. Não foram executados testes dinâmicos, testes de invasão, análise automatizada de dependências ou validação em ambiente limpo. As observações descrevem o pacote recebido e devem ser confirmadas durante a manutenção do projeto.
