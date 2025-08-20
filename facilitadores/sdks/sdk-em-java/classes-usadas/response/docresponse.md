---
description: Classe de resposta de documentos
---

# DocResponse

Classe herdada de [Doc](../body/doc.md).

### Propriedades:

<table><thead><tr><th width="192">nome</th><th width="275.3333333333333" align="center">tipo</th><th>descrição</th></tr></thead><tbody><tr><td>open_id</td><td align="center">int</td><td></td></tr><tr><td>token</td><td align="center">String</td><td>token do documento</td></tr><tr><td>status</td><td align="center">String</td><td>status do documento: "em-curso", "assinado", "recusado" ou "lixeira"</td></tr><tr><td>original_file</td><td align="center">String</td><td>url do arquivo original salvo na amazon</td></tr><tr><td>signed_file</td><td align="center">String</td><td>url do arquivo assinado salvo na amazon</td></tr><tr><td>created_through</td><td align="center">String</td><td>Como o documento foi criado: "web" ou "api"</td></tr><tr><td>extra_docs</td><td align="center">ArrayList&#x3C;<a href="extradocresponse.md">ExtraDocResponse</a>></td><td>Lista de documentos extras do documento</td></tr><tr><td>deleted</td><td align="center">boolean</td><td>Se True, o documento foi deletado</td></tr><tr><td>deleted_at</td><td align="center">String</td><td>data que o documento foi deletado</td></tr><tr><td>created_at</td><td align="center">String</td><td>data que o documento foi criado</td></tr><tr><td>last_update_at</td><td align="center">String</td><td>ultima data que o documento foi atualizado</td></tr><tr><td>template</td><td align="center"><a href="template.md">Template</a></td><td>se o documento foi criado por um modelo, contem o token do modelo</td></tr><tr><td>answers</td><td align="center">ArrayList&#x3C;<a href="answers.md">Answers</a>></td><td>lista de variáveis e valores para a criação desse documento</td></tr><tr><td>auto_reminder</td><td align="center">int</td><td>numero de vezes que esse documento vai mandar email para os signatários</td></tr><tr><td>signers</td><td align="center">List&#x3C;<a href="signer-response.md">Signer</a>></td><td>representa a lista de signatário salvos no documento</td></tr></tbody></table>
