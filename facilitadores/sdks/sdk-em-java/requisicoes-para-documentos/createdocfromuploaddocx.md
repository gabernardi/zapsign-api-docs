---
description: Criar documento via Upload docx
---

# createDocFromUploadDocx

### Visão geral

Parâmetros:&#x20;

* [DocFromDocx](../classes-usadas/body/docfromdocx.md)

Retorno:

* [DocResponse](../classes-usadas/response/docresponse.md) - caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api.
* definir os signatários.
* definir o documento.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import body.doc.DocFromDocx;
import body.signer.Signer;
import docs.DocRequests;
import response.DocResponse;

import services.JsonConverter;
import java.io.IOException;
import java.util.ArrayList;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Crie seus signatários com a classe [Signer](../classes-usadas/body/signer.md):

```
Signer signer1 = Signer.builder()
                .name("My First Signer")
                .build();

Signer signer2 = Signer.builder()
                .name("My Second Signer")
                .email("test@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();
                
ArrayList<Signer> signers = new ArrayList<>();
        signers.add(signer1);
        signers.add(signer2);
```

Defina seu documento com a classe [DocFromDocx](../classes-usadas/body/docfromdocx.md):

```typescript
DocFromDocx docFromDocx: = DocFromDocx.docFromDocxBuilder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .url_docx("https://zapsign.s3.amazonaws.com/2022/1/docs/d7660fd2-fe74-4691-bec8-5c42c0ae2b3f/39a35070-8987-476d-86e3-75d91f588a5a.docx")
                .build();

```

Chame o método createDocFromUploadDocx e receba como resposta a classe [DocResponse ](../classes-usadas/response/docresponse.md)ou uma mensagem de erro:

```
try {
    DocResponse docResponse = new DocRequests(apiToken).createDocFromUploadDocx(docFromDocx);
    String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import body.doc.DocFromDocx;
import body.signer.Signer;
import docs.DocRequests;
import response.DocResponse;
import services.JsonConverter;

import java.util.ArrayList;

public class CreateDocFromUploadDocx {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";

        Signer signer1 = Signer.builder()
                .name("My First Signer")
                .build();

        Signer signer2 = Signer.builder()
                .name("My Second Signer")
                .email("test@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();

        ArrayList<Signer> signers = new ArrayList<>();
        signers.add(signer1);
        signers.add(signer2);

        DocFromDocx docFromDocx = DocFromDocx.docFromDocxBuilder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .url_docx("https://zapsign.s3.amazonaws.com/2022/1/docs/d7660fd2-fe74-4691-bec8-5c42c0ae2b3f/39a35070-8987-476d-86e3-75d91f588a5a.docx")
                .build();

        try {
            DocResponse docResponse = new DocRequests(apiToken).createDocFromUploadDocx(docFromDocx);
            String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
