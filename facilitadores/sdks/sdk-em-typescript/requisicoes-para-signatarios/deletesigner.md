---
description: Excluir signatário
---

# deleteSigner

### Visão geral

Parâmetros:&#x20;

* String - token do documento

Retorno:

* String[ ](../../sdk-em-java/classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para excluir esse signatário precisamos:

* definir seu token api.
* definir o token do signatário.
* chamar o método.

### Uso:

Salve seu [Api Token](../../../../):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Salve o token de seu signatário:

```typescript
const signerToken: string = "TOKEN DO SIGNATÁRIO";
```



Chame o método deleteSigner e receba como resposta uma string contendo "Signatário removido com sucesso."[ ](../../sdk-em-java/classes-usadas/response/signer-response.md)ou uma mensagem de erro:

```typescript
async function exempleDeleteSigner() {
    try {
        response: string = new SignerRequest(apiToken).deleteSigner(signerToken);
        console.log(response);
    }
    catch(Err) {
        console.log(Err);
    }  
}
```



### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import SignerRequest from "sdk-node-typescript-zapsign/src/signer/SignerRequest";
<strong>
</strong><strong>const apiToken: string = "SEU TOKEN";
</strong>const signerToken: string = "TOKEN DO SIGNATÁRIO";

async function exempleDeleteSigner() {
    try {
        response: string = new SignerRequest(apiToken).deleteSigner(signerToken);
        console.log(response);
    }
    catch(Err) {
        console.log(Err);
    }  
}
</code></pre>

