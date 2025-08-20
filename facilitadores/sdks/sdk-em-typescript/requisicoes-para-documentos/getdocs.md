---
description: Listar documentos
---

# getDocs

### Visão geral

Retorno:

* [DocsResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docsresponse) - caso sucesso
* Exception - caso falha

Para pegar os dados de um documento precisamos:

* definir seu token api.
* token do documento.
* chamar o método.

### Uso:

Salve seu[ Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Chame o método getDocs e receba como resposta a classe [DocsResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docsresponse) ou uma mensagem de erro:

```typescript
import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";

async function exempleAddExtraDoc() {
    try {
                        docResponse: DocResponse = await new DocRequests(apiToken).getDocs();
                        jsonDocResponse: string = new JsonConverter().docsResponseToJson(docResponse);
                        console.log(jsonDocResponse);
                } catch(Err) {
                         console.log(Err);
                }
}
```
