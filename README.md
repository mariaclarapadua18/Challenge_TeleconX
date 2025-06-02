# 📊 Análise de Churn de Clientes — Telecom X

## **1. Introdução**

Este relatório apresenta os resultados de uma análise de dados conduzida com base na base de dados **`TelecomX_BR.json`**, com o objetivo de apoiar a empresa **Telecom X** na identificação de fatores determinantes para o **churn de clientes** (cancelamento de serviços).

A análise faz parte do projeto **"Churn de Clientes"**, em resposta à crescente preocupação da empresa com a **alta taxa de cancelamento** dos seus serviços. A equipe foi desafiada a realizar uma investigação exploratória com foco em:

- Importação e manipulação de dados provenientes de um arquivo JSON.
- Aplicação de conceitos de **ETL (Extração, Transformação e Carga)**.
- Limpeza e transformação de dados visando consistência e qualidade.
- Criação de visualizações estratégicas.
- Extração de **insights relevantes** para auxiliar nas decisões empresariais.

O processo foi inteiramente realizado em **Python**, utilizando bibliotecas como `pandas`, `numpy`, `matplotlib`, `seaborn`, entre outras.

---

## **2. Etapas da Análise**

### **2.1. Extração e Importação de Dados**

A base de dados foi carregada a partir de um arquivo JSON. A estrutura original continha inconsistências típicas de dados reais, como valores ausentes, tipos incompatíveis e codificações pouco padronizadas.

### **2.2. Tratamento Inicial**

Durante essa etapa, foram adotadas as seguintes medidas:

- Conversão de colunas com valores `Yes/No` para valores binários (`1/0`), padronizando variáveis booleanas.
- Substituição de valores nulos:
  - Em colunas booleanas: preenchimento com `False`.
  - Em colunas numéricas: preenchimento com a **média da coluna**.
- Conversão de tipos de dados para as respectivas categorias (inteiros, floats, strings e booleanos).
- Criação de uma nova variável chamada **`dailyaccount`**, a qual representa a média diária de faturamento, calculada a partir da divisão do valor mensal por aproximadamente 30 dias. Essa métrica permite uma análise mais refinada do comportamento financeiro dos clientes.

---

## **3. Análise Exploratória de Dados (EDA)**

A Análise Exploratória de Dados foi realizada com o objetivo de **entender o perfil dos clientes**, detectar **padrões de comportamento** e **identificar correlações** com o cancelamento.

### **3.1. Análise Estatística Descritiva**

Foram calculadas medidas de tendência central e dispersão para todas as variáveis numéricas:

- **Média**, **mediana**, **desvio padrão** e **quartis**.
- Detecção de outliers.
- Comparações entre clientes que evadiram e os que permaneceram ativos.

---

### **3.2. Distribuição Geral da Evasão**

- **Taxa total de evasão:** **25,7%** dos clientes cancelaram seus serviços.
- Essa taxa foi visualizada por meio de gráficos de barras e pizza, demonstrando de forma clara a proporção entre clientes ativos e cancelados.

---

### **3.3. Análise por Variáveis Categóricas**

A seguir, estão listadas as taxas de evasão por categorias:

| Variável              | Insight Relevante                                                   |
|-----------------------|---------------------------------------------------------------------|
| **Gender**            | Homens e mulheres têm taxas de evasão semelhantes.                 |
| **SeniorCitizen**     | Clientes idosos evadem **40,27%** das vezes – valor acima da média. |
| **Partner**           | Clientes sem parceiro(a) têm evasão de **32,01%**.                 |
| **Dependents**        | Contas sem dependentes têm taxa de evasão de **30,34%**.          |
| **PhoneService**      | Não influencia significativamente na evasão.                       |
| **MultipleLines**     | Sem impacto relevante na evasão.                                   |
| **InternetService**   | Clientes com fibra óptica cancelam mais – possível insatisfação.   |
| **OnlineSecurity**    | Clientes **sem segurança online** cancelam mais.                   |
| **OnlineBackup**      | Diferença pequena entre evasão de quem tem ou não.                 |
| **DeviceProtection**  | Não influencia de forma significativa.                             |
| **TechSupport**       | Clientes sem suporte técnico evadem mais.                          |
| **StreamingTV/Movies**| Serviços de streaming não são determinantes.                       |
| **Contract**          | Planos **mensais** têm evasão de **41,32%**.                      |
| **PaperlessBilling**  | Faturas eletrônicas associadas a evasão de **32,48%**.             |
| **PaymentMethod**     | Clientes que utilizam **Electronic Check** têm maior evasão.       |

---

### **3.4. Análise por Variáveis Numéricas com Gráficos**

#### **Tenure (Tempo de Contrato)**

- Boxplots mostram que a evasão é significativamente mais comum nos **primeiros 30 meses** de contrato.

#### **Monthly Charges (Cobrança Mensal)**

- Clientes que pagam entre **R$60 e R$100/mês** são os que mais cancelam.
- Distribuição mostra um pico de clientes em **R$20/mês**, com redução acentuada acima de **R$80**.

#### **Total Charges (Cobrança Total)**

- A maioria dos clientes possui cobranças acumuladas inferiores a **R$2.000**, o que pode indicar relacionamentos curtos ou baixo uso.

#### **Distribuição da Duração do Contrato**

- A maior parte dos clientes está nos primeiros meses de contrato, com picos acima de **700 clientes** com menos de 10 meses, o que corrobora a tendência de evasão precoce.

---

## **Atividade Extra: Análise de Correlação**

Foi realizada uma análise de correlação entre as variáveis numéricas da base. Um dos focos foi a correlação entre a variável **Total de Serviços** e **Churn**, que resultou em um valor de **0,01634**. Isso indica uma correlação praticamente nula, sugerindo que a quantidade de serviços contratados não influencia a decisão de cancelamento.

                total_servicos     Churn
total_servicos        1.00000      0.01634
Churn                 0.01634      1.00000

---

## **4. Conclusão**

A análise exploratória da base **TelecomX_BR.json** permitiu identificar variáveis críticas para o entendimento do churn de clientes. Os principais fatores associados à evasão são:

- Tipo de contrato (planos mensais);
- Ausência de serviços como **suporte técnico** e **segurança online**;
- Perfil do cliente (idosos, sem parceiro e sem dependentes);
- Método de pagamento (Electronic Check);
- Tempo de permanência inferior a 30 meses.

Esses **insights** subsidiam a formulação de estratégias de retenção, como:

- Campanhas de fidelização focadas nos primeiros meses;
- Incentivos para migração a planos anuais;
- Investimento em serviços valorizados (segurança e suporte);
- Análise de métodos de pagamento para mitigar riscos de evasão.

---

## **5. Recomendações Finais**

1. **Segmentar clientes por risco de evasão** e priorizar campanhas direcionadas.
2. **Melhorar os serviços de fibra óptica**, que apresentam altos índices de insatisfação.
3. **Reavaliar o modelo de faturamento eletrônico**, que embora moderno, está associado à maior evasão.
4. **Oferecer planos com vantagens a longo prazo**, como descontos progressivos ou benefícios por tempo de permanência.
5. **Investir em coleta de feedbacks** para avaliar o motivo de evasão nos primeiros meses.

---
