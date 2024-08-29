
### Automate Easy pay card linking to inner circle account for GMAP

Sim, o sistema inclui o envio de e-mails via o **Message Orchestrator**. Este componente é responsável por enviar notificações aos clientes após o processo de vinculação do cartão Easy Pay à conta do Inner Circle ter sido concluído com sucesso. A seguir estão os detalhes e as subtarefas relacionadas a esse sistema de envio de e-mails.

### Função do Message Orchestrator no Sistema

O **Message Orchestrator** serve como um serviço externo responsável por gerenciar e enviar mensagens, incluindo e-mails, para os clientes. No contexto deste projeto, ele será usado para enviar uma notificação de confirmação ao cliente informando que o cartão Easy Pay foi vinculado com sucesso à sua conta do Inner Circle.

### Subtarefas para Implementar o Envio de E-mails

Aqui estão as subtarefas necessárias para configurar e integrar o envio de e-mails via o Message Orchestrator:

#### 1. **Configuração do Template de E-mail**

- **1.1. Criar Template de E-mail:**
    
    - Desenvolver o conteúdo do e-mail que será enviado aos clientes. O template deve incluir informações como o nome do cliente, detalhes do cartão vinculado, e uma mensagem de confirmação.
    - Garantir que o template seja configurado no Message Orchestrator com um ID de template específico.
- **1.2. Personalização do Template:**
    
    - Adicionar placeholders para dados dinâmicos (como nome do cliente, data de vinculação, etc.) que serão substituídos com as informações específicas de cada cliente no momento do envio do e-mail.

#### 2. **Integração com o Enrollment Queue Processor**

- **2.1. Implementar Chamada à API do Message Orchestrator:**
    
    - Na função `Enrollment Queue Processor`, após o cartão ter sido vinculado com sucesso, adicionar uma chamada à API do Message Orchestrator.
    - Passar os parâmetros necessários (endereço de e-mail, ID do template, e dados dinâmicos) para a API do Message Orchestrator.
- **2.2. Verificar Respostas da API:**
    
    - Implementar lógica para lidar com as respostas da API. Caso o envio do e-mail seja bem-sucedido, registrar essa informação no log. Se houver falha, registrar o erro e implementar uma estratégia de retry ou fallback.

#### 3. **Monitoramento e Logs**

- **3.1. Implementar Logging Detalhado:**
    - Adicionar logs detalhados que registrem cada tentativa de envio de e-mail, incluindo o status de sucesso ou falha, e quaisquer erros retornados pela API do Message Orchestrator.
- **3.2. Configurar Alertas de Falhas:**
    - Configurar alertas para monitorar falhas no envio de e-mails, especialmente se o número de falhas exceder um determinado limite.

#### 4. **Testes de Envio de E-mails**

- **4.1. Testes de Integração:**
    
    - Realizar testes de integração para garantir que os e-mails estão sendo enviados corretamente após o processo de vinculação de cartões.
- **4.2. Testes de Templates:**
    
    - Testar diferentes cenários para garantir que os templates de e-mail estão sendo preenchidos corretamente com os dados dinâmicos.
- **4.3. Testes de Performance:**
    
    - Verificar o desempenho do sistema de envio de e-mails sob carga para garantir que ele possa lidar com um grande volume de e-mails simultâneos, se necessário.

### Resumo

O envio de e-mails via Message Orchestrator é um componente essencial deste projeto, garantindo que os clientes sejam notificados adequadamente quando seus cartões Easy Pay forem vinculados às contas do Inner Circle. A implementação bem-sucedida dessa funcionalidade envolve configurar corretamente os templates de e-mail, integrar as chamadas à API do Message Orchestrator na função `Enrollment Queue Processor`, e garantir que todo o processo seja monitorado e testado adequadamente para assegurar a confiabilidade e a eficiência do sistema.
### Resumo Completo do Projeto: Automação de Vinculação de Cartão Easy Pay ao Inner Circle

**Objetivo:**  
O objetivo deste projeto é automatizar o processo de vinculação de cartões Easy Pay a contas do Inner Circle, melhorando a experiência do cliente ao garantir que novos cartões sejam automaticamente associados às contas de membros, sejam eles novos ou existentes. O processo envolve a integração com vários sistemas e a implementação de funções que asseguram a execução correta e eficiente do fluxo de trabalho.

### Componentes Principais:

1. **Daily File Container (Sistema Externo):**
    
    - Responsável por fornecer o arquivo diário de inscrições contendo os cartões Easy Pay emitidos no dia anterior.
2. **Easy Pay Card Status API (Azure Function/Java 17):**
    
    - Recupera, valida e transforma as informações dos cartões Easy Pay, interagindo com o sistema externo para obter os dados necessários.
3. **Enrollment File Check (Azure Function/Java 17):**
    
    - Baixa o arquivo de inscrição diário do servidor SFTP, valida sua integridade e enfileira as entradas para processamento na `Queue`.
4. **Enrollment Queue Processor (Azure Function/Java 17):**
    
    - Desenfileira e processa cada entrada da fila, verificando se a conta de fidelidade existe e vinculando ou desvinculando o cartão Easy Pay conforme necessário.
    - Envia métricas de processo para o `Table Storage` e aciona o `Message Orchestrator` para enviar notificações por e-mail.
5. **Cron Scheduler:**
    
    - Ativa periodicamente as funções `Enrollment File Check` e `Enrollment Queue Processor` para garantir o processamento diário dos arquivos de inscrição.
6. **Queue:**
    
    - Armazena as informações de inscrição de maneira assíncrona, permitindo que o `Enrollment Queue Processor` recupere e processe os dados.
7. **Table Storage:**
    
    - Armazena métricas de desempenho e resultados do processo de vinculação de cartões.
8. **Loyalty Orchestrator (Sistema Externo):**
    
    - Gerencia a vinculação e desvinculação de cartões Easy Pay às contas de fidelidade dos clientes.
9. **Message Orchestrator (Sistema Externo):**
    
    - Envia e-mails de confirmação aos clientes após a vinculação bem-sucedida do cartão Easy Pay.

### Fluxo de Trabalho:

1. **Recepção do Arquivo Diário:**
    
    - O `Enrollment File Check` faz o download do arquivo de inscrição do `Daily File Container` via SFTP, valida sua estrutura e enfileira os dados na `Queue` para processamento.
2. **Processamento das Inscrições:**
    
    - O `Enrollment Queue Processor` lê as mensagens da fila, verifica a existência da conta de fidelidade, e realiza a vinculação ou desvinculação do cartão usando a API do `Loyalty Orchestrator`.
3. **Envio de Notificações:**
    
    - Após a vinculação do cartão, o `Enrollment Queue Processor` chama o `Message Orchestrator` para enviar um e-mail de confirmação ao cliente.
4. **Monitoramento e Métricas:**
    
    - As métricas do processo são armazenadas no `Table Storage`, e alertas são configurados para monitorar o desempenho e as falhas no sistema.

### Subtarefas Detalhadas:

1. **Configuração do Servidor SFTP:**
    
    - Estabelecer a conexão e configurar a transferência de arquivos do servidor SFTP da PDI.
2. **Implementação das Funções Azure (Java 17):**
    
    - Desenvolver as funções `Enrollment File Check` e `Enrollment Queue Processor`, incluindo a lógica de enqueue e dequeue.
3. **Integração com APIs Externas:**
    
    - Configurar chamadas às APIs do `Loyalty Orchestrator` e `Message Orchestrator` para gerenciar o vínculo dos cartões e enviar notificações.
4. **Monitoramento e Logs:**
    
    - Implementar o `Table Storage` para armazenar métricas e configurar alertas para monitorar o sistema.
5. **Automação de Processos com `Cron Scheduler`:**
    
    - Configurar o agendamento periódico das funções Azure para garantir o processamento diário dos arquivos de inscrição.
6. **Testes e Validação:**
    
    - Executar testes unitários, de integração, e de desempenho para garantir que o sistema funcione conforme o esperado.
7. **Documentação e Treinamento:**
    
    - Documentar todo o processo e realizar treinamento para a equipe responsável pela manutenção do sistema.


1. **NGPRPG-28683: Daily File Lookup**
    
    - **Descrição:** Esta subtarefa envolve a configuração e a execução da busca diária do arquivo de inscrições no servidor SFTP. O objetivo é garantir que o arquivo mais recente, que contém os dados dos cartões Easy Pay emitidos no dia anterior, seja localizado e recuperado para processamento subsequente.
    - **Atividades Incluídas:**
        - Conectar-se ao servidor SFTP.
        - Navegar até o diretório correto onde o arquivo de inscrição está armazenado.
        - Identificar e baixar o arquivo do dia.
2. **NGPRPG-28684: Process File and Enqueue Entries**
    
    - **Descrição:** Após o arquivo de inscrição ser recuperado, esta subtarefa foca no processamento desse arquivo. Isso inclui a leitura dos dados de inscrição e a enfileiramento de cada registro na `Queue` para processamento posterior.
    - **Atividades Incluídas:**
        - Validar a integridade do arquivo.
        - Extrair as informações dos registros de inscrição.
        - Enviar cada registro para a fila (`Queue`) para processamento assíncrono.
3. **NGPRPG-28685: Dequeue Entries for Processing**
    
    - **Descrição:** Esta subtarefa é responsável por desenfileirar as entradas na fila e processá-las. O foco está em garantir que cada registro de inscrição seja tratado de maneira correta e eficiente, ativando as próximas etapas do fluxo de trabalho.
    - **Atividades Incluídas:**
        - Ler mensagens/entradas da fila.
        - Preparar os dados para as operações subsequentes, como vinculação de cartões e envio de notificações.
4. **NGPRPG-28688: Fetch Data in Loyalty Orchestrator**
    
    - **Descrição:** Aqui, o foco está em interagir com a API do Loyalty Orchestrator para buscar as informações necessárias de cada conta de fidelidade associada ao cartão Easy Pay. Isso inclui verificar se a conta existe e obter detalhes relevantes para o processo de vinculação.
    - **Atividades Incluídas:**
        - Realizar chamadas à API do Loyalty Orchestrator.
        - Verificar se a conta de fidelidade existe para o cliente.
        - Recuperar detalhes da conta, como o status de vinculação do cartão.
5. **NGPRPG-28687: Send Email Message via Message Orchestrator**
    
    - **Descrição:** Após a vinculação do cartão Easy Pay, esta subtarefa lida com o envio de uma mensagem de e-mail de confirmação ao cliente, utilizando o Message Orchestrator. O e-mail notificará o cliente de que seu cartão foi vinculado com sucesso.
    - **Atividades Incluídas:**
        - Configurar e enviar o e-mail usando o Message Orchestrator.
        - Garantir que o e-mail contenha as informações corretas do cliente e do cartão vinculado.
        - Monitorar o sucesso do envio e tratar eventuais falhas.
6. **NGPRPG-28689: Manage Cards in Loyalty Orchestrator**
    
    - **Descrição:** Esta subtarefa se concentra na gestão dos cartões dentro do Loyalty Orchestrator. Isso inclui vincular o novo cartão Easy Pay à conta do cliente, desvincular cartões antigos, se necessário, e garantir que o estado final do cliente no sistema de fidelidade esteja correto.
    - **Atividades Incluídas:**
        - Chamar a API do Loyalty Orchestrator para vincular o cartão.
        - Desvincular cartões antigos, se aplicável.
        - Atualizar o status do cliente no sistema de fidelidade.




