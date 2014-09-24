# Notificação

Notificações que o Cobre Grátis envia para um sistema externo após ocorrer alguma alteração nos boletos.
Essas notificações são realizadas através de uma requisição HTTP POST na URL configurada no cadastro de notificações.

O cadastro de notificações fica localizado no menu "Integração".

O Cobre Grátis poderá notificar quando um boleto foi marcado como rascunho, aberto, cancelado ou pago,
dependendo da configuração feita no cadastro da notificação.

O histórico das notificações realizadas ficam salvos no cadastro da notificação.

Parâmetros passados na requisição:

* `id` => ID no Cobre Grátis
* `parcel` => Número da Parcela (1 para boletos não parcelados)
* `code` => Código de Segurança (configurado no cadastro da notificação)
* `meta` => Valor do campo meta (passado na criação do boleto)
* `our_number` => Nosso Número
* `expire_at` => Data de Vencimento
* `document_number` => Número do Documento
* `document_date` => Data do Documento
* `document_amount` => Valor do Documento
* `name` => Nome do Pagador
* `paid_amount` => Valor Pago
* `paid_at` => Data do Pagamento
* `status` => Situação do Boleto (draft, opened, cancelled, paid)
* `bank_rate` => Taxa cobrada pelo banco
* `event` => Tipo de evento (draft, opened, cancelled, paid)
* `service_id` => ID do modelo
* `bank_billet_account_id` => ID da conta de cobrança
* `bank_billet_subscription_id` => ID da Assinatura(Caso de boleto gerado por Assinatura)
* `parcels_ids` => IDs de todas as parcelas(Caso de boleto parcelado)
* `public_url` => URL pública do Boleto

