# Adicionar anexo (documento extra) via Modelo

## Adicionar documento extra via modelo

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/models/{{doc_principal_token}}/upload-extra-doc/`

Esse endpoint permite que você anexe um documento extra ao documento principal **a partir de um Modelo dinâmico (isto é, um .docx com variáveis que você sobe na ZapSign, que terá suas variáveis automaticamente substituídas e convertido para .pdf)**. Você deverá enviar os dados em JSON, bem como receberá eles nesse mesmo formato.&#x20;

É possível anexar até 14 documentos (um por vez, isto é, uma requisição para cada anexo), totalizando 15 documentos que o signatário pode assinar de uma vez só.&#x20;

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

| Name                                           | Type   | Description                                                                                                                                                                                                                                                                                    |
| ---------------------------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| template\_id<mark style="color:red;">\*</mark> | string | <p>Identificador/token do template (modelo dinâmico)</p><p>Ex: https://app.zapsign.com.br/conta/modelos/{TEMPLATE_ID}</p><p></p><p>Para acessar a sua lista de templates clique aqui:<br><a href="https://app.zapsign.com.br/conta/modelos/">https://app.zapsign.com.br/conta/modelos/</a></p> |
| data\[]\['de']                                 | string | <p>Nome da variável a ser substituída. </p><p>Ex: "{{NOME COMPLETO}}"</p>                                                                                                                                                                                                                      |
| data\[]\['para']                               | string | Valor a ser preenchido no lugar da variável. Ex: "João dos Santos"                                                                                                                                                                                                                             |

{% tabs %}
{% tab title="200: OK Documento extra adicionado com sucesso." %}
```json
{
    "open_id": 17,
    //utilize esse token caso queira posicionar assinaturas neste documento extra
    "token": "50c7d90e-ead6-46b5-99d6-33d2d3b9a31f", 
    "name": "Anexo ao Contrato de Admissão João",
    "original_file": "https://zapsign.s3.amazonaws.com/aaa/48025712-b429-4216-8a33-d90c575d0b7f/0e2d0a87-a0f6-4a49-a05f-7a439fd7308e.pdf",
    "signed_file": null
},
```
{% endtab %}

{% tab title="404: Not Found Documento ou modelo especificados não foram encontrados" %}

{% endtab %}

{% tab title="400: Bad Request Campos obrigatórios não estão presentes na requisição" %}

{% endtab %}

{% tab title="403: Forbidden Modelo foi deletado, está inativo ou pertence a outra Company" %}

{% endtab %}

{% tab title="402: Payment Required Company atual não possui plano API" %}

{% endtab %}

{% tab title="400: Bad Request Documento pai já foi assinado, foi excluído ou também é um documento extra" %}

{% endtab %}

{% tab title="400: Bad Request Requisição atual ultrapassaria o máximo de anexos permitidos " %}

{% endtab %}
{% endtabs %}

Não há outros parâmetros a serem enviados na requisição, pois todos eles serão herdados do documento principal.

{% hint style="info" %}
**Obs:** não confunda a adição de anexos com a [assinatura em lote via API](https://docs.zapsign.com.br/signatarios/assinar-em-lote-via-api), já que nesta última a assinatura é feita programaticamente pelo seu sistema via código. Os casos de uso são distintos.
{% endhint %}

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-750bab98-f46d-4a69-99d8-4d3f230ff77f" %}

### Exemplo de retorno

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```javascript
{
    "open_id": 17,
    //utilize esse token caso queira posicionar assinaturas neste documento extra
    "token": "50c7d90e-ead6-46b5-99d6-33d2d3b9a31f", 
    "name": "Anexo ao Contrato de Admissão João",
    "original_file": "https://zapsign.s3.amazonaws.com/aaa/48025712-b429-4216-8a33-d90c575d0b7f/0e2d0a87-a0f6-4a49-a05f-7a439fd7308e.pdf",
    "signed_file": null
},
```

### Perguntas frequentes

#### O que é um anexo/documento extra?

Caso você utilize a plataforma web da ZapSign, irá perceber que é possível subir vários PDFs de uma vez para serem assinados pelos mesmos signatários:

![Exemplo na plataforma web de um envelope com 3 PDFs.](<../.gitbook/assets/image (49).png>)

Assim, quando o signatário vai assinar o documento, ele se depara com a lista de todos eles, para assinar de uma vez só:

![](<../.gitbook/assets/image (60).png>)

**O documento principal será o número 1** e os **documentos extras aparecerão para o signatário como documentos de número 2, 3, etc.** Ao fazer um GET no documento principal, os documentos extras aparecerão no parâmetro "extra\_docs".



**O documento extra consome crédito de API?** \
Sim. Cada documento extra conta igual a um documento principal. Assim, caso você adicione 14 documentos extras a um documento principal, isso contará como "15 créditos" de API, e não um só.&#x20;

**Eu consigo posicionar assinaturas no documento extra?** \
Sim! Basta encaminhar o token do documento extra no endpoint de posicionar assinaturas.

**Adicionei um anexo sem querer. Tem como remover/desfazer o engano?**\
Não. Por enquanto não é possível remover um anexo, depois de adicionado.
