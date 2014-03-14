# Webhook

Webhooks são notificações que o Cobre Grátis envia para um sistema externo após algum evento ocorrer no sistema.
Essas notificações são realizadas através de uma requisição HTTP POST no endereço configurado para Webhook no cadastro de Webhooks.

O cadastro de Webhooks fica localizado no menu "Integração".

O Cobre Grátis poderá notificar quando um boleto foi marcado como rascunho, aberto, cancelado ou pago,
dependendo da configuração feita no cadastro do Webhook.

Os logs das notificações realizadas ficaram salvos e 
poderão ser acessados através do Webhook que originou a notificação.

Parâmetros passados na requisição:

* `id` => ID no Cobre Grátis
* `parcel` => Número da Parcela (1 para boletos não parcelados)
* `code` => Código de Segurança (configurado no cadastro de Web Hooks)
* `meta` => Valor do campo meta (passado na criação do boleto)
* `our_number` => Nosso Número
* `expire_at` => Data de Vencimento
* `document_number` => Número do Documento
* `document_date` => Data do Documento
* `document_amount` => Valor do Documento
* `name` => Nome do Sacado
* `paid_amount` => Valor Pago
* `paid_at` => Data do Pagamento
* `status` => Status do Boleto (Rascunho, Aberto, Cancelado, Pago)
* `bank_rate` => Taxa cobrada pelo banco
