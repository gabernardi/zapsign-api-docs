---
description: Detalhar documento
---

# detailDoc

### Visão geral

Parâmetros:&#x20;

* String - token do documento

Retorno:

* [docResponse ](../classes-usadas/response/docresponse.md)- caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api.
* token do documento.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import docs.DocRequests;
import response.DocResponse;

import services.JsonConverter;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Salve o token do documento original:

```
String docToken = "TOKEN DOCUMENTO"
```

Chame o método detailDoc e receba como resposta a classe [DocResponse ](../classes-usadas/response/docresponse.md)ou uma mensagem de erro:

```
try {
    DocResponse docResponse = new DocRequests(apiToken).detailDoc(docToken);

    String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import docs.DocRequests;
import response.DocResponse;
import services.JsonConverter;

public class DetailDoc {
    public static void main(String[] args) throws Exception {
    String apiToken = "SEU TOKEN";
    String docToken = "TOKEN DOCUMENTO"

        try {
            DocResponse docResponse = new DocRequests(apiToken).detailDoc(docToken);

            String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
