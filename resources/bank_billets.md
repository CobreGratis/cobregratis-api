Boletos Bancários
========

Campos disponíveis e formatos utilizados
------------

* [Documentação](http://suporte.cobregratis.com.br/hc/pt-br/articles/201644783-Campos-que-podem-ser-usados-na-criação-de-boletos)

Listar boletos bancários
------------

* `GET /bank_billets.#{format}?page=#{page}`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<bank-billets type="array">
  <bank-billet>
    ...
  </bank-billet>
  <bank-billet>
    ...
  </bank-billet>
</bank-billets>
```

Dados de um boleto bancário
-----------

* `GET /bank_billets/1.#{format}`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<bank-billet>
  <address nil="true"></address>
  <city nil="true"></city>
  <cnpj-cpf nil="true"></cnpj-cpf>
  <created-by-api type="boolean">true</created-by-api>
  <kind>normal</kind>
  <name>Rafael Lima</name>
  <parcel type="integer">1</parcel>
  <created-at type="datetime">2012-07-03T01:40:56-03:00</created-at>
  <notify-overdue type="boolean">false</notify-overdue>
  <subdivision-parent-id type="integer" nil="true"></subdivision-parent-id>
  <comments nil="true"></comments>
  <guarantor nil="true"></guarantor>
  <line>03399.43011 85400.000007 00175.901024 3 54060000050000</line>
  <paid-amount type="float" nil="true"></paid-amount>
  <percent-fines type="decimal" nil="true"></percent-fines>
  <quantity nil="true"></quantity>
  <acceptance>N</acceptance>
  <deleted-at type="datetime" nil="true"></deleted-at>
  <email-state type="integer">1</email-state>
  <generated-at type="datetime" nil="true"></generated-at>
  <our-number-prefix nil="true"></our-number-prefix>
  <pdf-created-at type="datetime" nil="true"></pdf-created-at>
  <updated-at type="datetime">2012-07-03T01:43:44-03:00</updated-at>
  <zipcode nil="true"></zipcode>
  <account-id type="integer">1</account-id>
  <amount type="float">500.0</amount>
  <discount-amount type="decimal" nil="true"></discount-amount>
  <document-number nil="true"></document-number>
  <processed-our-number>0000000001759</processed-our-number>
  <decimal-character>,</decimal-character>
  <email-sent-at type="datetime">2012-07-03T01:41:05-03:00</email-sent-at>
  <html-state type="integer">1</html-state>
  <id type="integer">51663</id>
  <meta type="binary" nil="true" encoding="base64"></meta>
  <percent-interest-day type="decimal" nil="true"></percent-interest-day>
  <service-id type="integer">1349</service-id>
  <assignor-code>4331 / 430185-4</assignor-code>
  <homologation type="boolean">false</homologation>
  <html-delayed-at type="datetime">2012-07-03T01:40:58-03:00</html-delayed-at>
  <our-number>0000175</our-number>
  <pdf-state type="integer" nil="true"></pdf-state>
  <document-date type="date" nil="true"></document-date>
  <due-date-business-day nil="true"></due-date-business-day>
  <neighborhood nil="true"></neighborhood>
  <currency>R$</currency>
  <customer-id type="integer" nil="true"></customer-id>
  <description nil="true"></description>
  <document-amount type="decimal" nil="true"></document-amount>
  <document-type nil="true"></document-type>
  <paid-at type="date" nil="true"></paid-at>
  <instructions nil="true"></instructions>
  <overdue-notified-at type="datetime" nil="true"></overdue-notified-at>
  <pdf-delayed-at type="datetime" nil="true"></pdf-delayed-at>
  <status>c</status>
  <bank-billet-account-id type="integer">1212</bank-billet-account-id>
  <email-delayed-at type="datetime">2012-07-03T01:41:04-03:00</email-delayed-at>
  <expire-at type="date">2012-07-26</expire-at>
  <html-created-at type="datetime">2012-07-03T01:41:04-03:00</html-created-at>
  <other-amount-to-add type="decimal" nil="true"></other-amount-to-add>
  <state nil="true"></state>
  <thousand-character>.</thousand-character>
  <external-link>http://bole.to/86i613v3</external-link>
  <hashcode>86i613v3</hashcode>
  <carnet-external-link nil="true"></carnet-external-link>
</bank-billet>
```

Criar um boleto bancário
--------------

* `POST /bank_billets.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<bank-billet>
  <bank-billet-account-id>1212</bank-billet-account-id>
  <amount>500.0</amount>
  <expire-at>2012-07-26</expire-at>
  <name>Rafael Lima</name>  
</bank-billet>
```

Essa requisição irá retornar o status `201 Created`, com a URL do boleto bancário criado no header `Location` e com os dados do boleto bancário no `body`. Veja **Dados de um boleto bancário** para mais informações.

Atualizar boleto bancário
---------------

* `PUT /bank_billets/1.json`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<bank-billet>
  <name>Nome Corrigido</name>  
</bank-billet>
```

Essa requisição irá retornar o status `200 OK` se a atualização for realizada. Caso contrário retornará os status `422 Unprocessible Entity`.

Somente boletos em rascunho podem ser alterados.

Excluir boleto bancário
-------------

* `DELETE /bank_billets/1.json`

Essa requisição irá retornar o status `200 OK`.
