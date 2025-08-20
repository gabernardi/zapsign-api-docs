---
description: Adicionar anexo (documento extra)
---

# addExtraDoc

### Visão geral

Parâmetros:&#x20;

* [ExtraDoc](../classes-usadas/body/extradoc.md)

Retorno:

* [ExtraDocResponse ](../classes-usadas/response/extradocresponse.md)- caso sucesso
* Exception - caso falha

Para adicionar esse documento extra precisamos:

* definir seu token api.
* token do documento original.
* definir o documento extra.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import body.doc.ExtraDoc;
import docs.DocRequests;
import response.ExtraDocResponse;

import services.JsonConverter;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Salve o token do documento original:

```
String docToken = "TOKEN DOCUMENTO ORIGINAL";
```

Defina seu documento extra com a classe [ExtraDoc](../classes-usadas/body/extradoc.md):

```
ExtraDoc extraDoc = ExtraDoc.extraDocBuilder()
    .name("Extra doc")
    .url_pdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
    .build();

```

Chame o método addExtraDoc e receba como resposta a classe [ExtraDocResponse ](../classes-usadas/response/extradocresponse.md)ou uma mensagem de erro:

```
try {
    ExtraDocResponse extraDocResponse = new DocRequests(apiToken).addExtraDoc(docToken, extraDoc);
    String jsonExtraDocs = new JsonConverter().extraDocToJson(extraDocResponse);
    System.out.println(jsonExtraDocs);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import body.doc.ExtraDoc;
import docs.DocRequests;
import response.ExtraDocResponse;
import services.JsonConverter;

public class AddExtraDoc {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";

        String docToken = "TOKEN DOCUMENTO ORIGINAL";

        ExtraDoc extraDoc = ExtraDoc.extraDocBuilder()
                .name("Extra doc")
                .url_pdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                .build();

        try {
            ExtraDocResponse extraDocResponse = new DocRequests(apiToken).addExtraDoc(docToken, extraDoc);
            String jsonExtraDocs = new JsonConverter().extraDocToJson(extraDocResponse);
            System.out.println(jsonExtraDocs);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
