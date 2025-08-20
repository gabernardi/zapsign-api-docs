---
description: >-
  Essa API permite que Parceiros de Revenda Direta gerenciem o status de
  pagamento dos clientes de forma automatizada, proporcionando maior controle
  sobre a adimplência e continuidade dos serviços
---

# Atualizar status de pagamento

**Exemplo de uso**

No modelo de Parceria de Revenda Direta da ZapSign, você pode usar esta API para atualizar o status de pagamento dos seus clientes. Se um cliente se tornar inadimplente, a API permite suspender automaticamente os benefícios do plano, garantindo que os serviços sejam restritos até a regularização.\
\
Desta forma, caso seu cliente esteja inadimplente, será possível suspender os benefícios do plano atribuido a ele.

#### Como configurar

Para utilizar essa funcionalidade, certifique-se de ter em mãos o API Token do parceiro e do cliente cujo status de pagamento você deseja atualizar. Esses tokens são essenciais para realizar as alterações necessárias diretamente via API, mantendo o controle sobre a experiência do cliente e a integridade dos serviços prestados.

**Funcionamento do Endpoint**

Ao utilizar esse endpoint, você nos envia o `api_token` da conta do cliente junto com o parâmetro `payment_status`, que pode ser "inadimplente" ou "adimplente".

Nosso sistema irá validar se o token usado para autenticação na API pertence à conta mãe da conta associada ao token enviado no corpo da requisição (a conta do cliente). Se essa condição for atendida, a requisição será aceita.

* **Se o status for "inadimplente"**: O plano contratado pelo cliente será bloqueado, restringindo o acesso aos benefícios até que o pagamento seja regularizado.
* **Se o status for "adimplente"**: O plano contratado será desbloqueado, restaurando o acesso completo aos serviços.

## Alterar status de pagamento de um parceiro

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/partner/update-payment-status/`

**Headers**

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

| Name               | Type   | Description                     |
| ------------------ | ------ | ------------------------------- |
| client\_api\_token | string | Token de API do parceiro        |
| payment\_status    | string | "adimplente" \| "inadimplente"  |

{% tabs %}
{% tab title="Exemplo de payload:" %}
```json
{
    "client_api_token": "f44f44e-sve2-4d01-8753-9e8fdf825e44cfe41581-fc98-4f81-8f0f-b8a184046421",
    "payment_status": "inadimplente"
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="200: OK Atualização realizada com sucesso" %}
{% code overflow="wrap" %}
```json
Status atualizado com sucesso.
```
{% endcode %}
{% endtab %}

{% tab title="400: Bad Request - Organização parceira sem plano ativo" %}
```
A organização especificada não possui um plano ativo.
```
{% endtab %}

{% tab title="401: Unauthorized - Credenciais Inválidas" %}
```
Credenciais inválidas.
```
{% endtab %}

{% tab title="403: Forbidden- Organização não é parceira " %}
```
A organização especificada não é parceira da organização atual.
```
{% endtab %}

{% tab title="404: Not Found - Organização parceira não encontrada" %}
```
A organização especificada não foi encontrada.
```
{% endtab %}
{% endtabs %}
