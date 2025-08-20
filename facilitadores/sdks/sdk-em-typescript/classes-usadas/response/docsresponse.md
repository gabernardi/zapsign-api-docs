---
description: Classe de resposta de lista de documentos
---

# DocsResponse

### Propriedades:

| nome     |                                                                              tipo                                                                              | descrição                                       |
| -------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------: | ----------------------------------------------- |
| count    |                                                                             number                                                                             | Quantidade de documentos encontrados            |
| next     |                                                                             string                                                                             | url para próxima requisição se tiver paginação  |
| previous |                                                                             string                                                                             | url para requisição anterior se tiver paginação |
| results  | [DocResponse](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/response/docresponse)\[] | Array de documentos encontrados                 |

