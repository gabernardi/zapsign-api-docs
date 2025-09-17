# Cancelar documentos

Este endpoint permite interromper o fluxo de assinatura em casos de problemas no documento. Pode ser usado administradores, proprietários ou usuários inseridos em grupos de permissões específicos, com acesso ao token da empresa.

***

#### Observações

* **Permissões**: Pode ser usado por administradores, proprietários ou grupo com acesso.
* **Estado final**: O documento fica com status "recusado" e não pode mais ser assinado.
* **Marca d'água**: Adiciona marca d'água no PDF final indicando o cancelamento.
* **Webhook**: Pode disparar o webhook "doc\_signed" após o cancelamento (PDF atualizado).
* **User-Agent**: Header obrigatório para evitar spam.

### Exemplo de requisição

<mark style="color:yellow;">`POST`</mark>  `https://api.zapsign.com.br/api/v1/refuse/`

#### Body

```json
{
  "doc_token": "bfe4e2c7-33be-4a70-8669-a0491f92e795",
  "rejected_reason": "Documento cancelado pela empresa"
}
```

#### Headers

| Name                                            | Type   | Description                                                                                            |
| ----------------------------------------------- | ------ | ------------------------------------------------------------------------------------------------------ |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p></p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

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
