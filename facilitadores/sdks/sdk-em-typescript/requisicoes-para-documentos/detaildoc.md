---
description: Detalhar documento
---

# detailDoc

### Visão geral

Parâmetros:&#x20;

* Token do documento - string

Retorno:

* [docResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docresponse) - caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api.
* token do documento.
* chamar o método.

### Uso:

Salve seu [Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Salve token do documento original:

<pre class="language-typescript"><code class="lang-typescript"><strong>const docToken: string = "TOKEN DOCUMENTO ORIGINAL";
</strong></code></pre>



Chame o método detailDoc e receba como resposta a classe [DocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docresponse) ou uma mensagem de erro:

```typescript
async function exempleDetailDoc() {
            try {
                        docResponse: DocResponse = await new DocRequests(apiToken).detailDoc(docToken);
                        jsonDocResponse: string = new JsonConverter().docResponseToJson(docResponse);
                        console.log(jsonDocResponse);
                } catch(Err) {
                         console.log(Err);
                }
}
```

###

### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
<strong>
</strong><strong>const apiToken: string = "SEU TOKEN";
</strong><strong>
</strong>const docToken: string = "TOKEN DOCUMENTO ORIGINAL";

async function exempleDetailDoc() {
      try {
            const docResponse: DocResponse = await new DocRequests(apiToken).detailDoc(docToken);
            const jsonDocResponse: string = new JsonConverter().docResponseToJson(docResponse);
            console.log(jsonDocResponse);
         } catch(Err) {
            console.log(Err);
         }
}
</code></pre>

