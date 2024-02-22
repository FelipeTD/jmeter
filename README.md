# JMeter
- Projeto para aprender sobre JMeter

## Informações

### Apache JMeter
- É um `software` (100%) código aberto feito em Java utilizado para testar o desempenho da aplicação
- Foi originalmente feito para testar aplicaçãoes `web`, mas foi expandido para outros testes

### O que posso fazer com ele?
- Testar diferentes aplicações como:
  - Web - HTTP, HTTPS (Java, NodeJS, PHP, ASP.NET)
  - SOAP / REST Webservices
  - FTP
  - Database via JDBC
  - LDAP
  - Message-oriented middleware (MOM) via JMS
  - Mail - SMTP(S), POP3(S) and IMAP(S)
  - Native commands or shell scripts
  - TCP
  - Java Objects
- HTML report
- Extração de dados via HTML, JSON, XML ou qualquer formato de texto
- 100% Java
- Multi-threading
- Cache e analise offline
- Fácil de utilizar com integração continua com maven, gradle e jenkins

### Como eu faço isso?
- Usando JMeter para entender como usar ele
  - https://jmeter.apache.org/usermanual/index.html
- Referência de componente para informações sobre cada elemento de teste
  - https://jmeter.apache.org/usermanual/component_reference.html
- Funções de referência para detalhes e exemplos para cada função
  - https://jmeter.apache.org/usermanual/functions.html
- Referências de propriedade para entender todas as propriedades que podem ser customizadas 
  - https://jmeter.apache.org/usermanual/properties_reference.html
- Javadoc API documentation
  - https://jmeter.apache.org/api/index.html
- JMeter FAQ (Wiki)
  - https://cwiki.apache.org/confluence/display/JMETER/JMeterFAQ
- JMeter Wiki
  - https://cwiki.apache.org/confluence/display/JMETER/Home
- Construir JMeter e Add-Ons para uso avançado
  - https://jmeter.apache.org/building.html

### JMeter não é um navegador
- Parece com um navegador, mas não tem todas as funcionalidades de um navegador

### Tutoriais
- Distributed Testing
  - https://jmeter.apache.org/usermanual/jmeter_distributed_testing_step_by_step.html
- Recording Tests
  - https://jmeter.apache.org/usermanual/jmeter_proxy_step_by_step.html
- JUnit Sampler
  - https://jmeter.apache.org/usermanual/junitsampler_tutorial.html
- Access Log Sampler
  - https://jmeter.apache.org/usermanual/jmeter_accesslog_sampler_step_by_step.html
- Extending JMeter
  - https://jmeter.apache.org/usermanual/jmeter_tutorial.html

### Mais informações
- Changes List
  - https://jmeter.apache.org/changes.html
- Read about existing Issues (Bugs or Enhancements) or reporting new ones (please do it !)
  - https://jmeter.apache.org/issues.html
- License
  - https://www.apache.org/licenses/
- Mailing Lists
  - https://jmeter.apache.org/mail.html
- Source Repositories
  - https://jmeter.apache.org/svnindex.html
- Contributors
  - https://cwiki.apache.org/confluence/display/JMETER/JMeterCommitters

## Tutorial do youtube sobre JMeter

### Instalação
- Basta ir no site do JMeter e baixa o .zip
  - Descompactar o zip e executar o arquivo jmeter.bat dentro da pasta bin

### Elementos básicos do JMeter
- Thread Group
  - Define uma quantidade de chamadas a serem realizadas
  - É uma simulação de utilizadores utilizando o sistema
- Samplers
  - É um tipo diferente de requisição feita no Thread Group
- Listeners
  - Mostram o resultado dos testes
  - Esses resultados podem ser vistos em 4 tipos diferentes
    - Resultado em gráfico
    - Resultado em árvore
    - Resultado em tabela
    - Resultado em logs
- Configuration
  - Configura valor padrão e variáveis para serem utilizadas pelos ‘samplers’ 

### Creating First Test In JMeter
- Link https://www.youtube.com/watch?v=nUu7rq1097A&list=PLUDwpEzHYYLs33uFHeIJo-6eU92IoiMZ7&index=5
- Step 1 > Start JMeter
- Step 2 > Create a TestPlan
  - Contém todos os elementos do JMeter
- Step 3 > Create a Thread Group (Users)
  - Botão direito no Test Plan -> Add -> Thread (users) -> Thread Group
  - Pode configurar
    - Number of Threads (users) -> Número de usuários
    - Ramp-up period (seconds) -> Tempo para cada requisição
    - Loop Count -> Quantidade de vezes que vai ser executado
- Step 4 > Add a Sampler (Http)
  - Botão direito no users -> Add -> Sampler -> Http Request
    - Server name or IP
      - Endereço a ser testado sem o https://
    - Path
      - /
      - Pode ser adiciona o path que deseja testar também
- Step 5 > Add Listeners
  - Botão direito no users -> Add -> Listener -> View Result Tree
  - Botão direito no users -> Add -> Listener -> View Result in Table
- Step 6 > Run Test Plan
  - Apertar o botão verde na parte de cima do JMeter
- Step 7 > Save Test Plan
  - Salvar o teste num arquivo `.jmx`

### Timers in JMeter
- O que são `Timers`?
- JMeter faz requisições sem aplicar nenhum delay entre as requisições
- Se você realizar testes de estresse no servidor sem nenhum delay vai acontecer um `overload`
- Então não será possível simular um cenário realista
- JMeter `Timers` são a solução para todos esses problemas
- `Timer` pode ser aplicado entre cada requisição entre um `Sampler`e um `Request`
- Tipos de `Timers`
  - Constant Timers
  - Uniform Random Timer
  - Gaussian Random Timer
  - BeanShell Timer
  - BSF Timer
  - JSR223 Timer
- Exemplo
  - Botão direito em Test Plan -> Add -> Threads (users) -> Thread Group
  - Botão direito em Thread Group -> Add -> Sampler -> Http Request
  - Copiar e colar 2x o Http Request criado
  - Botão direito em Thread Group -> Add -> Listener -> View Results in Table
  - Botão direito em Thread Group -> Add -> Timer -> Constant Timer
  - Pode ser adicionado no Http Request também
- Exemplo Uniform Random Timer
  - Botão direito em Thread Group -> Add -> Timer -> Uniform Random Timer
  - Random Delay Max
  - Constant Delay Offset
  - Formula
    - 0.X * Random Delay Max + Constant Delay Offset
    - Exemplo
    - 0.X * 100 + 0
    - 0 e 99 ms
- Gaussian Random Timer
  - Define um tempo randomico para cada requisição de utilizador
- BeanShell Timer
  - Define um tempo para cada requisição de utilizador
- BSF Timer
  - Utiliza um `script` BSF para definir o tempo entre cada requisição
- JSR223 Timer
  - Utiliza um `script` JSR223 para definir o tempo entre cada requisição

### Logic Controllers in JMeter
- Logic Controller permite você lidar com a ordem de processamento de samplers e requests
- Decidem quando e como será enviado uma requisição ao servidor ‘web’
- JMeter oferece vários controladores lógicos:
  - Critical Section Controller
  - ForEach Controller
  - If Controller
  - Include Controller
  - Interleave Controller
  - Loop Controller
  - Module Controller
  - Once Only Controller
  - Random Controller
  - Random Order Controller
  - Recording Controller
  - Runtime Controller
  - Simple Controller
  - Switch Controller
  - Throughput Controller
  - Transaction Controller
  - While Controller
- Loop Controller
  - Faz uma requisição ser enviada ao servidor uma quantidade de vezes ou para sempre
  - Botão direto em Test Plan -> Add -> Threads (users) -> Thread Group
  - Botão direito em Thread Group -> Add -> Sampler -> Http Request
    - Criar um para index www.pavanonlinetrainings.com
  - Copiar e colar Request
    - Criar um para Blog www.pavantestingtools.com
  - Copiar e colar Request
    - Criar um para Teste 
      - Server www.pavantestingtools.com
      - Path /p/manual-testing-project.html
  - Botão direito em Thread Group -> Add -> Listener -> View Results Tree
  - Botão direito em Thread Group -> Add -> Logic Controller -> Loop Controller
  - Arraste o Index para dentro do Loop Controller
    - O index será executado 5 vezes
    - Se na Thread Group você colocar para rodar 2 vezes
    - O index será executado 5 x 2 vezes
  - Se o Listener for colocado dentro do Loop Controler ele irá exibir somente as chamadas do Index
  - Isso porque ele exibe somente o que está dentro do Loop Controller

### Recording Controller in JMeter | Non Test Elements | Recording script
- Passo 1 
  - Adicionando NonTestElement -> Http Recording
- Passo 2 
  - Definir proxy no navegador
- Passo 3 
  - Começando o recording em um Recording Controller diferente
- Passo 4 
  - Começando cenário de Recording
- Passo 5 
  - Stop Recording and Save
- Passo 1
  - Add Thread Group
  - Test Plan -> Add -> Non-Test Elements -> HTTP(s) Test Script Recorder
  - Thread Group -> Add -> Logic Controller -> Recording Controller
    - Renomear para LoginPage
  - Thread Group -> Add -> Logic Controller -> Recording Controller
    - Renomear para Registration
- Passo 2
  - Abrir navegador
  - Três pontos -> Definições
  - Sistema ≥ Abrir definições do proxy do seu computador
  - Também pode seguir o caminho do windows -> pesquisa -> Propriedades da internet -> Conexões -> Configurações da LAN
  - Selecionar opção
    - Usar um servidor proxy para a rede local
      - Endereço: localhost
- Passo 3
  - Target Controller deve ser LoginPage
  - Clicar em Start
  - Após realizar a requisição clicar em ‘stop’
  - Não funcionou muito bem
  - Preciso procurar outro exemplo de utilização
- Adicionar um listener no Test Plan -> View Results Tree
- Pelo que entendi essa opção seria para não precisa configurar os controllers
- O Recording Controller cria todas as requisições que uma página faz para realizar a chamada
- Então pela lógica funcionou corretamente
- A única parte que não entendi é porque se não configurar o LAN não funciona

### Simple, Module and Include Controllers | Test Fragment in JMeter

### Links e referências
- Site do JMeter
  - https://jmeter.apache.org/
- JMeter Tutorial
  - https://www.youtube.com/watch?v=817zU_bXh9Y&list=PLUDwpEzHYYLs33uFHeIJo-6eU92IoiMZ7