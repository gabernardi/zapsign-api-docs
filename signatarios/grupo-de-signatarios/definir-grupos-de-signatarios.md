# Definir Grupos de Signatários

Grupos de signatários permitem definir diferentes conjuntos de pessoas que devem assinar um documento, com a possibilidade de configurar uma ordem de assinatura entre esses grupos.

A definição dos grupos e de suas regras é feita diretamente no payload do endpoint de criação de documentos, sem a necessidade de chamadas adicionais à API.

### Como Funciona o Fluxo de Grupos?

1. Agrupamento: Você vincula os signatários a um grupo específico através do campo `order_group`.
2. Ordem de Assinatura: Se a propriedade `signature_order_active` for `true`, o documento só será liberado para o grupo seguinte (ex: `order_group: 2`) após as condições de assinatura do grupo anterior (ex: `order_group: 1`) serem totalmente retidas.
3. Paralelismo: Signatários que estão no mesmo `order_group` recebem a notificação e podem assinar o documento simultaneamente.



**⚠️ Regras de Validação para `minimum_signatures_required`:**

* Não pode ser igual a zero.
* Não pode ser maior do que a quantidade de signatários configurados para aquele `order_group`.

### Parâmetros do Payload

Abaixo estão os campos específicos utilizados para estruturar e gerenciar os grupos:

#### Campos Globais

* `signature_order_active` _(boolean)_: Define se a ordem de assinatura entre os grupos será sequencial. Envie `true` para ativar o fluxo ordenado ou `false` para liberar a assinatura para todos ao mesmo tempo.

#### Campos do Objeto `signers` (Array)

Dentro de cada objeto de signatário, utilize o campo abaixo para definir a qual grupo ele pertence:

* `order_group` _(integer)_: Número que representa o grupo de assinatura daquele signatário (ex: `1`, `2`, `3`...).



## Criar documento com Grupos de Signatários

<mark style="color:green;">`POST`</mark> [`https://api.zapsign.com.br/api/v1/docs/`](https://api.zapsign.com.br/api/v1/doc)

<table><thead><tr><th width="161">Name</th><th width="128">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

**Body**

| Name                                  | Type             | Description                                          |
| ------------------------------------- | ---------------- | ---------------------------------------------------- |
| name                                  | string           | Nome do documento                                    |
| url\_pdf                              | string           | URL do PDF a ser assinado                            |
| external\_id                          | string           | ID externo para controle do cliente                  |
| signers                               | Array            | Lista de signatários                                 |
| send\_automatic                       | boolean          | Envia automaticamente após a criação                 |
| lang                                  | string           | Idioma do fluxo (`pt`, `en`, `es`, ...)              |
| disable\_signer\_emails               | boolean          | Desativa o envio de e-mails aos signatários          |
| brand\_logo                           | string           | (opcional) URL do logotipo personalizado             |
| brand\_primary\_color                 | string           | Cor principal personalizada (ex: `#000000`)          |
| brand\_name                           | string           | Nome da marca exibido                                |
| created\_by                           | string           | E-mail de quem criou o documento                     |
| date\_limit\_to\_sign                 | string (ISO8601) | Data limite para assinatura (`YYYY-MM-DDTHH:mm:ssZ`) |
| signature\_order\_active              | boolean          | Define se há ordem de assinatura entre grupos        |
| observers                             | Array            | Lista de e-mails de observadores                     |
| reminder\_every\_n\_days              | number           | (opcional) Envia lembrete a cada N dias              |
| allow\_refuse\_signature              | boolean          | Permite recusar assinatura                           |
| disable\_signers\_get\_original\_file | boolean          | Impede que signatários acessem o PDF final           |
| signature\_groups                     | Array            | (opcional) Lista de grupos de signatários            |



**Propriedades de signature\_groups**

<table><thead><tr><th>Name</th><th width="198">Type</th><th>Description</th></tr></thead><tbody><tr><td>order_group</td><td>string</td><td>order_group do grupo a ser modificado</td></tr><tr><td>title</td><td>string</td><td>Nome do grupo</td></tr><tr><td>minimum_signatures_required</td><td>string</td><td>(opcional) Número mínimo de assinaturas</td></tr></tbody></table>



**Propriedades de signers**

| Name                      | Type    | Description                                                              |
| ------------------------- | ------- | ------------------------------------------------------------------------ |
| name                      | string  | Nome do signatário                                                       |
| email                     | string  | E-mail do signatário                                                     |
| auth\_mode                | string  | Modo de autenticação (ex: `assinaturaTela`)                              |
| order\_group              | number  | Número do grupo sequencial. Grupos com mesmo número assinam juntos       |
| custom\_message           | string  | Mensagem personalizada que será enviada ao signatário no corpo do e-mail |
| phone\_country            | string  | Código do país do telefone (ex: `"55"`)                                  |
| phone\_number             | string  | Número do telefone                                                       |
| require\_cpf              | boolean | Define se o CPF será obrigatório                                         |
| cpf                       | string  | CPF do signatário                                                        |
| send\_automatic\_email    | boolean | Envia automaticamente e-mail de assinatura                               |
| send\_automatic\_whatsapp | boolean | Envia automaticamente WhatsApp (se suportado)                            |
| lock\_email               | boolean | Bloqueia edição do e-mail na interface do signatário                     |

{% tabs %}
{% tab title="Exemplo de payload:" %}
```json
// Grupo 1: Signatário 1, Signatário 2
// Grupo 2: Signatário 3

{
  "name": "Contrato Teste",
  "url_pdf": "https://zapsign.s3.amazonaws.com/exemplo.pdf",
  "external_id": "TESTE_CENARIO_A",
  "signers": [
    {
      "name": "Signatário 1",
      "email": "email1@cliente.com",
      "auth_mode": "assinaturaTela",
      "order_group": 1,
      "custom_message": "Você é o primeiro do grupo. Assine assim que possível.",
      "phone_country": "55",
      "phone_number": "11999999999",
      "require_cpf": true,
      "cpf": "12345678900",
      "send_automatic_email": true,
      "send_automatic_whatsapp": false,
      "lock_email": false
    },
    {
      "name": "Signatário 2",
      "email": "email2@cliente.com",
      "auth_mode": "assinaturaTela",
      "order_group": 1,
      "custom_message": "Você está junto com o Signatário 1. Assine quando puder.",
      "phone_country": "55",
      "phone_number": "11888888888",
      "require_cpf": true,
      "cpf": "66778899001",
      "send_automatic_email": true,
      "send_automatic_whatsapp": false,
      "lock_email": false
    },
    {
      "name": "Signatário 3",
      "email": "email3@cliente.com",
      "auth_mode": "assinaturaTela",
      "order_group": 2,
      "custom_message": "Assine apenas após os dois primeiros signatários completarem.",
      "phone_country": "55",
      "phone_number": "11777777777",
      "require_cpf": true,
      "cpf": "99887766554",
      "send_automatic_email": true,
      "send_automatic_whatsapp": false,
      "lock_email": false
    }
  ],
  "signature_groups": [
    {
      "order_group": 1,
      "title": "Primeiro Grupo",
      "minimum_signatures_required": 1,
    },
    {
      "order_group": 2,
      "title": "Segundo Grupo",
    }
  ]
  "send_automatic": true,
  "lang": "pt",
  "disable_signer_emails": false,
  "brand_logo": "",
  "brand_primary_color": "#000000",
  "brand_name": "Minha Empresa",
  "created_by": "admin@minhaempresa.com",
  "date_limit_to_sign": "2025-12-31T23:59:59Z",
  "signature_order_active": true,
  "observers": ["observador@cliente.com"],
  "reminder_every_n_days": 3,
  "allow_refuse_signature": true,
  "disable_signers_get_original_file": false
}

```
{% endtab %}
{% endtabs %}

Respostas

{% tabs %}
{% tab title="200 OK" %}
```json
{
    "message": "OK"
}
```
{% endtab %}

{% tab title="400 Bad Request " %}
Exemplos de erros:

* Quando a numeração dos grupos não for contínua:

```json
{
    "message": "A numeração dos grupos deve ser contínua. Valores esperados: [0, 1, 2], valores fornecidos: [0, 2, 3]"
}
```

* Quando os grupos não começarem pelo valor 0:

```json
{
    "message": "A ordem dos grupos de signatários deve começar por 0. Primeiro grupo encontrado: 1"
}
```

* Quando faltarem signatários do documento a serem associados a algum grupo:

```json
{
    "message": "Há signatários neste documento que não foram incluídos em nenhum grupo."
}
```
{% endtab %}
{% endtabs %}
