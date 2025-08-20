---
description: Uma visão geral da classe de requisições para signtários
---

# Requisições para Signatários

### Classe SignersRequests

Essa é a classe responsável para a emissões de requisições para a api da zapsign. Para construir essa classe deve-se apenas colocar o [token de api](../../../../) como referencia:

```
SignerRequests signerRequest = new SignerRequests(apiToken);
```

Utilizando a classe SignerRequests é possivel realizar as seguintes requisições:

* [detailSigner](detailsigner.md): Detalhar signatário
* [updateSigner](updatesigner.md): Atualizar signatário
* [addSigner](addsigner.md): Adicionar signatário
* [deleteSigner](deletesigner.md): Excluir signatário
* [signInBatch](signinbatch.md): Assinar em lote via API
