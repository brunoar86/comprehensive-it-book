# Programação Assíncrona

## Conceitos Básicos de Programação Assíncrona

A programação assíncrona é um paradigma de programação utilizado para melhorar a eficiência e a capacidade de resposta de um software. Ao contrário da execução síncrona, onde as tarefas são executadas sequencialmente, a programação assíncrona permite que tarefas sejam realizadas em paralelo, sem bloquear o fluxo principal de execução. Vamos explorar os conceitos fundamentais para entender melhor este paradigma.

### Entendimento de Síncrono e Assíncrono

#### Síncrono 

Na execução síncrona, uma tarefa deve ser concluída antes que a próxima possa começar. Isso significa que o programa espera pela conclusão de cada operação antes de prosseguir, o que pode levar a ineficiências significativas, especialmente quando se trata de operações de I/O (Entrada/Saída), como solicitações de rede ou leitura de arquivos, que podem demorar.

#### Assíncrono 

Na execução assíncrona, o programa pode iniciar uma tarefa e prosseguir para a próxima sem esperar pela conclusão da primeira. Isso é especialmente útil para operações que levam tempo, pois o programa pode continuar executando outras tarefas. A conclusão da tarefa assíncrona é geralmente tratada por meio de callbacks, promises ou async/await, permitindo ao programa ser notificado e agir quando a operação é concluída.

### Bloqueio vs Não Bloqueio

#### Bloqueio 

Uma operação de bloqueio impede a execução de outras operações até que seja concluída. Em programação síncrona, as operações de I/O, por exemplo, são bloqueantes por natureza, o que pode resultar em um uso ineficiente dos recursos do sistema, pois o processo ou thread fica ocioso esperando pela conclusão da operação.

#### Não Bloqueio 

Uma operação não bloqueante permite que outras operações sejam executadas enquanto espera pela conclusão de uma tarefa. Isso é fundamental na programação assíncrona, onde as operações de I/O não bloqueiam o thread principal, permitindo que a aplicação permaneça responsiva.

### Concorrência vc Paralelismo

#### Concorrência 

Refere-se à capacidade de uma aplicação fazer progresso em várias tarefas ao mesmo tempo. Em um ambiente de execução de thread única, como JavaScript no navegador, a concorrência é alcançada alternando tarefas de forma eficiente, dando a impressão de que as operações estão sendo executadas em paralelo, mesmo estando em um único thread.

#### Paralelismo 

Envolve a execução de várias operações ao mesmo tempo em diferentes threads ou processadores. O paralelismo é mais explícito em sistemas com múltiplos cores ou CPUs, onde tarefas ou operações podem ser distribuídas entre eles para serem executadas simultaneamente.

## Callbacks

Os callbacks são uma das técnicas fundamentais em programação assíncrona, especialmente em JavaScript, onde são amplamente utilizados para manipular eventos, realizar solicitações de rede e mais. Vamos explorar o que são callbacks, como são usados, e os problemas comuns associados a eles.

### Definição e uso

Um callback é uma função que é passada como argumento para outra função e é executada após a conclusão de alguma operação assíncrona. A função que recebe o callback geralmente executa algumas operações (como fazer uma solicitação de rede) e chama o callback fornecido quando termina, passando os resultados da operação para o callback, se necessário.

Aqui está um exemplo simples de como um callback pode ser usado para uma operação assíncrona:

~~~javascript
function exemploAssincrono(callback) {
    setTimeout(() => {
        // Simula uma operação que leva tempo, como uma solicitação de rede
        const resultado = 'operação concluída';
        callback(resultado);
    }, 1000);
}

exemploAssincrono(resultado => {
    console.log(resultado); // Imprime: operação concluída
});
~~~

No exemplo acima, setTimeout é usado para simular uma operação assíncrona. O callback é chamado após 1 segundo com o resultado da operação.

### Problemas comuns (ex: "Callback Hell")

O uso excessivo de callbacks, especialmente em situações onde várias operações assíncronas dependem umas das outras, pode levar a um fenômeno conhecido como "Callback Hell" (ou "Pyramid of Doom"). Isso ocorre quando os callbacks são aninhados uns dentro dos outros, levando a um código profundamente aninhado que é difícil de ler e manter.

~~~javascript
operacaoAssincrona1(function(resultado1) {
    operacaoAssincrona2(resultado1, function(resultado2) {
        operacaoAssincrona3(resultado2, function(resultado3) {
            console.log(resultado3);
            // Continua aninhando mais operações...
        });
    });
});
~~~

O "Callback Hell" torna o código confuso devido à sua estrutura aninhada e ao fluxo de controle não linear. Isso pode dificultar a compreensão do código, a depuração e a manutenção.

Para lidar com os desafios apresentados pelo "Callback Hell", foram desenvolvidas abordagens alternativas, como Promises e async/await, que oferecem uma sintaxe mais limpa e um fluxo de controle mais linear para operações assíncronas. Estas abordagens são agora preferidas para muitos novos projetos e desenvolvedores devido à sua legibilidade e facilidade de uso.

Apesar dos desafios, os callbacks continuam sendo uma parte essencial da programação JavaScript, especialmente para eventos e situações onde uma abordagem simples assíncrona é suficiente. Compreender como usar callbacks efetivamente é fundamental para qualquer desenvolvedor que trabalhe com JavaScript ou qualquer linguagem de programação que os suporte.

## Promises

Promises são um conceito essencial do JavaScript. Elas estão presentes em praticamente todo o ecossistema da linguagem.

Promises são um padrão de desenvolvimento que visam representar a conclusão de operações assíncronas. Elas não eram nativas do JavaScript até o ES6, quando houve uma implementação oficial na linguagem, antes delas, a maioria das funções usavam callbacks.

### Entendendo Promises
### Criação e Uso de Promises
### Encadeamento de Promises
### Tratamento de Erros com Promises

## Async/Call

### Sintaxe e Funcionamento
### Uso com Promises
### Tratamento de Exceções com Try/Catch

## Event Loop

### Como o JavaScript trata Operações Assíncronas Internamente
### Microtasks e Macrotasks

## Workers Threading

### Web Workers
### Service Workers
### Conceitos de Threading em Outras Linguagens de Programação

## Gerenciamento de Estado em Aplicações Assíncronas

### State Machines
### Bibliotecas de Gerenciamento de Estado

## Padrões e Práticas Recomendadas

### Evitando "Callback Hell"
### Composição de Promises
### Estratégias de Error Handling e Retry

## Aplicações em Tempo Real

### WebSockets

Websocket é uma tecnologia avançada que possibilita a abertura de uma comunicação interativa entre o navegador do usuário e o servidor. Diferente do modelo convencional de requisições HTTP, onde cada requisição necessita de uma nova conexão TCP, os websockets permitem que uma conexão única e persistente seja estabelecida. Essa conexão fica aberta, possibilitando que tanto o cliente quanto o servidor troquem dados a qualquer momento, de forma bidirecional e com baixa latência.

O processo de estabelecimento da conexão websocket começa com um handshake HTTP, onde o cliente solicita a atualização da conexão para websockets através do cabeçalho 'Upgrade'. Se o servidor suportar websockets, ele responde apropriadamente, e a conexão HTTP é então elevada a uma conexão websocket. Após o handshake, os dados podem ser enviados em ambos os sentidos até que a conexão seja fechada por qualquer uma das partes.

Após o estabelecimento bem-sucedido de uma conexão através do handshake inicial, a conexão passa por diferentes estados ao longo de sua vida. Estes estados permitem o gerenciamento eficiente da comunicação bidirecional entre o cliente e o servidor. Os estados principais são os seguintes:

0 - CONNECTING: Este é o estado inicial, quando a conexão websocket está tentando ser aberta e não está pronta para enviar ou receber dados.
1 - OPEN: Após o handshake ser bem-sucedido, a conexão websocket entra no estado "open". Neste estado, a conexão está ativa e tanto o cliente quanto o servidor podem enviar e receber mensagens. Este é o estado em que a maior parte da comunicação acontece.
2- CLOSING: Quando uma solicitação para fechar a conexão é feita, o conexão entra no estado "closing". Isso pode ser iniciado por qualquer uma das partes (cliente ou servidor) enviando um frame de controle de fechamento. Este estado é o prelúdio do término da conexão, embora a conexão ainda permaneça aberta até que o processo de fechamento seja concluído.
3 - CLOSED: Este estado indica que a conexão foi fechada completamente. Nenhum dado pode ser enviado ou recebido e a conexão não pode ser reaberta.

Esta tecnologia é particularmente útil em aplicações web que necessitam de atualizações em tempo real, como jogos online, chats, plataformas de negociação financeira e qualquer aplicação que se beneficie de uma comunicação rápida e contínua entre o cliente e o servidor. Os websockets são suportados na maioria dos navegadores modernos e oferecem uma maneira eficiente de manter uma conexão viva sem a necessidade de polling constante ou long polling, técnicas essas que são menos eficientes e mais custosas em termos de recursos.

O objetivo principal do websocket, conforme descrito no RFC 6455, é fornecer um mecanismo para comunicações bidirecionais e full-duplex sobre uma única conexão de longa duração, que é mais eficiente do que as abordagens tradicionais em HTTP para aplicações que requerem interações em tempo real. O protocolo permite que tanto o cliente quanto o servidor enviem dados a qualquer momento, uma vez que a conexão websocket esteja estabelecida, facilitando a criação de aplicações web dinâmicas e interativas.


### Server-Sent Events (SSE)
### Polling vs. Long Polling

## Ferramentas e Bibliotecas

### Axios para solicitações HTTP assíncronas
### RxJS e a programação reativa
### Async.js para Manipulação de Operações Assíncronas

# Web Services

Um web service é definido como um componente de software desenhado para suportar a interação interoperável entre sistemas diferentes da web. Utilizando um conjunto de protocolos e padrões abertos, os web services permitem que aplicações se comuniquem, executem funções ou troquem dados, independentemente de suas linguagens de programação, arquiteturas ou plataformas subjacentes. Eles agem como uma ponte digital, facilitando o diálogo entre aplicações em um ambiente distribuído.

## SOAP (Simple Object Access Protocol)

---
## REST (Representational State Transfer)

REST é um estilo arquitetural definido por Roy Fielding em sua tese de doutorado em 2000. Seu desenvolvimento foi uma resposta direta às complexidades observadas em protocolos como SOAP, buscando uma maneira para resolver o problema da escalabilidade da web.

Os estudos sugeriram que a escalabilidade da web é influenciada por um conjunto de requisitos, determinando portanto uma abordagem pragmática à implementação da Web: satisfazer uniformemente os requisitos. 

### Características Definidoras de REST

REST se baseia em seis requisitos fundamentais que direcionam a concepção de serviços web eficientes:

#### Cliente-Servidor

A divisão de responsabilidades é tema central do requisito cliente-servidor. A Web é sistema baseado em cliente-servidor, no qual clientes e servidores têm papéis distintos. Eles podem ser implementados de maneira independente, fazendo uso de qualquer linguagem de programação ou tecnologia, desde que mantenham a conformidade com a __interface uniforme__ da Web.

#### Interface Uniforme

As interações entre os componentes Web (clientes, servidores e intermediários da rede) dependem da uniformidade das suas interfaces. Se qualquer componente divergir dos padrões estabelecidos, então o sistema de comunicação da Web para de funcionar.

Os componentes Web interagem consistentemente baseados nos quatro requisitos da interface uniforme:

1. Identificação de recursos
2. Manipulação de recursos através de representação
3. Mensagens autodescritivas
4. Hypermedia as the engine of application state (HATEOAS)

##### Identificação de recursos

Cada conceito único baseado na Web é reconhecido como um __recurso__ e pode ser acessado por um identificador único, como a URI. Por exemplo, uma URI de um site, tal como __http://www.exemplo.com__, identifica exclusivamente o conceito do recurso raiz de um site específico.

##### Manipulação de Recursos através de representação

Clientes manipulam representações de recursos. Um mesmo recurso pode ser representado para clientes diferentes de formas distintas. Por exemplo, um documento pode ser representado como HTML para um navegador Web, e como um JSON para um programa automatizado. A ideia é que a representação é uma forma de interagir com o recurso, mas não é o recurso em si. Essa distinção permite que o recurso seja representado de formas diferentes sem nunca mudar seu identificador.

##### Mensagens Autodescritivas

O estado __desejado__ do recurso pode ser representado por meio de uma mensagem de requisição do cliente. O estado __atual__ do recurso pode ser representado por meio de uma mensagem de resposta retornada pelo servidor. Como um exemplo, o cliente de um editor de uma página pode usar uma mensagem de requisição para transferir a representação que sugere uma atualização (novo estado) na página para uma página web (recurso) gerenciada por um servidor. É papel do servidor aceitar ou rejeitar a requisição do cliente.

##### Hypermedia as the Engine of Application State (HATEOAS)

A representação do estado de um recurso inclui __links__ para os recursos relacionados. __Links__ são as linhas que tecem a Web, por permitirem que os usuários busquem informação em aplicações de maneira direta. A presença ou a ausência de um __link__ em uma paǵina é uma parte importante do estado atual do recurso.

#### Sistema em Camadas

O requisito do sistema em camadas permite que os intermediários baseados na rede, como __proxies__ e __gateways__ sejam implantados de forma transparente entre um cliente e servidor usando a interface uniformizada da Web. De modo geral, um intermediário baseado na rede interpeptará a comunicação cliente-servidor para um propósito específico. Intermediários baseados na Web são comumente usados para garantir a segurança, cacheamento de respostas e balanceamento de carga.

#### Cache

Armazenamento em __cache__ é um dos requisitos da arquitetura web mais importantes. O requisito de __cache__ indica que o servidor web deve declarar o quanto cada dado da resposta é passível de armazenamento em __cache__. Armazenar os dados das respostas em __cache__ pode ajudar a reduzir a latência percebida pelo cliente, aumentar a disponibilidade e a confiabilidade de uma aplicação, e controlar a carga do servidor web. Em outras palavras, o armazenamento em __cache__ reduz o custo da Web.

Um __cache__ pode existir em qualquer lugar no caminho da rede entre o cliente e o servidor. Eles podem estar em um servidor web de uma organização, por meio de um serviço especializado de entrega de conteúdos (CDN), ou dentro do próprio cliente.

#### Stateless

O requisito __stateless__ indica que um servidor web não é obrigado a memorizar o estado das aplicações de seus clientes. Como resultado, cada cliente precisa incluir toda a informação contextual que considerar relevante em cada interação com o servidor web. Servidores web pedem ao cliente que gerencie a complexidade da comunicação do estado de suas aplicações para que o servidor web possa atender a um número muito maior de clientes. Esta troca é um contribuidor chave para a escalabilidade do estilo arquitetural Web.

#### Código sob Demanda

A Web faz uso pesado de código sob demanda, um requisito REST que permite aos servidores web transferir temporariamente programas executáveis, como __scripts__ e __plug-ins__, para os clientes.

Código sob demanda tende a estabelecer um casamento das tecnologias usadas um servidor e seus clientes, já que o cliente precisa entender e executar o código que baixa sob demanda do servidor. Por este motivo, o código sob demanda é o único requisito do estilo arquitetural Web que é considerado opcional. Tecnologias embarcadas em navegadores como __Java applets__, JavaScript e Flash são exemplos no quesito de código sob demanda.

### JAX-RS

### JWT - JSON WEB TOKEN

### HTTP

---
## XML-RPC (XML Remote Procedural Call)

---
## JSON-RPC

---
## GraphQL

GraphQL é uma linguagem de consulta (QL -> query language) para APIs de dados na perspectiva do consumidor __frontend__. GraphQL é também uma camada em tempo de execução que precisa ser implementada no __backend__ e é essa camada que possibilita que o consumidor do __frontend__ utilize a nova linguagem.

A principal vantagem do GraphQL é permitir que os clientes solicitem exatamente os dados de que precisam e possibilitar a agregação dos dados de múltiplas fontes em uma única consulta.

### Princípios Fundamentais do GraphQL

__Linguagem Declarativa__: Ao contrário do REST, onde o servidor define os endpoints e a forma dos dados, no GraphQL, são os clientes que especificam a estrutura dos dados requeridos através de consultas. Isso reduz o __over-fetching__ (demandar dados demais) e o __under-fetching__ (demandar dados de menos).

__Sistema de Tipos__: GraphQL utiliza um sistema de tipos fortemente tipado para definir as capacidades da API. Cada API GraphQL é definida por seus tipos de dados, que podem ser escalares, objetos, enumerações, interfaces, entre outros.

__Resolução de Consultas__: O servidor GraphQL resolve as consultas interpretando o grafo de dados requerido, acessando diferentes fontes de dados, como bancos de dados, APIs ou mesmo serviços de terceiros para compor a resposta.

### Vantagens do GraphQL

__Flexibilidade para os Clientes__: Os clientes podem adaptar as consultas para receber apenas os dados necessários, otimizando o tráfego de rede e melhorando a performance do aplicativo.

__Integração de Dados de Múltiplas Fontes__: GraphQL pode unificar diversas fontes de dados em uma única API, simplificando o desenvolvimento frontend.

__Descoberta de API e Autodocumentação__: O sistema de tipos de GraphQL fornece um entendimento claro do esquema da API, facilitando a exploração e documentação automática das APIs.

### Implementação do Servidor GraphQL

A implementação de um servidor GraphQL envolve a definição de um esquema (schema) que especifica os tipos e as relações entre eles, além dos resolvers, que são as funções responsáveis por buscar os dados para cada tipo. As linguagens mais comuns para implementação de servidores GraphQL incluem JavaScript (com Node.js), Python, Ruby, e Java.

---
## gRPC (Google Remote Procedure Call)

---
## OData (Open Data Protocol)

---