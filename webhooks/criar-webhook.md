# Criar webhook

Há **duas formas de criar um webhooks na ZapSign**, via **interface web** ou via **chamada do endpoint na** **API.** Dessa forma, você pode configurar webhooks de maneira flexível e eficiente, garantindo que seu sistema seja notificado em tempo real sobre os eventos importantes.

{% hint style="info" %}
**Lembre:se Não é necessário criar um webhook para cada documento,** somente para cada evento que deseja.&#x20;
{% endhint %}

**Nesta seção:**\
\
[Criando webhooks via web;\
](criar-webhook.md#criando-webhook-via-web)\
[Criando webhooks via Api;](criar-webhook.md#criando-via-api) \
[Configurando Headers para webhooks;](criar-webhook.md#configurando-headers-para-webhooks)



***

### Criando webhooks Via web

\
**Passo 1:** Em sua conta, navegue até área de **Configurações>Integrações>Api ZapSign>** [**Webhooks**](https://app.zapsign.com.br/conta/configuracoes/integration?tab=api-zapsign)**.**\
\
**Passo 2:** Insira o **endpoint** (URL) do seu servidor que receberá os dados dos webhooks. Esse endpoint deve estar preparado para processar requisições **POST** e lidar com os dados JSON que a ZapSign enviará.

**Passo 3:** Defina quais eventos deseja monitorar. A ZapSign permite que você escolha cinco tipos de eventos, são eles:

* [Documento Criado](eventos/document/documento-criado.md)
* [Documento Assinado](eventos/document/documento-assinado.md)
* [Documento Recusado](eventos/document/documento-recusado.md)
* [Documento removido](eventos/document/documento-removido.md)
* [Documento Expirado](eventos/document/documento-expirado.md)



{% hint style="warning" %}
**Atenção**: A opção "Todos" inclui somente os eventos de documentos (criado, assinado, removido e recusado). Não inclui o de "Email bounce" (para falhas em entregas de email). Para este evento, é necessário cadastrá-lo separadamente.
{% endhint %}

**Passo 4:** Configure se deseja adicionar um filtro para receber notificações apenas de documentos criados a partir de um template específico. Além disso, é possível definir reintentos em caso de falha na notificação.

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

***

### Criando webhooks via API

Você também pode criar seus endpoints via API, ajustando os cabeçalhos e eventos conforme a necessidade do seu fluxo de trabalho para uma integração perfeita!



<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/user/company/webhook/`

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body



```json

{
    "url": "https://SUA_URL.com",
    "type": "TIPO_EVENTO",
    "headers": [
        {
            "name": "Authorization",
            "value": "Bearer SEU_TOKEN_API"
        }
    ]
}

```

| Name                                   | Type           | Description                                                                                                                                                   |
| -------------------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| url<mark style="color:red;">\*</mark>  | string         | Ex: [https://api.seusite.com/webhook-zapsign/](https://api.seusite.com/webhook-zapsign/)                                                                      |
| type<mark style="color:red;">\*</mark> | string         | Tipos de eventos que você deseja receber. Opções: "" (todos - default) \| "doc\_signed" \| "doc\_created" \| "doc\_deleted"\| "doc\_refused"\|"email\_bounce" |
| doc\_token                             | string         | Token do documento para associar o Webhook. Caso enviado, os webhooks serão disparados apenas para o documento em questão                                     |
| headers                                | Array\<Header> | Headers a serem enviados ao disparar o webhook. A configuração de cada header está abaixo                                                                     |

{% tabs %}
{% tab title="200- Sucesso" %}
```json
{
    "id": // Você receberá um ID de resposta//
}
```
{% endtab %}

{% tab title="403 Forbidden" %}
Verifique se seu API TOKEN está correto.
{% endtab %}
{% endtabs %}

### Configurando headers para webhooks

Também é possível implementar headers nos webhooks, garantindo maior segurança no envio de dados e otimizando o desempenho entre as aplicações.\


**Webhook** - raiz do JSON:

*   **headers** - para cada header:

    * **name (string) -** Nome do cabeçalho HTTP a ser enviado.&#x20;

    &#x20;     **Ex:** Authorization

    * **value (string)** - Valor do cabeçalho HTTP a ser enviado.&#x20;

    &#x20;     **Ex:** Bearer SEU\_TOKEN\_DE\_AUTENTICACAO\


<mark style="color:green;">`POST`</mark>` ``{{api_url}}/api/v1/user/company/webhook/header/`

```
{
    "id": {{webhook_id}},
    "headers": [
        {
            "name": "Authorization",
            "value": "Bearer YOUR_AUTHENTICATION_TOKEN"
        }
    ]
}

```

### Exemplo de requisição

Faça um teste com a requisição pronta no Postman!

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-3413e0f8-be2d-4161-9ffa-b449443dc68d?ctx=documentation" %}

