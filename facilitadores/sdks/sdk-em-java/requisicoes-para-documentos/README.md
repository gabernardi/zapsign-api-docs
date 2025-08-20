---
description: Uma visão geral da classe de requisições para documentos
---

# Requisições para Documentos

### Classe DocRequests

Essa é a classe responsável para a emissões de requisições para a api da zapsign. Para construir essa classe deve-se apenas colocar o [token de api](../../../../) como referencia:

```
DocRequests docRequest = new DocRequests(apiToken);
```

Utilizando a classe DocRequests é possível realizar as seguintes requisições:

* [createDocFromUploadPdf](createdocfromuploadpdf.md): Criar documento via Upload pdf
* [createDocFromUploadDocx](createdocfromuploaddocx.md): Criar documento via Upload docx
* [createDocFromUploadAsync](createdocfromuploadasync.md): Criar documento via Upload pdf Assíncrono
* [createDocFromPdfBase64](createdocfrompdfbase64.md): Criar documento via pdf de um base 64
* [createDocFromBase64Async](createdocfrombase64async.md): Criar documento via pdf de um base 64 Assíncrono
* [createDocFromTemplate](createdocfromtemplate.md): Criar documento via Modelo
* [createDocFromTemplateAsync](createdocfromtemplateasync.md): Criar documento via Modelo Assíncrono
* [addExtraDoc](addextradoc.md): Adicionar anexo (documento extra)
* [detailDoc](detaildoc.md): Detalhar documento
* [getDocs](getdocs.md): Listar documentos
* [deleteDoc](deletedoc.md): Excluir documento
* [placeSignatures](placesignatures.md): Posicionar assinaturas
