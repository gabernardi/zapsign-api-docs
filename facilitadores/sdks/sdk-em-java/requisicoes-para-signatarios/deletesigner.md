---
description: Excluir signatário
---

# deleteSigner

### Visão geral

Parâmetros:&#x20;

* String - token do documento

Retorno:

* String[ ](../classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para excluir esse signatário precisamos:

* definir seu token api.
* definir o token do signatário.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```java
import signers.SignerRequest;
```

Salve seu [Api Token](../../../../):

```java
String apiToken = "SEU TOKEN";
```

Salve o token de seu signatário:

```java
String signerToken = "TOKEN DO SIGNATÁRIO";
```

Chame o método deleteSigner e receba como resposta uma string contendo "Signatário removido com sucesso."[ ](../classes-usadas/response/signer-response.md)ou uma mensagem de erro:

```java
try {
    Signer signerResponse = new SignerRequest(apiToken).updateSigner(signerToken, signer);
    String jsonDocResponse = new JsonConverter().signerToJson(signerResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```java
import signers.SignerRequest;

public class DeleteSigner {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";
        String signerToken = "TOKEN DO SIGNATÁRIO";

        try {
            String response = new SignerRequest(apiToken).deleteSigner(signerToken);
            System.out.println(response);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
