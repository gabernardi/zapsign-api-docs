---
description: Detalhar signatário
---

# detailSigner

### Visão geral

Parâmetros:&#x20;

* String - token do signatário

Retorno:

* [Signer ](../../sdk-em-java/classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para obter esse signatário precisamos:

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



Chame o método detailSigner e receba como resposta a classe [Signer](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signer) ou uma mensagem de erro:

```typescript
async function exempleDetailSigner() {
    try {
           const signerRequest: SignerRequest = await new SignerRequest(apiToken).detailSigner(signerToken);
           const jsonDocResponse: string = new JsonConverter().signerToJson(docResponse);
           console.log(jsonDocResponse);
         } catch(Err) {
           console.log(Err);
     }
   }
}
```



### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import SignerRequest from "sdk-node-typescript-zapsign/src/signer/SignerRequest";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
<strong>
</strong><strong>const apiToken: string = "SEU TOKEN";
</strong><strong>
</strong>const signerToken: string = "TOKEN DO SIGNATÁRIO";

async function exempleDetailSigner() {
    try {
           const signerRequest: SignerRequest = await new SignerRequest(apiToken).detailSigner(signerToken);
           const jsonDocResponse: string = new JsonConverter().signerToJson(docResponse);
           console.log(jsonDocResponse);
         } catch(Err) {
           console.log(Err);
     }
   }
}
</code></pre>

