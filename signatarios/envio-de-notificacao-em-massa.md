# Envio de notificação em massa

Este endpoint permite o envio de notificação em massa para todos os signatários pendentes do documento, útil quando um documento tem muitos signatários, podendo disparar notificação para todos os signers que estão pendentes para o documento. Respeita a ordem de assinatura e grupos de assinatura quando ativos.

***

### Exemplo de requisição

<mark style="color:yellow;">`POST`</mark>  [`https://api.zapsign.com.br/api/v1/docs/{token}/resend-notifications-bulk/`](https://api.zapsign.com.br/api/v1/docs/%7Btoken%7D/resend-notifications-bulk/)

**Corpo**: não requer body específico

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Resposta (200)

**Exemplo com falhas parciais:**

```json
{
  "success": true,
  "total_signers": 3,
  "sent_count": 2,
  "failed_count": 1,
  "failed_signers": [
    { "name": "Fulano de Tal", "reason": "Sem email ou telefone" }
  ],
  "has_order_active": true,
  "has_signature_groups": false
}
```

**Exemplo com sucesso total:**

```json
{
  "success": true,
  "total_signers": 5,
  "sent_count": 5,
  "failed_count": 0,
  "failed_signers": [],
  "has_order_active": false,
  "has_signature_groups": true
}
```

#### Códigos de erro

* 400 `document_not_in_progress`: Documento não está em andamento
* 400 `no_pending_signers`: Não há signatários pendentes para notificar
* 403 `permission_denied`: Token inválido/ausente ou documento não pertence à empresa
* 429 `cooldown_period`: Aguarde o período de cooldown (mensagem inclui tempo restante)
* 500 `internal_error`: Erro interno ao enviar as notificações
* 500 `unexpected_error`: Erro inesperado

#### Observações

* `success` pode ser false quando nenhuma notificação é enviada com sucesso
* Respeita ordem de assinatura e grupos (quando ativos)
