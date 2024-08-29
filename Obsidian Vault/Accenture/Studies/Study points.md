### **Versioning (Controle de Versões)**

1. **Semantic Versioning (Versionamento Semântico)**: É uma convenção para atribuir números de versão a software. O número de versão é composto por três partes: `MAJOR.MINOR.PATCH` (por exemplo, `1.4.2`). Cada parte tem um significado específico:
    
    - **MAJOR**: Mudança incompatível na API, ou seja, quebra de compatibilidade.
    - **MINOR**: Novas funcionalidades compatíveis com versões anteriores.
    - **PATCH**: Correções de bugs compatíveis com versões anteriores. Esse sistema ajuda a indicar a severidade e o impacto das mudanças no software.
	
1. **Gitflow**: É um fluxo de trabalho que organiza o uso de branches no Git, facilitando o gerenciamento de versões e a integração de código. O Gitflow usa duas branches principais, `master` e `develop`, e várias branches auxiliares como `feature`, `release` e `hotfix`. Cada branch tem um propósito específico, por exemplo, as branches `feature` são usadas para desenvolver novas funcionalidades, enquanto as branches `release` são usadas para preparar o código para uma nova versão.
    
3. **Trunk Based Development**: É uma estratégia de desenvolvimento onde os desenvolvedores integram pequenas mudanças ao "trunk" (a branch principal) com frequência, muitas vezes diariamente. Ao contrário do Gitflow, onde há várias branches long-lived, o trunk-based development minimiza o número de branches, favorecendo a integração contínua e a entrega rápida.
    

### **Advanced Git (Git Avançado)**

1. **Rebase**: É um comando no Git que permite integrar mudanças de uma branch em outra, movendo ou "reaplicando" commits. O rebase é útil para manter um histórico de commits mais linear e limpo, evitando os "merge commits" que ocorrem com o comando `merge`.
    
2. **Pull Requests**: São solicitações de revisão de código que permitem a colaboração entre desenvolvedores em projetos. Com um pull request, um desenvolvedor solicita que seu código seja revisado e mesclado em uma branch principal, como `develop` ou `master`. Outros desenvolvedores podem revisar, comentar e aprovar ou sugerir mudanças antes que o código seja aceito.
    
3. **Merge Conflicts**: Ocorrências quando o Git não consegue automaticamente mesclar duas ou mais alterações feitas em um mesmo arquivo. Isso geralmente acontece quando diferentes desenvolvedores alteram a mesma linha de código ou seções próximas. Esses conflitos precisam ser resolvidos manualmente para que a mesclagem possa ser concluída.
    
4. **Cherry Picking**: É uma técnica no Git que permite selecionar e aplicar commits específicos de uma branch em outra, sem precisar mesclar toda a branch. Isso é útil quando você precisa aplicar uma correção ou funcionalidade específica sem trazer todas as mudanças da branch de origem.
    
5. **Stash**: Um comando do Git que salva temporariamente as mudanças não comitadas em uma pilha de armazenamento, permitindo que você troque de branch sem perder o progresso atual. Posteriormente, essas mudanças podem ser recuperadas e aplicadas novamente com o comando `git stash apply`.
    

### **Practices (Práticas)**

1. **Unit Tests (Testes Unitários)**: São testes automatizados que verificam o comportamento de uma pequena parte do código, como uma função ou método específico, isoladamente do restante do sistema. Testes unitários são fundamentais para garantir que cada unidade de código funcione corretamente.
    
2. **Smoke Tests (Testes de Fumaça)**: São testes rápidos e abrangentes que verificam se as principais funcionalidades do software estão funcionando após uma nova compilação ou integração. O objetivo é garantir que o software "não pegue fogo" ao ser executado, antes de passar por testes mais aprofundados.
    
3. **Load Tests (Testes de Carga)**: São testes que avaliam o desempenho do software sob uma carga significativa de uso, simulando cenários de uso intenso para verificar como o sistema se comporta em termos de velocidade, estabilidade e capacidade.
    
4. **Dependency Injection (Injeção de Dependências)**: É um padrão de design em que objetos recebem suas dependências de fora, em vez de criarem-nas diretamente. Isso facilita o teste e a manutenção do código, pois as dependências podem ser substituídas ou modificadas sem alterar o objeto que as utiliza.
    
5. **Immutability (Imutabilidade)**: Refere-se à prática de criar objetos ou estados que não podem ser modificados após sua criação. Em vez de alterar o estado de um objeto, uma nova instância é criada com o novo estado. A imutabilidade ajuda a evitar efeitos colaterais inesperados, facilitando o rastreamento de mudanças e a depuração do código.
    
### **Principles (Princípios)**

1. **DRY (Don't Repeat Yourself)**: É um princípio de desenvolvimento de software que recomenda evitar a repetição de código. A ideia é que cada parte da lógica do sistema deve ser implementada apenas uma vez, de modo que mudanças possam ser feitas em um único lugar, reduzindo a probabilidade de erros e facilitando a manutenção.
    
2. **KISS (Keep It Simple, Stupid)**: Este princípio incentiva a simplicidade no design e na implementação do software. A ideia é que sistemas simples são mais fáceis de entender, manter e testar. Complexidade desnecessária deve ser evitada para minimizar o risco de erros e problemas.
    
3. **YAGNI (You Aren't Gonna Need It)**: Este princípio sugere que você não deve implementar funcionalidades que acha que pode precisar no futuro, mas que ainda não são necessárias. A ideia é focar apenas no que é necessário agora, evitando desperdício de tempo e recursos em funcionalidades que podem nunca ser usadas.
    

### **Java**

1. **JUnit**: É uma biblioteca de testes unitários para Java, amplamente utilizada para escrever e rodar testes automatizados. Com JUnit, os desenvolvedores podem criar testes para verificar se as partes do código estão funcionando conforme esperado, e esses testes podem ser executados automaticamente para detectar problemas.
    
2. **Mockito**: É uma biblioteca de simulação (mocking) para Java, que permite criar objetos simulados (mocks) para testar a interação entre diferentes partes do código. Com Mockito, você pode testar unidades de código em isolamento, simulando o comportamento de suas dependências.
    
3. **Parametrized Tests (Testes Parametrizados)**: São testes unitários que permitem rodar o mesmo teste várias vezes com diferentes conjuntos de dados. Em vez de escrever múltiplos testes para diferentes casos, você define os dados de entrada e as expectativas, e o teste é executado para cada conjunto de parâmetros.
    
4. **Spring Boot**: É um framework que simplifica o desenvolvimento de aplicações Java baseadas em Spring. Ele fornece uma configuração automática e ferramentas para criar rapidamente aplicativos prontos para produção, sem a necessidade de muita configuração manual.
    
5. **Microbenchmarking**: Refere-se à prática de medir o desempenho de pequenos pedaços de código, como métodos ou funções individuais, para avaliar sua eficiência. Em Java, a ferramenta mais comum para microbenchmarking é o JMH (Java Microbenchmark Harness), que permite criar benchmarks precisos e confiáveis.
    
6. **Gradle**: É uma ferramenta de automação de build para projetos Java (e outras linguagens). Gradle permite compilar, testar, empacotar e distribuir o software de forma eficiente, utilizando um sistema de build declarativo e altamente configurável. É conhecido por sua flexibilidade e desempenho superior em comparação com outras ferramentas de build, como o Maven.
    

### **Modern Java (Java Moderno)**

1. **Sealed Classes**: São uma funcionalidade introduzida no Java 15 que permite restringir quais classes podem estender ou implementar uma classe ou interface. Uma classe selada (sealed) define explicitamente as subclasses que são permitidas. Isso é útil para controlar a herança e garantir que apenas subclasses específicas possam ser criadas, o que facilita a manutenção e a segurança do código.
    
2. **Records**: Introduzidos no Java 14, os `records` são uma nova forma de declarar classes imutáveis que são usados principalmente para armazenar dados. Eles simplificam a criação de classes que apenas carregam dados, sem a necessidade de escrever muito código padrão (boilerplate), como construtores, `equals`, `hashCode` e `toString`.
    
3. **Pattern Matching (Correspondência de Padrões)**: É uma funcionalidade que permite simplificar a lógica condicional e a extração de componentes de objetos. No Java moderno, o pattern matching foi introduzido para `instanceof`, permitindo que o tipo de um objeto seja verificado e, simultaneamente, atribuído a uma variável local, simplificando o código e melhorando a legibilidade.
    
### **Tools (Ferramentas)**

1. **Grafana K6**: K6 é uma ferramenta de teste de carga e desempenho de código aberto, originalmente desenvolvida pela Grafana Labs. Ela permite que os desenvolvedores criem scripts de teste de carga usando JavaScript para simular o comportamento de usuários em um sistema, medindo seu desempenho sob condições de estresse. É frequentemente usada para identificar gargalos de desempenho antes de uma aplicação ser lançada em produção.
    
2. **Postman**: É uma ferramenta amplamente utilizada para testar APIs. Com Postman, os desenvolvedores podem enviar solicitações HTTP para uma API e verificar as respostas, facilitando o processo de desenvolvimento e depuração. Ele suporta diferentes métodos HTTP (GET, POST, PUT, DELETE, etc.) e permite a criação de coleções de testes automatizados.
    
3. **Insomnia**: É uma ferramenta similar ao Postman, usada para testar APIs. Insomnia oferece uma interface simples e intuitiva para enviar solicitações HTTP e visualizar as respostas. É muito apreciada por desenvolvedores por sua simplicidade e eficiência no desenvolvimento e teste de APIs RESTful.
    
4. **Testcontainers**: É uma biblioteca Java que oferece suporte para testes de integração com bancos de dados, microsserviços, entre outros, usando contêineres Docker. Com Testcontainers, você pode criar e gerenciar contêineres durante os testes, garantindo um ambiente de teste isolado e consistente.
    
5. **IntelliJ IDEA**: É um dos IDEs (Integrated Development Environment) mais populares para desenvolvimento em Java e outras linguagens. O IntelliJ IDEA oferece uma ampla gama de funcionalidades, como análise de código, refatoração, integração com sistemas de controle de versão e suporte a frameworks populares como Spring, Hibernate e muitos outros. Ele é conhecido por sua interface intuitiva e por melhorar a produtividade dos desenvolvedores.
    

### **Miscellaneous (Diversos)**

1. **Mockoon**: É uma ferramenta que permite simular APIs locais para teste e desenvolvimento. Com Mockoon, você pode criar rapidamente servidores mock que retornam respostas personalizadas para diferentes endpoints, facilitando o desenvolvimento de front-ends ou testes quando a API real ainda não está disponível.
    
2. **Azurite**: É uma emulador local para os serviços de armazenamento do Azure (Blobs, Queues, Tables). Ele permite que os desenvolvedores simulem os serviços de armazenamento do Azure em suas máquinas locais, facilitando o desenvolvimento e teste de aplicações que interagem com o Azure sem a necessidade de uma conta na nuvem ou de conexão com a internet.
    
3. **Regular Expressions (Expressões Regulares)**: São sequências de caracteres que formam um padrão de pesquisa, usadas principalmente para busca e manipulação de texto. Expressões regulares são ferramentas poderosas para validar, extrair e substituir padrões em strings, sendo amplamente utilizadas em diversas linguagens de programação.
    
4. **JWT (JSON Web Token)**: JWT é um padrão para a criação de tokens que podem ser usados para autenticação e troca de informações seguras entre diferentes partes. Um JWT é um token compacto e autossuficiente que contém todas as informações necessárias para verificar a identidade de um usuário e suas permissões, frequentemente usado em sistemas de autenticação web.
    
5. **OWASP (Open Web Application Security Project)**: OWASP é uma comunidade online dedicada à segurança de software. Eles oferecem uma variedade de ferramentas, documentos e recursos que ajudam a melhorar a segurança de aplicativos. Um dos recursos mais conhecidos é o OWASP Top 10, uma lista das dez vulnerabilidades de segurança mais críticas em aplicações web.
    
### **Documentation as Code (Documentação como Código)**

O conceito de "Documentação como Código" refere-se à prática de tratar a documentação de software da mesma forma que o código-fonte, ou seja, ela é escrita, versionada, revisada e mantida usando as mesmas ferramentas e práticas de desenvolvimento de software. Isso garante que a documentação esteja sempre atualizada e em sintonia com o código, além de facilitar a colaboração entre os desenvolvedores. Abaixo estão algumas ferramentas e padrões relacionados a esse conceito:

1. **OpenAPI Standard**: O OpenAPI é uma especificação para a criação de documentações de APIs RESTful. Ele permite que desenvolvedores descrevam todos os aspectos de uma API, como endpoints, métodos HTTP suportados, parâmetros e esquemas de resposta, em um formato padronizado (geralmente YAML ou JSON). Documentação gerada com OpenAPI pode ser automaticamente utilizada para gerar código cliente, servidores mock e documentação interativa.
    
2. **AsyncAPI Standard**: AsyncAPI é uma especificação similar ao OpenAPI, mas voltada para APIs assíncronas, como aquelas baseadas em eventos e mensageria (por exemplo, Kafka, MQTT). Ela fornece uma forma padronizada de documentar eventos, canais de comunicação, mensagens e schemas, permitindo a criação de documentações consistentes e interativas para sistemas baseados em eventos.
    
3. **Markdown**: Markdown é uma linguagem de marcação leve que permite criar documentos formatados de maneira simples e legível. É amplamente utilizado para escrever documentação em repositórios de código, como arquivos `README.md`, e é compatível com várias ferramentas de documentação como code, wikis e geradores de sites estáticos.
    
4. **PlantUML**: PlantUML é uma ferramenta que permite a criação de diagramas a partir de uma sintaxe simples de texto. Usando PlantUML, você pode gerar automaticamente diagramas UML (como diagramas de classes, sequências, casos de uso, etc.) diretamente no código-fonte, facilitando a criação e manutenção de documentação visual que acompanha as mudanças no código.
    
5. **Mermaid JS**: Mermaid é uma ferramenta similar ao PlantUML, mas voltada para ser usada em Markdown e outros documentos de texto. Mermaid permite gerar uma variedade de diagramas (fluxogramas, gráficos de Gantt, diagramas de sequência, etc.) usando uma sintaxe simples em texto, que pode ser embutida em documentos Markdown ou visualizada diretamente em navegadores compatíveis.
    
### **Visual Documentation (Documentação Visual)**

A documentação visual refere-se à prática de representar graficamente a arquitetura, o design e o fluxo de sistemas de software. Essa abordagem facilita a compreensão de estruturas complexas e o alinhamento entre equipes técnicas e não técnicas. Abaixo estão algumas ferramentas e métodos populares para a criação de documentação visual:

1. **C4 Model (Modelo C4)**: O Modelo C4 é uma abordagem hierárquica para descrever a arquitetura de sistemas de software de maneira clara e estruturada. Ele divide a documentação em quatro níveis de abstração:
    
    - **Context Diagram (Diagrama de Contexto)**: Mostra o sistema em questão e como ele interage com usuários e outros sistemas. É uma visão de alto nível que foca nas relações externas.
        
    - **Container Diagram (Diagrama de Contêineres)**: Detalha os principais contêineres de software (como aplicações, bancos de dados, serviços) dentro do sistema, e como eles se comunicam entre si. Um contêiner pode ser uma aplicação web, uma API, um banco de dados, etc.
        
    - **Component Diagram (Diagrama de Componentes)**: Explora o interior dos contêineres, detalhando os componentes de software individuais e suas interações.
        
    - **Code (ou Class) Diagram (Diagrama de Código ou Classes)**: Foca nos detalhes de implementação, mostrando classes, interfaces, métodos e relacionamentos entre eles. Este nível pode ser opcional dependendo do nível de detalhe necessário.
        
    
    O C4 Model é amplamente utilizado por arquitetos de software e desenvolvedores para comunicar de maneira clara a estrutura e a interação dos sistemas em diferentes níveis de abstração.
    
2. **Sequence Diagram (Diagrama de Sequência)**: O Diagrama de Sequência é um tipo de diagrama UML (Unified Modeling Language) que mostra como os objetos em um sistema interagem uns com os outros em uma sequência de mensagens ao longo do tempo. Ele é particularmente útil para ilustrar fluxos de processos e o comportamento dinâmico de sistemas, mostrando:
    
    - **Objetos ou componentes envolvidos**: Representados como linhas de vida verticais.
    - **Mensagens trocadas entre eles**: Representadas como setas horizontais entre as linhas de vida.
    - **Ordem das interações**: Mostrada de cima para baixo, onde as mensagens são enviadas e recebidas em sequência temporal.
    
    Diagramas de Sequência são muito úteis para detalhar fluxos específicos dentro de um sistema, como uma transação de banco de dados, uma chamada de API, ou a interação entre diferentes serviços em uma arquitetura de microsserviços.
    
### **Azure Platform (Plataforma Azure)**

1. **Cosmos DB**: O Azure Cosmos DB é um banco de dados NoSQL distribuído globalmente, projetado para escalar horizontalmente e oferecer alta disponibilidade, baixa latência e consistência garantida. Ele suporta múltiplos modelos de dados, como chave-valor, documentos, colunas e grafos, e é ideal para aplicações que precisam de um banco de dados globalmente distribuído.
    
2. **Functions (Funções do Azure)**: O Azure Functions é um serviço de computação sem servidor (serverless) que permite executar pequenas partes de código (funções) em resposta a eventos, sem a necessidade de gerenciar a infraestrutura. É usado para automatizar tarefas, processar dados, executar APIs e muito mais.
    
3. **Application Configuration**: O Azure App Configuration é um serviço que centraliza a gestão de configurações e parâmetros para aplicações. Ele permite gerenciar configurações de maneira segura e eficiente, suportando a segmentação de configurações por ambiente (desenvolvimento, produção, etc.) e facilitando a implementação de mudanças sem a necessidade de redeploys.
    
4. **Application Insights**: O Azure Application Insights é um serviço de monitoramento e telemetria que permite rastrear o desempenho e a utilização de aplicativos em tempo real. Ele coleta dados como métricas, logs e rastreamentos, ajudando a identificar e diagnosticar problemas em aplicações em execução no Azure ou em outras plataformas.
    
5. **Key Vault**: O Azure Key Vault é um serviço para armazenar e gerenciar segredos, chaves de criptografia e certificados digitalmente. Ele oferece uma maneira segura de proteger informações sensíveis, como chaves de API, senhas e outros dados confidenciais, garantindo que apenas aplicações autorizadas possam acessá-los.
    
6. **API Management**: O Azure API Management é um serviço que permite publicar, proteger, transformar, manter e monitorar APIs. Ele facilita o gerenciamento de APIs tanto internas quanto externas, oferecendo controle de acesso, análise de uso, versionamento e políticas de segurança.
    
7. **Storage Account**: O Azure Storage Account é um serviço que oferece armazenamento em nuvem altamente escalável e durável para diferentes tipos de dados, como blobs (arquivos), tabelas (dados estruturados), filas (mensageria) e discos (armazenamento persistente para VMs). Ele é usado para armazenar grandes volumes de dados de maneira confiável.
    
8. **Container Apps**: O Azure Container Apps é um serviço gerenciado para a execução de aplicações em contêineres sem a necessidade de gerenciar infraestrutura. Ele é projetado para escalar automaticamente com base na carga e permite a execução de aplicativos baseados em microserviços, eventos e tarefas em contêineres de forma eficiente.
    

### **Containerization (Conteinerização)**

1. **Docker**: Docker é uma plataforma que permite empacotar, distribuir e executar aplicações em contêineres. Um contêiner Docker encapsula uma aplicação e todas as suas dependências, garantindo que ela possa ser executada consistentemente em qualquer ambiente, desde o desenvolvimento até a produção.
    
2. **Kubernetes**: Kubernetes é uma plataforma de orquestração de contêineres que automatiza o gerenciamento, a escalabilidade e a implantação de aplicações em contêineres. Ele permite que aplicações sejam escaladas horizontalmente, garante a alta disponibilidade e simplifica o gerenciamento de ambientes complexos de microserviços.
    

### **Continuous Integration & Deployment (Integração e Implantação Contínuas)**

1. **Azure Pipelines**: O Azure Pipelines é uma ferramenta de CI/CD (Continuous Integration/Continuous Deployment) que automatiza a construção, teste e implantação de código em múltiplos ambientes. Ele suporta a integração com diversos repositórios de código e permite criar pipelines complexos para automação de todo o ciclo de vida de desenvolvimento.
    
2. **GitHub Actions**: GitHub Actions é uma plataforma de automação integrada ao GitHub que permite criar fluxos de trabalho automáticos para construção, teste e implantação de código. Com ela, é possível definir pipelines de CI/CD diretamente nos repositórios do GitHub, aproveitando a integração nativa com outras funcionalidades do GitHub.
    
3. **Azure Releases**: Parte do Azure DevOps, Azure Releases é uma ferramenta para gerenciar o processo de implantação contínua de aplicações. Ela permite definir pipelines de lançamento para implantar automaticamente versões de software em vários ambientes, com suporte a aprovações manuais e automáticas e diferentes etapas de implantação.
    

### **Quality Gates (Portões de Qualidade)**

1. **PMD**: PMD é uma ferramenta de análise estática de código que verifica o código-fonte em busca de padrões comuns que podem indicar bugs ou má qualidade. Ele suporta várias linguagens de programação e ajuda a identificar problemas como código duplicado, práticas de codificação ruins e problemas de desempenho.
    
2. **CheckStyle**: CheckStyle é uma ferramenta de análise de código que verifica o código Java em relação a convenções de estilo e padrões de codificação. Ele ajuda a garantir que o código esteja em conformidade com as diretrizes estabelecidas, promovendo um código mais limpo e fácil de manter.
    
3. **SpotBugs**: SpotBugs é uma ferramenta de análise estática de código para Java que identifica bugs e vulnerabilidades em código-fonte. Ele analisa bytecode para detectar possíveis problemas, como uso incorreto de APIs, nulidade, concorrência e outros tipos de erros comuns.
    
4. **Spectral Lint**: Spectral é uma ferramenta de linting que verifica e valida arquivos de configuração e especificações, como OpenAPI, AsyncAPI e JSON Schema. Ele ajuda a garantir que as definições de API sigam padrões específicos, evitando erros de configuração e promovendo boas práticas de documentação.
    
5. **Snyk**: Snyk é uma ferramenta de segurança focada em identificar e corrigir vulnerabilidades em dependências de código aberto, contêineres e infraestrutura como código (IaC). Ele se integra ao pipeline de CI/CD para garantir que o código esteja protegido contra vulnerabilidades conhecidas antes de ser implantado.
    

