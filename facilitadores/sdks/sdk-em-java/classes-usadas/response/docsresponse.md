---
description: Classe de resposta de lista de documentos
---

# DocsResponse

### Propriedades:

| nome     |                   tipo                   | descrição                                       |
| -------- | :--------------------------------------: | ----------------------------------------------- |
| count    |                    int                   | Quantidade de documentos encontrados            |
| next     |                  String                  | url para próxima requisição se tiver paginação  |
| previous |                  String                  | url para requisição anterior se tiver paginação |
| results  | ArrayList<[DocResponse](docresponse.md)> | Lista de documentos encontrados                 |
