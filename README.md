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

### Tutorial 5 - Creating First Test In JMeter
- Link https://www.youtube.com/watch?v=nUu7rq1097A&list=PLUDwpEzHYYLs33uFHeIJo-6eU92IoiMZ7&index=5
- Step 1 > Start JMeter
- Step 2 > Create a TestPlan
- Step 3 > Create a Thread Group (Users)
- Step 4 > Add a Sampler (Http)
- Step 5 > Add Listeners
- Step 6 > Run Test Plan
- Step 7 > Save Test Plan

### Links e referências
- Site do JMeter
  - https://jmeter.apache.org/
- JMeter Tutorial
  - https://www.youtube.com/watch?v=817zU_bXh9Y&list=PLUDwpEzHYYLs33uFHeIJo-6eU92IoiMZ7