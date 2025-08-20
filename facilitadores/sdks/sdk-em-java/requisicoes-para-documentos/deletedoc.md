---
description: Excluir documento
---

# deleteDoc

### Visão geral

Parâmetros:&#x20;

* String - token do documento

Retorno:

* [DocsResponse ](../classes-usadas/response/docresponse.md)- caso sucesso
* Exception - caso falha

Para deletar um documento precisamos:

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

Salve o token do documento:

```
String docToken = "TOKEN DOCUMENTO";
```

Chame o método deleteDoc e receba como resposta a classe [DocResponse ](../classes-usadas/response/docresponse.md)ou uma mensagem de erro:

```
try {
    DocResponse docResponse = new DocRequests(apiToken).deleteDoc(docToken);

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

public class DeleteDoc {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";
        String docToken = "TOKEN DOCUMENTO";

        try {
            DocResponse docResponse = new DocRequests(apiToken).deleteDoc(docToken);

            String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
