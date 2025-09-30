# Cancelar documentos

Este endpoint permite interromper o fluxo de assinatura em casos de problemas no documento. Pode ser usado administradores, proprietários ou usuários inseridos em grupos de permissões específicos, com acesso ao token da empresa.

***

#### Observações

* **Permissões**: Pode ser usado por administradores, proprietários ou grupo com acesso.
* **Estado final**: O documento fica com status "recusado" e não pode mais ser assinado.
* **Marca d'água**: Adiciona marca d'água "Documento recusado" no PDF final indicando o cancelamento.
* **Webhook**: Pode disparar o webhook "doc\_signed" após o cancelamento (PDF atualizado).
* Estado do documento: Deve estar "em andamento" para poder ser cancelado
* **User-Agent**: Header obrigatório para evitar spam.

###

<mark style="color:green;">**`POST`**</mark>` ``https://api.zapsign.com.br/api/v1/refuse/`

#### Headers

<table><thead><tr><th width="160">Name</th><th width="117">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p></p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="167">Name</th><th width="107">Type</th><th>Description</th></tr></thead><tbody><tr><td>doc_token<mark style="color:red;">*</mark></td><td>string</td><td>Token do documento</td></tr><tr><td>rejected_reason<mark style="color:red;">*</mark></td><td>string</td><td>Motivo do cancelamento do documento. Esta informação estará disponível na plataforma web em detalhes do documento</td></tr><tr><td>notify_signer</td><td>boolean</td><td>Se true, notifica os signatários por e-mail quando o documento for cancelado. Se false, nenhuma notificação é enviada. Default: false.</td></tr></tbody></table>

#### Exemplo do body

```json
{
  "doc_token": "bfe4e2c7-33be-4a70-8669-a0491f92e795",
  "rejected_reason": "Documento cancelado pela empresa"
}
```

#### Resposta (200)

**Exemplo de sucesso:**

```json
{
  "message": "Documento cancelado com sucesso!"
}
```

#### Códigos de erro

* 400 `missing_doc_token`: Você deve encaminhar o doc\_token (string)
* 400 `missing_rejected_reason`: Você deve encaminhar o rejected\_reason (string)
* 400 `invalid_json`: O JSON enviado está inválido
* 403 `document_already_signed`: Não se pode cancelar um documento assinado
* 403 `document_already_refused`: Não se pode cancelar um documento que já foi cancelado/recusado
* 403 `refuse_not_allowed`: A reprovação deste documento não é permitida
* 404 `document_not_found`: Documento não encontrado
* 500 `internal_error`: Erro interno ao processar a solicitação
