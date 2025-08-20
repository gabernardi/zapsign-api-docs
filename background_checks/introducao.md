# Introdução

**Nesta seção:**

* [Introdução a Antecedentes](https://docs.zapsign.com.br/background_checks/introducao#introducao-a-antecedentes)
* [O que é um Check e por que ele é útil para as empresas](https://docs.zapsign.com.br/background_checks/introducao#o-que-e-um-check-e-por-que-ele-e-util-para-as-empresas)
* [Ciclo de Vida de um Check](https://docs.zapsign.com.br/background_checks/introducao#ciclo-de-vida-de-um-check)
* [Tipos de Consultas Disponíveis](https://docs.zapsign.com.br/background_checks/introducao#tipos-de-consultas-disponiveis)
* [Preços das Consultas de Antecedentes](https://docs.zapsign.com.br/background_checks/introducao#precos-das-consultas-de-antecedentes)

### Introdução a Antecedentes

A funcionalidade de consulta de antecedentes permite que empresas obtenham informações chave sobre pessoas ou empresas a partir de diversas bases de dados públicas e privadas. Esse processo auxilia na tomada de decisões informadas em processos de contratação, avaliação de riscos ou verificação de identidade.

### O que é um Check e por que ele é útil para as empresas

Um Check é uma consulta que verifica os antecedentes de uma pessoa ou empresa em múltiplas bases de dados. Esse processo gera um relatório detalhado com uma pontuação geral que reflete o nível de risco associado, acompanhado do detalhamento dos resultados obtidos em cada base consultada.

As empresas utilizam os Checks para:

* Avaliar a confiabilidade de clientes, fornecedores ou colaboradores.
* Identificar possíveis riscos financeiros ou legais.
* Cumprir exigências regulatórias (KYC, AML)

### Ciclo de Vida de um Check

O processo de um Check segue um fluxo simples:

* **Criação:** É enviada uma solicitação para iniciar o Check com as informações da pessoa ou empresa.
* **Fila de Processamento:** O Check entra em uma fila e é direcionado aos sistemas responsáveis por realizar as consultas.
* **Resultados:** Após a conclusão das consultas, os resultados são consolidados e o relatório é gerado com a pontuação geral e os detalhes de cada base consultada.

A disponibilidade dos resultados das bases públicas depende da entidade que as administra. Caso alguma base de dados esteja indisponível no momento da consulta, serão feitas tentativas automáticas durante duas horas. Se após esse período a resposta ainda não for obtida, essa base será desconsiderada nos resultados finais.

Esse processo garante que os relatórios entregues sejam o mais completos possível, mantendo a confiabilidade e a precisão dos Checks.

### Tipos de Consultas Disponíveis

Atualmente, é possível realizar os seguintes tipos de consultas:

* **Pessoa:** Verificação abrangente do perfil de uma pessoa física, consultando diversas fontes oficiais e públicas para identificar antecedentes relevantes. Inclui informações como identidade, antecedentes criminais, afiliações e outros dados importantes para avaliar o risco.
* **Empresa:** Verificação de uma pessoa jurídica, consultando bases públicas e privadas para detectar vínculos com processos judiciais, sanções, histórico tributário, alertas na mídia, entre outros. Ideal para processos de due diligence ou avaliação de parceiros comerciais.
* **Histórico de crédito de pessoa:** Consulta especializada que entrega o histórico de crédito de uma pessoa, incluindo informações financeiras, dívidas, comportamento de pagamento e registros em birôs de crédito. Permite avaliar a solvência e confiabilidade financeira do indivíduo.
* **Histórico de crédito de empresa:** Consulta focada em obter o histórico de crédito de uma empresa. Inclui informações sobre cumprimento fiscal, dívidas, protestos e comportamento de pagamento, sendo útil para decisões de crédito ou formação de parcerias.

#### Disponibilidade por país e tipo de documento

| País / Tipo de consulta         | Brasil | Colômbia                            | México         | Chile                    | Perú                            |
| ------------------------------- | ------ | ----------------------------------- | -------------- | ------------------------ | ------------------------------- |
| Pessoa                          | CPF    | Cédula, cédula de extranjería e PPT | CURP e RFC     | RUT e RUT de extranjería | DNI, carné de extranjería e PTP |
| Empresa                         | CNPJ   | RUT                                 | RFC            | Não disponível           | No disponible                   |
| Histórico de crédito de pessoa  | CPF    | Cédula                              | Não disponível | Não disponível           | No disponible                   |
| Histórico de crédito de empresa | CNPJ   | RUT                                 | Não disponível | Não disponível           | No disponible                   |

### Preços das Consultas de Antecedentes

Cada vez que um Check é criado, o custo correspondente é automaticamente descontado de sua conta, de acordo com o tipo de consulta realizada.

{% hint style="warning" %}
**Importante:** A cobrança é realizada no momento da criação da consulta, e não quando os resultados são entregues.
{% endhint %}

#### Como recarregar sua conta

Você pode recarregar sua conta diretamente pelo seu painel de usuário acessando: [**Planos e Preços > Créditos**](https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits)

#### Custos por tipo de consulta

| Tipo de Consulta                         | Países                        | Créditos     | Equivalente em USD |
| ---------------------------------------- | ----------------------------- | ------------ | ------------------ |
| Consulta de pessoa                       | Colômbia, Brasil, Chile, Peru | 90 créditos  | R$9                |
| Consulta de pessoa                       | México                        | 130 créditos | R$13               |
| Consulta de empresa                      | Colômbia, Brasil, Chile, Peru | 90 créditos  | R$9                |
| Consulta de empresa                      | México                        | 130 créditos | R$13               |
| Histórico de crédito (pessoa ou empresa) | Colômbia, Brasil              | 200 créditos | R$20               |

{% hint style="warning" %}
**Dica:** Antes de realizar uma integração em massa, certifique-se de que possui créditos suficientes para evitar interrupções nos checks. Recomendamos utilizar o endpoint **Informações do plano** para consultar o saldo de créditos da sua conta.
{% endhint %}
