# Detalhe do Check

Este endpoint retorna todas as informações completas de uma consulta de antecedentes, incluindo:

* Os datasets que foram consultados.
* As informações encontradas em cada base de dados.
* As severidades associadas a cada achado.

A resposta inclui um JSON estruturado com todos os dados disponíveis, permitindo que você os analise e tome decisões automatizadas ou manuais conforme suas necessidades.

Recomendamos ler primeiro a seção [**Entendendo o Resultado**](background_checks/entendendo-o-resultado.md) para compreender como interpretar o score, os datasets, as severidades e como utilizar essas informações de forma eficaz.

<mark style="color:green;">**GET**</mark> `https://api.zapsign.com.br/api/v1/checks/{{check_id}}/details/`&#x20;

#### Header

<table><thead><tr><th width="154">Nome</th><th width="110">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>Authorization*</td><td>string</td><td>Token da API com o prefixo "Bearer". Ex: <code>Bearer c7f35c84-7893-4087-b4fb-d1f06c23</code></td></tr></tbody></table>

#### **Parâmetros de Path**

<table><thead><tr><th width="160">Nome</th><th width="105">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>check_id</td><td>string</td><td>Identificador da consulta</td></tr></tbody></table>

#### **Parâmetros de Query**

<table><thead><tr><th width="160">Nome</th><th width="86">Tipo</th><th>Descrição</th></tr></thead><tbody><tr><td>lang</td><td>string</td><td>Idioma dos resultados. Se não for especificado, os resultados estarão no idioma original das fontes. Valores possíveis: <code>es</code>, <code>en</code>, <code>pt-br</code>.</td></tr><tr><td>start_key</td><td>string</td><td>Paginação dos resultados. O parâmetro <code>next</code> na resposta indica a próxima página.</td></tr></tbody></table>

### **Possíveis estados de cada base de dados (result)**

* `not_started`: A coleta de dados da fonte foi ativada.
* `skipped`: A fonte de dados foi ignorada por falta de informações suficientes para realizar a consulta.
* `delayed`: A base de dados está demorando para responder.
* `completed`: Os dados foram obtidos com sucesso.
* `error`: Não foi possível obter dados da fonte.
* `expired`: A fonte de dados estava indisponível no momento da consulta.

### Response

{% tabs %}
{% tab title="credit_person_br" %}
```json
 {
    "details": [
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "personal_identity",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Validação de identidade com birô privado",
            "depth": 0,
            "document_type": "national-id",
            "found_company_name": "",
            "found_date_of_birth": "YYYY-MM-DDT00:00:00Z",
            "found_first_name": "NOME",
            "found_gender": "",
            "found_last_name": "SOBRENOME",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informação pessoal",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "N do CPF",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "Nome",
                                    "value": "NOME COMPLETO"
                                },
                                {
                                    "label": "Data de Nascimento",
                                    "value": "YYYY-MM-DD"
                                },
                                {
                                    "label": "Situação Cadastral",
                                    "value": "REGULAR"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-21T19:42:09.021073524Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "credit_history",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Histórico de crédito",
            "depth": 0,
            "document_type": "national-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Identificação",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Nome",
                                    "value": "NOME COMPLETO"
                                },
                                {
                                    "label": "CPF",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "Data de Nascimento",
                                    "value": "DD/MM/YYYY"
                                },
                                {
                                    "label": "Nome da Mãe",
                                    "value": "NOME DA MÃE"
                                },
                                {
                                    "label": "Sexo",
                                    "value": "NAO CONSTA"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Status do Documento",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Situação do CPF",
                                    "value": "REGULAR"
                                },
                                {
                                    "label": "Última atualização",
                                    "value": "31/05/2025"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Melhor Endereço e Telefone",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Endereço",
                                    "value": "ENDEREÇO ANONIMIZADO"
                                },
                                {
                                    "label": "Bairro",
                                    "value": "BAIRRO"
                                },
                                {
                                    "label": "Cidade",
                                    "value": "CIDADE"
                                },
                                {
                                    "label": "UF",
                                    "value": "UF"
                                },
                                {
                                    "label": "CEP",
                                    "value": "XXXXX-XXX"
                                },
                                {
                                    "label": "Complemento telefônico",
                                    "value": "-"
                                },
                                {
                                    "label": "Telefone residencial",
                                    "value": "-"
                                },
                                {
                                    "label": "Telefone comercial",
                                    "value": "-"
                                },
                                {
                                    "label": "Ramal",
                                    "value": "XX"
                                },
                                {
                                    "label": "Celular",
                                    "value": "XXXXXXXXX"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Anotações Negativas",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Ocorrências",
                                    "value": "Protestos"
                                },
                                {
                                    "label": "Quantidade",
                                    "value": "Nada consta"
                                },
                                {
                                    "label": "Data minor",
                                    "value": "-"
                                },
                                {
                                    "label": "Data maior",
                                    "value": "-"
                                },
                                {
                                    "label": "Valor (R$)",
                                    "value": "-"
                                },
                                {
                                    "label": "Mais Recente",
                                    "value": "-"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Consultas Realizadas para o CPF na Serasa Experian Resumo",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Total de consultas crédito",
                                    "value": "0"
                                },
                                {
                                    "label": "Total de consultas cheque",
                                    "value": "0"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Serasa Score com Positivo",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Chance de Pagamento",
                                    "value": "88.50%"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Renda",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Renda média",
                                    "value": "$ 1.000,00 - $ 2.000,00"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Informações Cadastrais Complementares",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Nome",
                                    "value": "NOME COMPLETO"
                                },
                                {
                                    "label": "CPF",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "RG",
                                    "value": "XXXXXXXXXXXX"
                                },
                                {
                                    "label": "Órgão emissor",
                                    "value": "-"
                                },
                                {
                                    "label": "Data da última alteração",
                                    "value": "31/05/2025"
                                },
                                {
                                    "label": "UF",
                                    "value": "-"
                                },
                                {
                                    "label": "Cidade de Nascimento",
                                    "value": "-"
                                },
                                {
                                    "label": "UF Nascimento",
                                    "value": "-"
                                },
                                {
                                    "label": "Escolaridade",
                                    "value": "-"
                                },
                                {
                                    "label": "Estado Civil",
                                    "value": "-"
                                },
                                {
                                    "label": "Dependentes",
                                    "value": "0"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-21T19:42:11.384442228Z"
        }
    ],
    "self": "/api/v1/checks/CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/details/",
    "next": ""
}


```
{% endtab %}

{% tab title="credit_company_br" %}
```json
{
    "details": [
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "business_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Emissão de Comprovante de Inscrição e de Situação Cadastral CNPJ",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "EMPRESA EXEMPLO LTDA",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informações gerais",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Data Situacao",
                                    "value": "04/05/2020"
                                },
                                {
                                    "label": "Tipo",
                                    "value": "MATRIZ"
                                },
                                {
                                    "label": "Nome Empresarial",
                                    "value": "EMPRESA EXEMPLO LTDA"
                                },
                                {
                                    "label": "Telefone",
                                    "value": "(XX) XXXX-XXXX"
                                },
                                {
                                    "label": "Situacao Cadastral",
                                    "value": "ATIVA"
                                },
                                {
                                    "label": "Endereço",
                                    "value": "ENDEREÇO ANONIMIZADO"
                                },
                                {
                                    "label": "Nome Fantasia",
                                    "value": "EMPRESA EXEMPLO"
                                },
                                {
                                    "label": "Porte",
                                    "value": "DEMAIS"
                                },
                                {
                                    "label": "Abertura",
                                    "value": "04/05/2020"
                                },
                                {
                                    "label": "Natureza Juridica",
                                    "value": "206-2 - Sociedade Empresária Limitada"
                                },
                                {
                                    "label": "CNPJ",
                                    "value": "XX.XXX.XXX/XXXX-XX"
                                },
                                {
                                    "label": "Ultima Atualizacao",
                                    "value": "2025-07-01T02:38:39.129Z"
                                },
                                {
                                    "label": "Status",
                                    "value": "OK"
                                },
                                {
                                    "label": "Email",
                                    "value": "email@anonimizado.com"
                                },
                                {
                                    "label": "Capital Social",
                                    "value": "5810000.00"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Atividades principais",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "63.11-9-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Tratamento de dados, provedores de serviços de aplicação e serviços de hospedagem na internet"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "atividades secundárias",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "62.03-1-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Desenvolvimento e licenciamento de programas de computador não-customizáveis"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "62.09-1-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Suporte técnico, manutenção e outros serviços em tecnologia da informação"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "64.63-8-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Outras sociedades de participação, exceto holdings"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Billing",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Free",
                                    "value": "Sim"
                                },
                                {
                                    "label": "DataBase",
                                    "value": "Sim"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "QSA",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Qualificação",
                                    "value": "22-Sócio"
                                },
                                {
                                    "label": "Nome",
                                    "value": "EMPRESA HOLDING LTDA."
                                },
                                {
                                    "label": "Nome do representante legal",
                                    "value": "NOME ANONIMIZADO"
                                },
                                {
                                    "label": "Qualificação do representante legal",
                                    "value": "05-Administrador"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Qualificação",
                                    "value": "05-Administrador"
                                },
                                {
                                    "label": "Nome",
                                    "value": "NOME ANONIMIZADO"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-04T19:38:20.625736143Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "business_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Validação de sanções com birô privado",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informação básica",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Empresa está atualmente sob alguma sanção",
                                    "value": "false"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-04T19:38:20.916500347Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "credit_history",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Serasa Company",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informações Cadastrais",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Situação Cadastral",
                                    "value": "SITUACAO DO CNPJ EM 10/05/2025: ATIVA"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Identificação",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Razão social",
                                    "value": "EMPRESA EXEMPLO LTDA"
                                },
                                {
                                    "label": "Número de inscrição no registro de empresas (NIRE)",
                                    "value": "XXXXXXXXXXX"
                                },
                                {
                                    "label": "Descrição do tipo de sociedade",
                                    "value": "SOCIEDADE EMPRESARIA LIMITADA"
                                },
                                {
                                    "label": "Opção tributária",
                                    "value": "-"
                                },
                                {
                                    "label": "Cod. natureza juridica",
                                    "value": "0206"
                                },
                                {
                                    "label": "Endereço",
                                    "value": "ENDEREÇO ANONIMIZADO"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Serasa Score com Positivo",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Fator de risco",
                                    "value": "75"
                                },
                                {
                                    "label": "Chance de Pagamento",
                                    "value": "0.75%"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Socios",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "CPF / CNPJ",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "Sócio / Acionista",
                                    "value": "EMPRESA HOLDING LTDA"
                                },
                                {
                                    "label": "Restrição",
                                    "value": "Não"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Administração",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "CPF / CNPJ",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "Administração",
                                    "value": "NOME ANONIMIZADO"
                                },
                                {
                                    "label": "Cargo",
                                    "value": "ADMINISTR"
                                },
                                {
                                    "label": "Restrição",
                                    "value": "Não"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-04T19:38:21.48534989Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "business_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Comprovante de Inscrição e de Situação Cadastral",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "error",
            "route": "id",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-04T19:38:54.369726428Z"
        }
    ],
    "self": "/api/v1/checks/CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/details/",
    "next": ""
}

```
{% endtab %}

{% tab title="person" %}
```json
{
    "details": [
        {
            "categorization": [
                {
                    "keyword": "CIVEL",
                    "category_id": "LR0602",
                    "category": "Labor: Other legal processes related to labor",
                    "participation": "Plaintiff",
                    "filing_year": "2022",
                    "filing_place": ""
                }
            ],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "legal_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Processos Judiciais e Administrativos",
            "depth": 0,
            "document_type": "national-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informações Gerais",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Número do processo",
                                    "value": "XXXXXXXX-XX.XXXX.X.XX.XXXX"
                                },
                                {
                                    "label": "Tipo de processo",
                                    "value": "PROCEDIMENTO DO JUIZADO ESPECIAL CIVEL"
                                },
                                {
                                    "label": "Assunto principal",
                                    "value": "DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MORAL (9992 DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MATERIAL (10502"
                                },
                                {
                                    "label": "Outros assuntos",
                                    "value": "DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MORAL (9992 DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MATERIAL (10502"
                                },
                                {
                                    "label": "Valor total da causa extraído do processo",
                                    "value": "-1.00"
                                },
                                {
                                    "label": "Nome do tribunal",
                                    "value": "Tribunal de Justiça de Minas Gerais"
                                },
                                {
                                    "label": "Nível do tribunal (instância)",
                                    "value": "1"
                                },
                                {
                                    "label": "Tipo do tribunal",
                                    "value": "ESPECIAL CIVEL"
                                },
                                {
                                    "label": "Corpo do Julgamento",
                                    "value": "2 UNIDADE JURISDICIONAL - 4 JD DA COMARCA DE MONTES CLAROS"
                                },
                                {
                                    "label": "Estado",
                                    "value": "Minas Gerais"
                                },
                                {
                                    "label": "Situação atual do processo",
                                    "value": "ARQUIVADO"
                                },
                                {
                                    "label": "Data de aviso",
                                    "value": "2022-07-04"
                                },
                                {
                                    "label": "Data da úlitma movimentação",
                                    "value": "2022-10-27"
                                },
                                {
                                    "label": "Data de Fechamento",
                                    "value": "2022-10-27"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Número do processo",
                                    "value": "XXXXXXXX-XX.XXXX.X.XX.XXXX"
                                },
                                {
                                    "label": "Tipo de processo",
                                    "value": "RECURSO INOMINADO"
                                },
                                {
                                    "label": "Assunto principal",
                                    "value": "DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MORAL (9992 DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MATERIAL (10502"
                                },
                                {
                                    "label": "Outros assuntos",
                                    "value": "DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MORAL (9992 DIREITO ADMINISTRATIVO E OUTRAS MATERIAS DE DIREITO PUBLICO (9985) - RESPONSABILIDADE DA ADMINISTRACAO (9991) - INDENIZACAO POR DANO MATERIAL (10502"
                                },
                                {
                                    "label": "Valor total da causa extraído do processo",
                                    "value": "-1.00"
                                },
                                {
                                    "label": "Nome do tribunal",
                                    "value": "Tribunal de Justiça de Minas Gerais"
                                },
                                {
                                    "label": "Nível do tribunal (instância)",
                                    "value": "2"
                                },
                                {
                                    "label": "Tipo do tribunal",
                                    "value": "CIVEL"
                                },
                                {
                                    "label": "Corpo do Julgamento",
                                    "value": "1 TITULAR 1 TR GRUPO JURISDICIONAL DE MONTES CLAROS|1 TURMA RECURSAL DO GRUPO JURISDICIONAL DE MONTES CLAROS"
                                },
                                {
                                    "label": "Estado",
                                    "value": "Minas Gerais"
                                },
                                {
                                    "label": "Situação atual do processo",
                                    "value": "ARQUIVADO"
                                },
                                {
                                    "label": "Data de aviso",
                                    "value": "2021-05-05"
                                },
                                {
                                    "label": "Data da úlitma movimentação",
                                    "value": "2022-02-24"
                                },
                                {
                                    "label": "Data de Fechamento",
                                    "value": "2022-02-24"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Decisões",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Data",
                                    "value": "2020-08-19T00:00:00Z"
                                },
                                {
                                    "label": "Conteúdo",
                                    "value": "JULGO IMPROCEDENTE O PEDIDO INICIAL E, EM CONSEQUENCIA, JULGO EXTINTO O PROCESSO, COM RESOLUCAO DO MERITO, NOS TERMOS DO ART. 487, INCISO I, DO CODIGO DE PROCESSO CIVIL."
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Data",
                                    "value": "2020-08-19T00:00:00Z"
                                },
                                {
                                    "label": "Conteúdo",
                                    "value": "DEFIRO AO AUTOR OS BENEFICIOS DA ASSISTENCIA JUDICIARIA GRATUITA."
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Partes",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Número do documento",
                                    "value": "XXXXXXXXXXXXXX"
                                },
                                {
                                    "label": "Nome",
                                    "value": "ENTIDADE PÚBLICA"
                                },
                                {
                                    "label": "Polaridade",
                                    "value": "PASSIVE"
                                },
                                {
                                    "label": "Tipo",
                                    "value": "DEFENDANT"
                                },
                                {
                                    "label": "Parte ativa",
                                    "value": "yes"
                                },
                                {
                                    "label": "Tipo específico",
                                    "value": "REU/RE"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Número do documento",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "Nome",
                                    "value": "NOME COMPLETO"
                                },
                                {
                                    "label": "Polaridade",
                                    "value": "ACTIVE"
                                },
                                {
                                    "label": "Tipo",
                                    "value": "AUTHOR"
                                },
                                {
                                    "label": "Parte ativa",
                                    "value": "yes"
                                },
                                {
                                    "label": "Tipo específico",
                                    "value": "AUTOR"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Número do documento",
                                    "value": "XXXXXXXXXXXXXX"
                                },
                                {
                                    "label": "Nome",
                                    "value": "ENTIDADE PÚBLICA"
                                },
                                {
                                    "label": "Polaridade",
                                    "value": "PASSIVE"
                                },
                                {
                                    "label": "Tipo",
                                    "value": "CLAIMED"
                                },
                                {
                                    "label": "Parte ativa",
                                    "value": "yes"
                                },
                                {
                                    "label": "Tipo específico",
                                    "value": "RECORRIDO(A)"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Número do documento",
                                    "value": "XXX.XXX.XXX-XX"
                                },
                                {
                                    "label": "Nome",
                                    "value": "NOME COMPLETO"
                                },
                                {
                                    "label": "Polaridade",
                                    "value": "ACTIVE"
                                },
                                {
                                    "label": "Tipo",
                                    "value": "CLAIMANT"
                                },
                                {
                                    "label": "Parte ativa",
                                    "value": "yes"
                                },
                                {
                                    "label": "Tipo específico",
                                    "value": "RECORRENTE"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Atualizações",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Data de Publicação",
                                    "value": "2022-10-27T00:00:00Z"
                                },
                                {
                                    "label": "Conteúdo",
                                    "value": "ARQUIVADO DEFINITIVAMENTE"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-05-06T22:13:30.528911729Z"
        },
    ],
    "self": "/api/v1/checks/CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/details/",
    "next": ""
}

```
{% endtab %}

{% tab title="company" %}
```json
{
    "details": [
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "United Nations Security Council Consolidate List",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.498205143Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Consolidated Screening Lists",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.59099409Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "business_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Emissão de Comprovante de Inscrição e de Situação Cadastral CNPJ",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "EMPRESA EXEMPLO LTDA",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informações gerais",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Data Situacao",
                                    "value": "04/05/2020"
                                },
                                {
                                    "label": "Tipo",
                                    "value": "MATRIZ"
                                },
                                {
                                    "label": "Nome Empresarial",
                                    "value": "EMPRESA EXEMPLO LTDA"
                                },
                                {
                                    "label": "Telefone",
                                    "value": "(XX) XXXX-XXXX"
                                },
                                {
                                    "label": "Situacao Cadastral",
                                    "value": "ATIVA"
                                },
                                {
                                    "label": "Endereço",
                                    "value": "ENDEREÇO ANONIMIZADO"
                                },
                                {
                                    "label": "Nome Fantasia",
                                    "value": "EMPRESA EXEMPLO"
                                },
                                {
                                    "label": "Porte",
                                    "value": "DEMAIS"
                                },
                                {
                                    "label": "Abertura",
                                    "value": "04/05/2020"
                                },
                                {
                                    "label": "Natureza Juridica",
                                    "value": "206-2 - Sociedade Empresária Limitada"
                                },
                                {
                                    "label": "CNPJ",
                                    "value": "XX.XXX.XXX/XXXX-XX"
                                },
                                {
                                    "label": "Ultima Atualizacao",
                                    "value": "2025-07-01T02:38:39.129Z"
                                },
                                {
                                    "label": "Status",
                                    "value": "OK"
                                },
                                {
                                    "label": "Email",
                                    "value": "email@anonimizado.com"
                                },
                                {
                                    "label": "Capital Social",
                                    "value": "5810000.00"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Atividades principais",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "63.11-9-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Tratamento de dados, provedores de serviços de aplicação e serviços de hospedagem na internet"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "atividades secundárias",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "62.03-1-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Desenvolvimento e licenciamento de programas de computador não-customizáveis"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "62.09-1-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Suporte técnico, manutenção e outros serviços em tecnologia da informação"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Code",
                                    "value": "64.63-8-00"
                                },
                                {
                                    "label": "Name",
                                    "value": "Outras sociedades de participação, exceto holdings"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "Billing",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Free",
                                    "value": "Sim"
                                },
                                {
                                    "label": "DataBase",
                                    "value": "Sim"
                                }
                            ]
                        }
                    ]
                },
                {
                    "title": "QSA",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Qualificação",
                                    "value": "22-Sócio"
                                },
                                {
                                    "label": "Nome",
                                    "value": "EMPRESA HOLDING LTDA."
                                },
                                {
                                    "label": "Nome do representante legal",
                                    "value": "NOME ANONIMIZADO"
                                },
                                {
                                    "label": "Qualificação do representante legal",
                                    "value": "05-Administrador"
                                }
                            ]
                        },
                        {
                            "cells": [
                                {
                                    "label": "Qualificação",
                                    "value": "05-Administrador"
                                },
                                {
                                    "label": "Nome",
                                    "value": "NOME ANONIMIZADO"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-21T22:11:39.814498154Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "business_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Validação de sanções com birô privado",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "found",
            "route": "id",
            "severity": "none",
            "tables": [
                {
                    "title": "Informação básica",
                    "rows": [
                        {
                            "cells": [
                                {
                                    "label": "Empresa está atualmente sob alguma sanção",
                                    "value": "false"
                                }
                            ]
                        }
                    ]
                }
            ],
            "update_date": "2025-07-21T22:11:40.143606628Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Common Position Terrorist EU",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.449626593Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "alert_in_media",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Búsqueda en medios GOOGLE RSS",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:44.634642926Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "World Bank Debarred Firms",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.484702298Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Office of Foreign Assets Control - OFAC by Name",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.494825772Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "health-exclusions",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.500513829Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Office of Foreign Assets Control - OFAC",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "id",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:38.66550845Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Lista de terroristas de USA",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.556195728Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Inter-American Development Bank",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.557456526Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Offshore Leaks Database",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "company_name",
            "severity": "none",
            "tables": null,
            "update_date": "2025-07-21T22:11:43.083473258Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "alert_in_media",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Listas, Alertas y PEPs Internacionales",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "ignored",
            "route": "company_name",
            "severity": "unknown",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.532888782Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "international_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Listas, Alertas y PEPs Internacionales",
            "depth": 0,
            "document_type": "company-name",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "ignored",
            "route": "company_name",
            "severity": "unknown",
            "tables": null,
            "update_date": "2025-07-21T22:11:40.468730965Z"
        },
        {
            "categorization": [],
            "check_id": "CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "data_set": "business_background",
            "database_id": "DBIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "database_name": "Comprovante de Inscrição e de Situação Cadastral",
            "depth": 0,
            "document_type": "tax-id",
            "found_company_name": "",
            "found_date_of_birth": "",
            "found_first_name": "",
            "found_gender": "",
            "found_last_name": "",
            "found_rfc": "",
            "id": "DTLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
            "identity_result": "",
            "identity_state": "",
            "result": "not_found",
            "route": "id",
            "severity": "unknown",
            "tables": null,
            "update_date": "2025-07-21T22:12:13.249893904Z"
        }
    ],
    "self": "/api/v1/checks/CHKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/details/",
    "next": ""
}

```
{% endtab %}
{% endtabs %}
