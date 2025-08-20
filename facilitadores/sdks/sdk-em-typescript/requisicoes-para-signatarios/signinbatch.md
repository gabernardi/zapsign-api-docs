---
description: Assinar em lote via API
---

# SignInBatch

### Visão geral

Parâmetros:&#x20;

* [SignBatch](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signbatch)

Retorno:

* String[ ](../../sdk-em-java/classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para assinar em lote precisamos:

* definir seu token api;
* definir o token do usuário;
* definir os tokens dos signatários;
* chamar o método.

### Uso:

Salve seu [Api Token](../../../../):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Salve o token de seu usuário, ([onde achar](../../../../signatarios/assinar-em-lote-via-api.md))

```typescript
const userToken: string = "TOKEN USUÁRIO";
```



Salve o token de seus signatários

```typescript
const signerToken1: string = "TOKEN DO SIGNATÁRIO 1";
const signerToken2: string = "TOKEN DO SIGNATÁRIO 2";

let signersToken: string[]  = [];
signersToken.push(signerToken1, signerToken2);
```



Crie a classe [SignInBatch](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signbatch):

```typescript
const signBatch = SignBatchBuilder()
                .withUserToken(userToken)
                .withSignerTokens(signersToken)
                .build();
```



Chame o método signInBatch e receba como resposta uma string contendo uma mensagem de sucesso ou uma mensagem de erro:

```typescript
async function exempleSignInBatch() {
    try {
        signerResponse: string = new SignerRequest(apiToken).signInBatche(signBatch);
        jsonDocResponse: string = new JsonConverter().signerToJson(signerResponse);
        console.log(jsonDocResponse);
    }
    catch(Err) {
        console.log(Err);
    }   
}
```



### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import SignerRequest from "sdk-node-typescript-zapsign/src/signer/SignerRequest";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { SignBatchBuilder } from "sdk-node-typescript-zapsign/src/body/signer/builders/SignBatchBuilder";
<strong>
</strong><strong>const apiToken: string = "SEU TOKEN";
</strong>const userToken: string = "TOKEN USUÁRIO";

const signerToken1: string = "TOKEN DO SIGNATÁRIO 1";
const signerToken2: string = "TOKEN DO SIGNATÁRIO 2";

let signersToken: string[]  = [];
signersToken.push(signerToken1, signerToken2);

const signBatch = SignBatchBuilder()
                .withUserToken(userToken)
                .withSignerTokens(signersToken)
                .build();
                
async function exempleSignInBatch() {
    try {
        signerResponse: string = new SignerRequest(apiToken).signInBatch(signBatch);
        jsonDocResponse: string = new JsonConverter().signerToJson(signerResponse);
        console.log(jsonDocResponse);
    }
    catch(Err) {
        console.log(Err);
    }   
}
</code></pre>
