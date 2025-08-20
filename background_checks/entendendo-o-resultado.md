# Entendendo o Resultado

## Quais resultados são obtidos de um check de antecedentes?

Ao completar um check de antecedentes, são gerados dois tipos principais de resultados:

### 1. Score Global

É uma medida numérica de 0 a 10 que indica o nível de confiança de uma pessoa ou empresa com base nas informações encontradas em diversas bases de dados.

* **10** representa um nível de confiança alto (sem antecedentes encontrados).
* **0** representa um nível de confiança baixo ou de risco (por exemplo, quando são encontrados múltiplos antecedentes criminais ou quando o registro não existe).

O score sempre começa em 10 e é reduzido conforme a gravidade dos antecedentes encontrados nas diferentes categorias.

📌 **Nota:** Na API, este score é representado em uma escala de 0 a 1 (por exemplo: 0,8 = 8/10).

#### **Como o score é calculado?**

Cada categoria de antecedentes (chamada **dataset**) possui um peso diferente no cálculo do score. Os achados confirmados por número de identificação (CPF ou CPNJ) impactam mais fortemente no score, pois a correspondência é 100% segura. As informações encontradas apenas pelo nome podem conter erros de homonímia e, por isso, têm um peso menor na composição do score.

***

### 2. Detalhes do Check

Além do score global, cada check retorna um conjunto de detalhes com todas as informações encontradas nas bases de dados consultadas, organizadas por dataset.

**Cada detalhe inclui:**

* Score do dataset (escala de 0 a 1)
* Informações específicas encontradas na fonte de dados
* Um nível de severidade para contextualizar os achados (ajuda no cálculo do score global, mas **não** deve ser interpretado como recomendação jurídica):
  * Unknown (não afeta o score)
  * None (não afeta o score)
  * Very Low
  * Low
  * Medium
  * High
  * Very High

***

## Tipos de Consultas

### Consulta de Pessoa

* **personal\_identity:** Validação da identidade da pessoa por registros oficiais (documentos, permissões de residência, registros eleitorais).
* **criminal\_record:** Verificação de antecedentes criminais em bases governamentais e judiciais.
* **legal\_background:** Consulta de processos legais, medidas corretivas e possíveis inabilitações.
* **international\_background:** Verificação em bases internacionais de alertas, sanções ou antecedentes globais.
* **professional\_background:** Revisão de antecedentes profissionais ou acadêmicos (associações profissionais, sanções disciplinares).
* **affiliations\_and\_insurances:** Validação de afiliações a sistemas de seguridade social e seguros públicos.
* **alert\_in\_media:** Análise de menções em mídias digitais, redes sociais e imprensa.
* **taxes\_and\_finances:** Revisão de registros financeiros e cumprimento de obrigações fiscais

<table><thead><tr><th width="233">dataset / peso</th><th width="74">Brasil</th><th width="92">Colômbia</th><th width="74">México</th><th width="69">Perú</th><th width="80">Chile</th></tr></thead><tbody><tr><td>personal_identity</td><td>0.1</td><td>0.2</td><td>0.2</td><td>0.2</td><td>0.2</td></tr><tr><td>criminal_records</td><td>0.5</td><td>0.6</td><td>0.5</td><td>0.6</td><td>0.6</td></tr><tr><td>legal_background</td><td>0.1</td><td>0.1</td><td>0.1</td><td>0.1</td><td>0.1</td></tr><tr><td>international_background</td><td>0.2</td><td>0.1</td><td>0.1</td><td>0.1</td><td>0.1</td></tr><tr><td>professional_backgroud</td><td>0.2</td><td>0</td><td>NA</td><td>0</td><td>0</td></tr><tr><td>affiliations_and_insurances</td><td>NA</td><td>0</td><td>NA</td><td>0</td><td>0</td></tr><tr><td>alert_in_media</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>taxes_and_finances</td><td>NA</td><td>0</td><td>0.1</td><td>NA</td><td>NA</td></tr></tbody></table>

### Consulta de Empresa

* **business\_background:** Verificação comercial e fiscal (registros fiscais, situação tributária, sanções administrativas).
* **criminal\_record:** Verificação de antecedentes criminais ligados à empresa ou aos seus representantes legais.
* **legal\_background:** Consulta de processos legais e sanções administrativas.
* **international\_background:** Verificação de alertas e sanções internacionais associadas à empresa.
* **alert\_in\_media:** Análise de menções na mídia que possam representar riscos reputacionais.
* **taxes\_and\_finances:** Revisão de obrigações fiscais e registros financeiros.

<table><thead><tr><th width="258">dataset / peso</th><th width="100">Brasil</th><th width="99">Colômbia</th><th width="134">México</th></tr></thead><tbody><tr><td>business_background</td><td>0.7</td><td>0.3</td><td>0.2</td></tr><tr><td>criminal_records</td><td>NA</td><td>0.4</td><td>0.3</td></tr><tr><td>legal_background</td><td>NA</td><td>0.1</td><td>0.3</td></tr><tr><td>international_background</td><td>0.3</td><td>0.1</td><td>0.1</td></tr><tr><td>alert_in_media</td><td>0</td><td>0</td><td>0</td></tr><tr><td>taxes_and_finances</td><td>NA</td><td>0.1</td><td>0.1</td></tr></tbody></table>

### Consulta de Histórico de Crédito - Pessoa

* **personal\_identity:** Validação da identidade oficial.
* **credit\_history:** Avaliação do comportamento financeiro, dívidas e histórico de pagamento (consulta em Datacrédito - Colômbia e Serasa - Brasil).

<table><thead><tr><th width="298">dataset / peso</th><th width="124">Brasil</th><th width="125">Colômbia</th></tr></thead><tbody><tr><td>personal_identity</td><td>0.2</td><td>0.2</td></tr><tr><td>credit_history</td><td>0.8</td><td>0.8</td></tr></tbody></table>

### Consulta de Histórico de Crédito - Empresa

* **business\_background:** Verificação comercial e fiscal da empresa.
* **credit\_history:** Avaliação do histórico financeiro da empresa (Datacrédito - Colômbia e Serasa - Brasil).

<table><thead><tr><th width="298">dataset / peso</th><th width="131">Brasil</th><th width="133">Colômbia</th></tr></thead><tbody><tr><td>business_background</td><td>0.2</td><td>0.2</td></tr><tr><td>credit_history</td><td>0.8</td><td>0.8</td></tr></tbody></table>
