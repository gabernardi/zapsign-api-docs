---
description: Assinar em lote via API
---

# signInBatch

### Visão geral

Parâmetros:&#x20;

* [SignBatch](signinbatch.md)

Retorno:

* String[ ](../classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para assinar em lote precisamos:

* definir seu token api.
* definir o token do usuário.
* definir os tokens dos signatários.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```java
import body.signer.SignBatch;
import signers.SignerRequest;

import java.util.ArrayList;
```

Salve seu [Api Token](../../../../):

```java
String apiToken = "SEU TOKEN";
```

Salve o token de seu usuário, ([onde achar](../../../../signatarios/assinar-em-lote-via-api.md))

```java
String userToken = "TOKEN USUÁRIO";
```

Salve o token de seus signatários

```java
String signer_token1 = "TOKEN DO SIGNATÁRIO 1";
String signer_token2 = "TOKEN DO SIGNATÁRIO 2";

ArrayList<String> signers_token = new ArrayList<>();
        signers_token.add(signer_token1);
        signers_token.add(signer_token2);
```

Crie a classe [SignInBatch](signinbatch.md):

```java
SignBatch signBatch = SignBatch.builder()
                .user_token(userToken)
                .signer_tokens(signers_token)
                .build();
```

Chame o método signInBatch e receba como resposta uma string contendo uma mensagem de sucesso ou uma mensagem de erro:

```java
try {
    Signer signerResponse = new SignerRequest(apiToken).signInBatch(signBatch);
    String jsonDocResponse = new JsonConverter().signerToJson(signerResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```java
import body.signer.SignBatch;
import signers.SignerRequest;

import java.util.ArrayList;

public class SignInBatch {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";
        String userToken = "TOKEN USUÁRIO";
        String signer_token1 = "TOKEN DO SIGNATÁRIO 1";
        String signer_token2 = "TOKEN DO SIGNATÁRIO 2";

        ArrayList<String> signers_token = new ArrayList<>();
        signers_token.add(signer_token1);
        signers_token.add(signer_token2);

        SignBatch signBatch = SignBatch.builder()
                .user_token(userToken)
                .signer_tokens(signers_token)
                .build();

        try {
            String response = new SignerRequest(apiToken).signInBatch(signBatch);
            System.out.println(response);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
