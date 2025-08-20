---
description: Listar documentos
---

# getDocs

### Visão geral

Retorno:

* [DocsResponse ](../classes-usadas/response/docsresponse.md)- caso sucesso
* Exception - caso falha

Para pegar os dados de um documento precisamos:

* definir seu token api.
* token do documento.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import docs.DocRequests;
import response.DocsResponse;

import services.JsonConverter;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Chame o método getDocs e receba como resposta a classe [DocsResponse ](../classes-usadas/response/docsresponse.md)ou uma mensagem de erro:

```
try {
    DocsResponse docsResponse = new DocRequests(apiToken).getDocs();

    String jsonDocResponse = new JsonConverter().docsResponseToJson(docsResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

<pre><code>import docs.DocRequests;
import response.DocsResponse;
import services.JsonConverter;

public class GetDocs {
    public static void main(String[] args) throws Exception {
<strong>    String apiToken = "SEU TOKEN";
</strong>
        try {
            DocsResponse docsResponse = new DocRequests(apiToken).getDocs();

            String jsonDocResponse = new JsonConverter().docsResponseToJson(docsResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
</code></pre>
