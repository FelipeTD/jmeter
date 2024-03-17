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
- Simple Controller
  - Utilizado para agrupar os requests
  - Login
  - Registration
  - Procurar um voo
  - O Simple Controller não tem funcionalidade
  - Ele serve somente para organizar as requisições que fazemos em grupos
- Modular Controller
  - Controle utilizado para executar fragmentos definidos no JMeter
  - Por exemplo o Simple Controller
- Test Fragment
  - É outra opção ao Simple Controller
  - Tem a mesma função de ser utilizado no Modular Controller
- Include Controller
  - Salve a requisição como um loginTF.jmx
  - Clique com o botão direito na requisição para fazer isso
  - Com o include controller consegue utilizar esse arquivo

### Random & Random Order Controllers in JMeter
- Random Controller
  - Executa um dos requests que estão dentro do Random Controller
- Random Order Controller
  - Executa os requests que estão dentro do Random Order Controller numa ordem aleatória

### Interleave Controller
- Interleave Controller
  - Trabalha da mesma forma que o Random Controller, mas não deixa repetir a opção em multiplas requisições

### Logic Controllers- Throughput Controller | How to Build a Distributed Load Test
- Como fazer os nossos Samplers executarem com uma porcentagem definida de execução
- Como usar Throughput Controller para fazer isso
- Threads (usuários virtuais) - 10
- Web Application
  - Home Page 20% - 2
  - Welcome, Page 30% - 3
  - Register Page 50% - 5
- São colocados em um Thread Group
- Consegue colocar as requisições dentro do Throughput Controller
- Define a quantidade por número total de execuções ou porcentagem

### Overview on Performance Testing
- O que é teste de desempenho
  - É um teste não funcional para se ter certeza que o programa irá funcionar corretamente
  - O objetivo não é encontrar erros, mas evitar gargalos
  - O foco do teste de desempenho é:
    - Verificar a velocidade
    - Verificar a escalabilidade
    - Verificar a estabilidade
  - Também é chamado de `Perf Testing`
- Porque realizar testes de desempenho
  - Garantir que o programa irá funcionar corretamente sem ficar lento ou instável quando vários utilizadores o utilizarem
  - A lentidão pode deixar o programa com uma má reputação
- Categorias de teste de desempenho
  - Load Testing
    - Testar se o carregamento da aplicação está rápido
  - Stress Testing
    - Realizar várias chamadas para entender o limite de requisições da aplicação
  - Endurance Testing
    - Testa se a aplicação consegue atender as requisições por um longo periodo de tempo
  - Spike Testing
    - Testa picos de carga nas requisições dos utilizadores
  - Volume Testing
    - Testar como o programa se comporta com muitos dados no banco de dados
- Problemas comuns em teste de desempenho
  - Long Load Time
    - Deve manter o carregamento inicial em segundos se possível
  - Poor Response Time
    - A resposta as requisições dos utilizadores deve novamente ser muito rápida
  - Poor Scalability
    - Quando a aplicação não consegue sustentar a quantidade de utilizadores
  - Bottlenecking
    - CPU utilization
    - Memory utilization
    - Network utilization
    - Operating System limitations
    - Disk usage
- Processo de teste de desempenho
  - Identificar o ambiente de testes
    - É importante saber a configuração que será utilizada para rodar o programa
  - Projetar e desenhar os testes
  - Identificar o critério de performance aceitável
  - Configurar o ambiente de testes
  - Implementar o ambiente de testes
  - Executar os testes
  - Analisar e reportar os resultados
- Metricas e parametros monitorados
  - Processor Usage 
    - Tempo de utilização do processador
  - Memory use
    - Quantidade de memória utilizada
  - Disk time
    - Tempo para ler ou escrever uma requisição no disco
  - Bandwidth
    - Bits por segundo usados pela ‘internet’
  - Private bytes
    - Quantidade de ‘bytes’ alocados e não podem ser utilizados por outro processo
    - Isso evita estouro de memória
  - Committed memory
    - Quantidade de memória virtual utilizada
  - Response time
    - Tempo de resposta de uma requisição
  - Throughput
    - Quantidade de requisições por segundo
  - Amount of connection pooling
    - A quantidade de requisições atendidas por `pool` de conexão
    - Quanto maior a quantidade atendida melhor o resultado
  - Maximum active sessions
    - Quantidade máxima de sessões ativas
  - Hit ratios
    - Quantidade de requisições atendidas por `cache` de dados ao inves de acesso ao banco de dados
  - Hits per second
    - Quantidade de chamadas com exito durante 1 segundo de teste de desempenho
  - Thread Counts
    - Quantidade de threads rodando e ativas
- Exemplo de teste de desempenho
  - Tempo de resposta não pode ser superior há 4 segundos quando 1000 utilizadores acessarem o `site` ao mesmo tempo
  - Verificar se o tempo de resposta da aplicação está aceitável quando a conexão estiver lenta
  - Verificar o número máximo de utilizadores que a aplicação suporta antes de cair
  - Verificar a execução do banco de dados quando 500 registros são lidos ou escritos simultaneamente
  - Verificar a CPU e memória usados quando a aplicação está num pico de utilização
  - Verificar o tempo de reposta quando a aplicaçãoe está com uma carga baixa, média e pesada
- Ferramentas de teste de desempenho
  - Apache JMeter
  - NeoLoad
  - Micro Focus LoadRunner
  - SmartBear LoadNinja

### Parameterization | CSV Dataset Config | User Defined Variables
- JMeter internal parameters
- Read Parameters values from CSV
- É possível ler parametros definidos internamente no JMeter
  - Add -> Config Element -> User defined variables
- Também é possível definir parametros dentro de um arquivo CSV
  - Add -> Config Element -> CSV Data Set Config

### Correlation 
- O que é correlation
  - É o processo de pegar um valor de um response e utilizar em outro request
  - É feito em tempo de execução por isso é chamado referência dinâmica
- Por que é requirido
  - Nos testes as vezes é necessário pegar valores de requisições anteriores para conseguir realizar outras requisições
  - Um exemplo é realizar o ‘login’ num sistema para conseguir realizar outras requisições
- Como usar o Regular Expression Extractor
  - Crie um `Test Plan` onde quer utilizar essa referência dinâmica
  - Adicione uma `Regular Expression Extractor` no passo onde essa referência precisa ser extraída
    - Add -> Post Processors -> Regular Expression Extractor
  - Referencie o valor extraído no passo seguinte
  - Execute e valide
  - Pode usar RegExp Tester no View Results Tree para testar expressões diretamente no response data

### If and While Controller
- Para utilizar o IF desmarque a opção `Interpret condition as variable expression?`
- No caso do While Controller pode utilizar uma variavel pré-definida
- Ficaria com o comando abaixo:
  - ${__groovy((vars.get('__jm__While Controller__idx') as int) < 3,)}

### Switch Controller e Transaction Controller
- Baseado no switch case
  - Percorre uma lista de condições e se nenhuma atender executa o padrão
- Foi utilizado um BeanShell Sampler para criar as condições
- O Http Request é executado dentro de um Transaction Controller
- Os países estão dentro de um arquivo Nations.txt
- A Thread é executada 11 vezes pegando os 11 países
- O BeanShell Sampler define qual o valor que será utilizado no switch
- O Switch pega o valor definido e chama a URL do valor

### For Each Controller
- A requisição Inicial retorna uma lista de opções
- Criamos uma expressão regular para pegar os nomes das cidades da lista retornada
- No ForEach utilizamos o resultado da expressão regular e mostramos o nome de cada cidade
- Também foi mostrado o indice de cada posição da lista de cidades

### Once Only Controller
- Utilizado para executar somente uma vez
- Pode ser usado no momento do ‘login’ para pegar o token de acesso necessário para chamar as outras funções do sistema

### Critical Section Controller
- Utilizado quando quer que as requisições sejam feitas uma por uma
- As threads no JMeter são executadas ao mesmo tempo
- Ao usar o Critical Section Controller elas serão executadas uma por vez
- Lembrando que precisa configurar 5 utilizadores para serem executados um por vez
- Se colocar para a thread se repetir 5 vezes o Critical Section Controller não faz sentido

### Runtime Controller
- Define a quantidade de tempo que uma requisição será feita
- O Http Request que você colocar dentro do Runtime Controller será feita requisições até acabar o tempo definido

### Links e referências
- Site do JMeter
  - https://jmeter.apache.org/
- JMeter Tutorial
  - https://www.youtube.com/watch?v=817zU_bXh9Y&list=PLUDwpEzHYYLs33uFHeIJo-6eU92IoiMZ7
- While Loop in JMeter | How to Use While Controller in JMeter
  - https://www.youtube.com/watch?v=2uNuLuKoBn4
- Switch Controller in Jmeter
  - https://www.youtube.com/watch?v=ZYeS1nOcK6U
- How to use for each controller in JMeter - JMeter Logic Controllers
  - https://www.youtube.com/watch?v=tQQ9KSM7xYw
- JMeter Performance Testing Tutorial 25 - Simple and Once Controller with example in JMeter
  - https://www.youtube.com/watch?v=jCzX2xgsdoc
- JMeter 2.12 - Critical Section Controller
  - https://www.youtube.com/watch?v=HVVyTvoTmdc