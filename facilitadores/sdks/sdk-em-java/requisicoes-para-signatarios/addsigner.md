---
description: Adicionar signatário
---

# addSigner

### Visão geral

Parâmetros:&#x20;

* String - token do documento
* [Signer](../classes-usadas/body/signer.md)

Retorno:

* [Signer ](../classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para adicionar esse signatário precisamos:

* definir seu token api.
* definir o token do documento.
* criar novo signatário.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```java
import body.signer.Signer;
import signers.SignerRequest;

import services.JsonConverter;
```

Salve seu [Api Token](../../../../):

```java
String apiToken = "SEU TOKEN";
```

Salve o token de seu documento:

```java
String docToken = "TOKEN DOCUMENTO";
```

Crie seu signatário com a classe [Signer](../classes-usadas/body/signer.md):

```java
Signer signer = Signer.builder()
                .name("New signer Name")
                .email("newEmail@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();
```

Chame o método addSigner e receba como resposta a classe [Signer ](../classes-usadas/response/signer-response.md)ou uma mensagem de erro:

```java
try {
    Signer signerResponse = new SignerRequest(apiToken).addSigner(signerToken, signer);
    String jsonDocResponse = new JsonConverter().signerToJson(signerResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```java
import body.signer.Signer;
import services.JsonConverter;
import signers.SignerRequest;

public class AddSigner {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";
        String docToken = "TOKEN DOCUMENTO";

        Signer signer = Signer.builder()
                .name("New signer Name")
                .email("newEmail@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();

        try {
            Signer signerResponse = new SignerRequest(apiToken).addSigner(docToken, signer);
            String jsonDocResponse = new JsonConverter().signerToJson(signerResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
