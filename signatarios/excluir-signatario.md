# Excluir signatário

Este endpoint permite a exclusão de um signatário de um documento, útil quando um signatário foi adicionado incorretamente ou se não for mais necessário no processo de assinatura.

{% hint style="warning" %}
**Atenção: a exclusão é sem volta.** Caso queira reinserir o signatário no documento, ele terá um novo token/link para assinar.
{% endhint %}

***

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-f2604fc9-736f-4aaa-aece-8e53674637f2?ctx=documentation" %}

\ <mark style="color:red;">`DELETE`</mark> `https://api.zapsign.com.br/api/v1/signer/{{signer_token}}/remove/`

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>não é possível excluir um signatário que já assinou o documento!</strong></td><td></td><td></td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr><tr><td> <strong>não é possível excluir o único signatário do documento -</strong> se for o caso, antes adicione o segundo signatário e só depois exclua o primeiro.</td><td></td><td></td><td><a href="../.gitbook/assets/Ebook marketing digital moderno azul cinza capa para ebook.png">Ebook marketing digital moderno azul cinza capa para ebook.png</a></td></tr></tbody></table>

{% hint style="info" %}
Em algumas situações, o webhook "doc\_signed" pode ser disparado após um signatário ser excluído. Se isso acontecer, é porque o PDF signed\_file foi atualizado.
{% endhint %}

{% tabs %}
{% tab title="200 " %}
Signatário removido com sucesso.
{% endtab %}

{% tab title="400" %}
Erro: Não é possível remover um signatário que já assinou o documento
{% endtab %}
{% endtabs %}

