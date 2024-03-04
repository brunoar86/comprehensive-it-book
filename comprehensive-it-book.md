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