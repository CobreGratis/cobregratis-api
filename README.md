# API do Cobre Grátis

O [Cobre Grátis](http://cobregratis.com.br) é um aplicativo na web para emissão e gerenciamento de boletos bancários.

Com a API é possível integrar qualquer sistema, seja ele uma loja virtual de e-commerce ou um sistema de ERP como Oracle, SAP, Microsiga para que ele emita boleto bancário automaticamente. É uma ferramenta realmente poderosa.

## Bibliotecas

* Ruby: [https://github.com/BielSystems/cobregratis-ruby](https://github.com/BielSystems/cobregratis-ruby)
* Python: [https://github.com/BielSystems/cobregratis-python](https://github.com/BielSystems/cobregratis-python)
* PHP: [https://github.com/BielSystems/cobregratis-php](https://github.com/BielSystems/cobregratis-php)
* Perl: [https://github.com/BielSystems/cobregratis-perl](https://github.com/BielSystems/cobregratis-perl)
* .NET: [https://github.com/FredZvt/cobregratis-dotnet](https://github.com/FredZvt/cobregratis-dotnet)
* Java: [https://github.com/duduribeiro/cobregratis-java](https://github.com/duduribeiro/cobregratis-java)
* Java (só leitura): [https://github.com/gustavohenrique/cobregratis-java](https://github.com/gustavohenrique/cobregratis-java)

## Benefícios da API

* Programadores conseguem incluir o Cobre Grátis como meio de pagamento em um e-commerce.
* Criar boletos bancários a partir de um sistema de ERP.
* Integração com o sistema de Contas a Receber
* Desenvolver aplicativos móveis para emissão e gerenciamento de boleto bancário
* Liberdade para fazer o que quiser, todo programador clama por isso!

## Programa de Parceiros

[Ganhe dinheiro integrando o Cobre Grátis!](http://bielsystems.wufoo.eu/forms/ganhe-dinheiro-integrando-o-cobre-gratis/)

## Não é um programador?

A API é para nerds. Se você não é um programador, e não tem nenhum na sua empresa, entre em contato com [HE:labs](http://helabs.com.br).

## Introdução

A API do Cobre Grátis é baseada nos princípios [RESTful](http://en.wikipedia.org/wiki/Representational_state_transfer#RESTful_web_services) e usa conexão HTTP com todos os seus verbos (GET/POST/PUT/DELETE). Com a nossa API o seu desenvolvedor poderá integrar facilmente um programa existente à plataforma de emissão de boleto bancário.

A URL Base da API é **https://app.cobregratis.com.br/**

As requisições só podem ser feitas com SSL (https:// na frente da URL Base)

É possível requisitar os dados no formato [JSON](http://www.json.org/json-pt.html) ou [XML](http://en.wikipedia.org/wiki/XML).

Por padrão, a API deve ser acessada através das mesmas URLs e verbos HTTP da interface HTML normal, adicionando-se o formato desejado (.xml ou .json) ao final da URL, ou então passando os headers `Content-type` e `Accept` na requisição HTTP com os valores de acordo com o formato desejado (application/xml ou application/json, respectivamente).

## Plano Contratado

Para utilizar a API é necessário ter contratado o Plano Premium do Cobre Grátis.

Para conhecer os planos e preços, acesse http://cobregratis.com.br/planos

## Convenções da API

Na documentação da API, utilizamos as seguintes convenções:

* **#{variable}** - Indica o nome de uma variável que precisa ser substituída por valores da sua conta.
* **...** - Indica o conteúdo da resposta de uma requisição, que foi truncado para facilitar a leitura da documentação.
* **$TOKEN** - Indica o Token de Autenticação e está neste formato para facilitar os testes na linha de comando. Supondo que o seu token é "zjuio96wkixkzy6z98sy", você pode rodar o comando abaixo e posteriormente copiar e colar os comandos desta documentação no terminal.
`export $TOKEN=zjuio96wkixkzy6z98sy`

## Códigos de Retorno

A API retorna os códigos de resposta HTTP. Estas são as informações mais relevantes:

* **200 OK** - A chamada foi bem sucedida.
* **400 Bad Request** - A requisição é inválida, em geral conteúdo mal formado.
* **401 Unauthorized** - O Token de Autenticação é inválido.
* **403 Forbidden** - O plano contratado não permite acesso à API.
* **404 Not Found** - O endereço acessado não existe.
* **429 Too Many Requests** - O usuário atingiu o [limite de requisições](#limite-de-requisições).
* **503 Service Unavailable** - A conta atingiu algum dos limites de uso.
* **500 Internal Server Error** - Houve um erro interno do servidor ao processar a requisição.

## Segurança

O Cobre Grátis utiliza Certificados SSL 256 bits.

Toda requisição realizada através da API deve utilizar o protocolo HTTPS pois estará passando informações de autenticação no cabeçalho da requisição.

As requisições realizadas na porta 80, serão automaticamente redirecionadas para a porta 443. Esta medida garante que nenhuma requisição realizada na API estará fora do protocolo seguro.

Todas as requisições realizadas nos servidore do Cobre Grátis serão criptografadas.

<a target="_blank" href="http://siteforte.com.br/certificado/app.cobregratis.com.br?utm_source=app.cobregratis.com.br&amp;utm_medium=selo_premium&amp;utm_term=siteforte&amp;utm_campaign=permanente"><img style="border:none;" title="Auditoria de segurança para serviços online com transações financeiras e informações confidenciais :: SITEFORTE - Segurança Digital" src="http://siteforte.com.br/selos/6_appcobregratiscombr.png"></a>
<script type="text/javascript" src="https://seal.godaddy.com/getSeal?sealID=EsVFjF1X7oM6H3W5JYic0wAmUVtfEaN5qV6XqBNWQa9BOCOV7DtucD"></script>

## Autentiçação

Todo acesso à API do Cobre Grátis é feito do ponto de vista de um usuário. Assim sendo, toda requisição à API deverá ser autenticada. A autenticação é feita via HTTP Basic, porém ao invés de passar o login e senha do usuário, como é tradicional, deve-se fornecer o **Token de Autenticação** do usuário no campo ‘login’ e nada no campo ‘password’. Alguns clientes HTTP podem reclamar do fato do campo ‘password’ estar vazio, nesse caso pode-se informar ‘X’ como senha, que o sistema irá ignorar.

O **Token de Autenticação** pode ser obtido no link [Minhas Informações](https://app.cobregratis.com.br/myinfo) dentro do Cobre Grátis.

Exemplo de chamada API autenticada (onde "zjuio96wkixkzy6z98sy" é o Token de Autenticação do usuário):

```shell
curl -i -u zjuio96wkixkzy6z98sy:X -X GET \
  -H 'Content-Type: application/xml' \
  -H 'User-Agent: MyApp (yourname@example.com)' \
  https://app.cobregratis.com.br/bank_billets/1.xml

HTTP/1.1 200 OK
Date: Fri, 05 Nov 2010 12:00:00 GMT
Content-Type: application/xml; charset=utf-8
...

<?xml version="1.0" encoding="UTF-8"?>
<bank_billet>
  <id type="integer">1</id>
  ...
</bank_billet>
```

Já a mesma solicitação sem os parâmetros de autenticação (ou com valores errados), resultaria em:

```shell
curl -i -X GET \
  -H 'Content-Type: application/xml' \
  -H 'User-Agent: MyApp (yourname@example.com)' \
  https://app.cobregratis.com.br/bank_billets/1.xml

HTTP/1.1 401 Unauthorized
Date: Fri, 05 Nov 2010 12:00:00 GMT
Content-Type: application/xml; charset=utf-8
...

<?xml version="1.0" encoding="UTF-8"?>
<hash>
  <error>Email ou senha inválidos.</error>
</hash>
```

## Fazendo uma Requisição

Para realizar uma requisição, é necessário concatenar a URL Base ao path da ação de um determinado recurso.
Cada ação disponível de cada recurso, terá uma URL específica, documentada nas [APIs Disponíveis](#apis-dispon%C3%ADveis).

Por exemplo, para fazer uma requisição para a ação 'listar' do recurso 'boletos bancários' (GET /bank\_billets.[format]), você deve usar a URL: **https://app.cobregratis.com.br/bank_billets.json**

## Identificando sua aplicação

Você deve incluir o header `User-Agent` com o nome da sua aplicação e um link ou endereço de e-mail dela, para que possamos entrar em contato caso 1) você esteja fazendo algo errado, e possamos avisá-lo antecipadamente antes de você ser bloqueado, ou 2) esteja fazendo algo muito legal, e possamos dar-lhe os parabéns :)
Segue um Exemplo:

    User-Agent: Landing Commerce (http://landingcommerce.com.br)

Se você não informar este cabeçalho, você receberá um erro `400 Bad Request`.

**Atenção:** Por uma questão de compatibilidade, este bloqueio será realizado somente a partir de 01/01/2013.

## Cache HTTP

Você deve fazer uso dos cabeçalhos HTTP de cache para diminuir a carga em nossos servidores (e aumentar a velocidade do seu aplicativo!).

A maioria dos retornos das requisições irão incluir um header `ETag` ou `Last-Modified`. Quando você solicitar um recurso pela primeira vez, armazene esse valor e nos envie de volta nas requisições seguintes nos headers `If-None-Match` e `If-Modified-Since`. Se o recurso não foi alterado, você receberá uma resposta com o header `304 Not Modified`, o que economiza tempo e largura de banda, por evitar de te enviar os dados que você já tem.

Mais informações sobre Cache HTTP (em inglês): http://www.mnot.net/cache_docs/

## Tratamento de erros

Se os nossos servidores estiverem com problema, sua requisição receberá um retorno de erro com status 5xx.

Erro 500 significa que a aplicação está completamente indisponível, mas você pode receber também outros erros da família 500 em casos específicos, tais como `502 Bad Gateway`, `503 Service Unavailable` ou `504 Gateway Timeout`.

É de sua responsabilidade identificar o erro e lidar com esses casos, fazendo com que o aplicativo tente enviar a requisição novamente depois de alguns minutos.

Nós temos uma página que informa o status dos servidores do Cobre Grátis em http://status.cobregratis.com.br/

## Limite de Requisições

Existem dois tipos de limite de requisições. Em ambos os casos a contagem é feita para cada Token de Autenticação utilizado.

### Intervalo
Cada usuário pode realizar uma requisição a cada 1 segundo.
Caso o usuário realize duas requisições simultâneas, o servidor retorna o status HTTP [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4).
Neste caso, o servidor envia o header `Retry-After` com o número de segundos que você deve esperar até realizar a próxima requisição.

### Requisições por Hora
Cada usuário pode realizar no máximo 500 requisições por hora.
O número de requisições feitas pelo usuário é zerada no primeiro minuto de cada hora.

A cada requisição realizada, o servidor retorna os headers `X-RateLimit-Limit` e `X-RateLimit-Remaining` com o número de requisições permitidas e o número de requisições restantes para aquela hora.
Exemplo:

```shell
curl -i -u zjuio96wkixkzy6z98sy:X -X GET \
  -H 'Content-Type: application/xml' \
  -H 'User-Agent: MyApp (yourname@example.com)' \
  https://app.cobregratis.com.br/bank_billets/1.xml

HTTP/1.1 200 OK
Date: Fri, 05 Nov 2010 12:00:00 GMT
Content-Type: application/xml; charset=utf-8
X-RateLimit-Limit: 500
X-RateLimit-Remaining: 486
...
```

Caso atinja o número máximo de requisições dentro de uma hora, o servidor retorna o status HTTP [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4).
Neste caso, você deve esperar até o primeiro minuto da hora seguinte para realizar a próxima requisição.

## APIs Disponíveis

* [Boletos Bancários](https://github.com/BielSystems/cobregratis-api/blob/master/resources/bank_billets.md)

## Webhook
* [Documentação](https://github.com/BielSystems/cobregratis-api/blob/master/resources/webhooks.md)

## Ajude-nos a melhorar

Por favor, nos diga como podemos melhorar a API.
Se você tem alguma necessidade específica ou se encontrou um bug, use o [GitHub issues](https://github.com/BielSystems/cobregratis-api/issues).
Fique a vontade para _forkar_ este projeto e enviar _pull requests_ com melhorias.