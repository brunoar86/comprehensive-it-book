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

Hypermedia Transfer Protocol (HTTP) é um protocolo de camada de aplicação para a transmissão de documentos hipermídia, como HTML. Ele foi projetado para comunicação entre navegadores da web e servidores web, mas também pode ser usado para outros fins. O HTTP segue um modelo clássico cliente-servidor, com um cliente abrindo uma conexão para fazer uma solicitação e esperando até que receba uma resposta. HTTP é um protocolo sem estado, o que significa que o servidor não mantém nenhum dado (estado) entre duas solicitações. 

#### Identificado recursos na Web

O alvo de uma requisição HTTP é chamado de "resource", ou recurso em português, com a natureza ainda não definida; Isso pode ser um documento, uma foto ou qualquer outra coisa. Cada recurso é identificado por uma Identificação de recursos uniforme, do inglês __Uniform Resource Identifier__ (URI) usada pelo HTTP para identificar recursos.

A identidade e a localização de recursos na Web são fornecidas, principalmente por um único URL (Uniform Resource Locator, um tipo de URI). Pode ser que as vezes a identidade e a localização não são dadas pelo mesmo URI: O HTTP usa um cabeçalho HTTP específico, 'Alt-Svc' quando o recurso solicitado quer que o cliente acesse-o de outra localização.

##### URLs e URNs

URLs

A forma mais comum de URL é o Uniform Resource Locator (URL), que é conhecido como endereço de Web.

https://developer.mozilla.org
https://developer.mozilla.org/pt-BR/docs/Learn
https://developer.mozilla.org/pt-BR/search?q=URL

Qualquer um desses URLs podem ser digitados na barra de endereços do seu navegador dizendo para carregar a página associada (recurso).

Uma URL é composta por diferentes partes, algumas são estritamente necessárias e outras são opcionais. Um exemplo mais complexo seria algo como isso:

http://www.exemplo.com:80/pasta/para/meu-arquivo.html?chave1=valor1&chave2=valor2#AlgumaCoisaNoDocumento

URNs 

Um Nome de Recurso Uniforme do inglês Uniform Resource Name (URN) é uma URI que identifica um recurso pelo nome em um namespace particular.

urn:usbn:9780141036144
urn:ietf:rfc:7230

As duas URNs correspondem:

1. o livro Nineteen Eighty-Fourpor George Orwell;
2. a especificação 720 da IETF, Hypertext Transfer Protocol (HTTP/1.1): Sintaxe de mensagem e rotas.

##### Sintaxe das Uniform Resource Identifiers (URIs)

ESQUEMA OU PROTOCOLO

http://www.example.com:80/path

__http://__ é o protocolo. Ele indica qual é o protocolo que o navegador irá usar. Usualmente o protocolo é o HTTP, ou sua versão segura, HTTPS. A Web requer um desses dois, mas os navegadores também sabem lidar com outros protocolos como o __mailto:__ (para abrir um cliente de e-mail) ou o __ftp:__ para fazer uma transferência de arquivo, então não fique surpreso se ver alguns desses protocolos. Esquemas comuns são:

Esquema     |      Descrição
            |
data        |   URI de dados (en-US)
file        |   Nomes de arquivos específicos do host
ftp         |   Protocolo de transferência de arquivo (en-US)
http/https  |   Hyper text transfer protocol (Secure)
mailto      |   Endereço de correio eletrônico
ssh         |   Secure shell
tel         |   telefone
urn         |   Uniform Resource Names
view-source |   Código fonte de um recurso
ws/wss      |   Conecções de WebSocket (Encriptadas)

AUTORIDADE

http://www.example.com:80/path/to/my

__www.example.com__ é o nome de domínio ou autoridade que governa o namespace. Ele indica qual servidor web será solicitado. Alternativamente, é possível utilizar um IP adress, mas isso pode ser menos conveniente e não é muito utilizado na Web.

PORTA

http://www.example.com:80/path/to/myfile.html?key1=value1

__:80__ é a porta nesta instância. Ela indica qual é o portão técnico para acessar os recursos no servidor web. Usualmente ela é omitida se o servidor web utiliza a porta padrão do protocolo HTTP (80 para HTTP e 443 para HTTPS) para garantir o acesso aos recursos. Do contrário, ela se torna obrigatória.

CAMINHOS

http://www.example.com:80/path/to/myfile.html?key1=value1

__/path/to/myfile.html__ é o caminho para o recurso no servidor Web. Nos primeiros dias da Web, um caminho era representado pelo caminho físico correspondente no servidor Web. Hoje em dia isso é mais uma abstração tratada pelos servidores Web não sendo necessariamente o endereço físico do arquivo em questão.

QUERY/PARÂMETROS

http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument

__?key1=value1&key2=value2__ são parâmetros extras fornecidos ao servidor Web. Eles são uma lista de pares chaves/valores separados com o símbolo __&__. O servidor pode usar esses parâmetros para fazer coisas extras depois de retornado o recurso para o usuário. Cada servidor web tem suas regrasem relação aos parâmetros, e o único jeito confiável de saber como um servidor Web específico trata os parâmetros é perguntando o dono do servidor.

FRAGMENTOS

http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument

__SomehereInTheDocument__ é uma âncora para outra parte do próprio recurso. Uma âncora representa uma espécie de marcador dentro do recurso, dando ao navegador as instruções para mostrar o conteúdo localizado naquele ponto marcado. Em um documento HTML, por exemplo, o navegador irá dar scroll para a âncora em um ponto definido; em um vídeo ou áudio, o navegador irá tentar ir para o tempo que a âncora representa. Vale ressaltar que a parte após o #, também conhecido como identificador de fragmento, nunca é enviado ao servidor com o pedido.

##### Notas de Uso

Ao usar URLs em conteúdo HTML, em geral se deve usar apenas alguns desses esquemas URL. Quando se referir a subrecursos - que são, arquivos que estão sendo carregados como parte de um documento maior - você deverá utilizar apenas os esquemas HTTP e HTTPS. Gradualmente os navegadores estão reduzindo o suporte ao uso do FTP para carregar subrecursos por razões de segurança.

FTP ainda é aceitável em alto nível (como digitados diretamente na barra de URL do navegador, ou o alvo do link), todavia alguns navegadores podem delegar o carregamento do FTP para outra aplicação.

#### Data URLs

Data URLs, URLs com prefixo do protocolo __data:__, permitem que criadores de conteúdos incorporem pequenos arquivos em linha nos documentos. Eles eram conhecidos como "data URIs" até o nome ser aposentado pela WHATWG.

SINTAXE

URLs de dados são compostos de quatro partes: um prefixo (data:), um tipo MIME indicando o tipo do dado, um token base64 opcional no caso de dado não textual e o dado em si:

__data:[<mediatype>][;base64],<data>__

O mediatype é uma string tipo MIME como 'image/jpeg' para um arquivo de imagem JPEG. Se omitido, considera-se text/plain;charset=US-ASCII.

Se o dado contém caracteres reservados do RFC 3986, ou contém caracteres de espaço, carateres de linha nova, ou outro caracter não imprimível, esses caracteres precisarão ser codificados para URL.

Se o dado for textual, você pode incorporar o texto (utilizando as entidades apropriadas ou os escapes baseados no fecho do tipo de documento). De outro modo, voce pode especificar o __base64__ para inserir dados binários  codificados em base64.

Alguns exemplos:

__data:,Hello%2C%20World! (Dados simples text/plain)__

__data:text/plain;base64,SGVsbG8sIFdvcmxkIQ%3D%3D__ (Versão codificada em base64-encoded do anterior)

__data:text/html,%3Ch1%3EHello%2C%20World!%3C%2Fh1%3E__ (Um documento HTML com <h1>Hello, World!</h1>)

__data:text/html,<script>alert('hi');</script>__ (Um documento html que executa um alerta Javascript)

CODIFICAÇÃO DE DADOS EM FORMATO BASE64

Base64 é um grupo de esquemas de codificação binary-to-text que representa dados binários em uma string no formato ASCII através da sua tradução para uma representação radix-64. Por consistir apenas de caracteres ASCII, as strings base64 são geralmente url-safe e é por isso que elas podem ser usadas para codificar dados em Data URLs.

Para mais informações, acesse: https://developer.mozilla.org/en-US/docs/Web/HTTP

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

### Introdução

gPRC é uma tecnologia de chamada de procedimento remoto (RPC) desenvolvida pelo Google, que permite que diferentes sistemas se comuniquem entre si de forma eficiente e independente da linguagem de programação. A sigla gRPC significa Google Remote Procedure Call. Pense no gRPC como um mensageiro eficiente (RPC) que pode entregar mensagens em diferentes idiomas (independência da linguagem) com a precisão e eficiência de um serviço expresso.


### Componentes-chave do gRPC

__Protocol Buffers (ProtoBuf)__: É a linguagem de definição de interface (IDL) usada pelo gRPC. ProtoBuf permite definir a estrutura dos dados e o contrato de serviço de uma forma linguagem-neutra. Imagine o ProtoBuf como o esqueleto e a pele de um robô, onde você define todas as partes e funções que o robô pode realizar, mas sem especificar em que material ele é feito ou em que sistema operacional ele roda.

__Canais__: São conexões de longa duração entre o cliente e o servidor, por onde passam as chamadas RPC. Pense em canais como tubos em um sistema de correio pneumático, onde as mensagens são enviadas de um ponto a outro de forma rápida e segura.

__Serviços__: No gRPC, um serviço é uma coleção de métodos que podem ser chamados remotamente. Analogamente, você pode pensar em serviços como os diferentes serviços oferecidos por uma empresa de entregas, cada um com suas especificidades, como entrega expressa, rastreamento de pacores, entre outros.

### Funcionamento do gRPC

O gRPC usa HTTP/2 como seu protocolo de transporte, permitindo comunicação bidirecional, streaming, e uma melhor utilização da conexão de rede. Imagine que HTTP/2 é uma rodovia multifaixa em comparação com a estrada de uma única faixa do HTTP/1.1, permitido que mais dados (veículos) fluam em ambas as direções simultaneamente e de forma mais eficiente.

### Vantagens do gRPC

__Alto desempenho__: Devido ao uso de ProtoBufe HTTP/2, o gRPC é mais rápido e mais eficiente que outras tecnologias de RPC, como o SOAP ou REST.
__Independência de linguagem__: Você pode definir um serviço em um ProtoBuf e gerar código cliente e servidor em várias linguagens, facilitando a integração entre sistemas heterogêneos.
__Suporte a streaming__: gRPC suporta streaming bidirecional, permitindo que clientes e servidores enviem uma sequência de mensagens um para o outro sem esperar que a outra parte termine de enviar todas as suas mensagens.

### Implementação Prática

Para implementar um serviço gRPC, você precisa seguir estes passos:

1. __Definir o serviço em ProtoBuf__: Especifique os métodos que seu serviço oferecerá, junto com seus parâmetros e tipos de retorno.
2. __Gerar código cliente/servidor__: Use as ferramentas do gRPC para gerar código base a partir da sua definição ProtoBuf em sua linguagem de escolha.
3. __Implementar o serviço no servidor__: Escreva a lógica do serviço no lado do servidor, usando o código base gerado.
4. __Implemetar o cliente__: Use o código base do cliente para chamar o serviço a partir de outro sistema.

### Recursos e Ferramentas para Aprofundamento

__Documentação Oficial do gRPC__: https://gRPC.io
__Protocol Buffers Google Developers__: https://protobuf.dev
__Livros e Tutoriais__: Busque por livros atualizados online específicos para a linguagem de programação que você está usando com gRPC.

## OData (Open Data Protocol)

---