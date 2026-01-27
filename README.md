# Dev.ensinaG4

## Influência Sistêmica das Empresas de IA nos Mercados Financeiros: Uma Análise Comparativa entre a Bolha Dot-Com e o AI Boom


## 🎯 Motivação e Objetivos 

Este projeto visa fazer uma análise histórico-comparativa entre duas ondas tecnológicas com grandes impactos no mercado financeiro global: A Bolha Dot-com no início dos anos 2000 e o atual avanço da Inteligência Artificial Generativa a partir de 2022. Com isso, buscamos investigar se o atual ciclo de IA generativa configura uma bolha especulativa isolada, análoga ao que ocorreu na Bolha Dot-com ou se constituiu-se como driver sistêmico do mercado.

Para tal, utilizamos a Cisco (CSCO) e a NVIDIA (NVDA) como proxies representativos da bolha dot-com(1999-2000) e do atual ciclo de IA(2023-2025). Ademais, testamos a hipótese de contágio sistêmico e integração com outros setores.

## 🧠 Hipóteses Centrais

* **Hipótese Nula:** A valorização de IA é puramente especulativa, de forma análoga à Cisco em 2000.
* **Hipótese Alternativa:** A IA atua como um **driver** sistêmico com correlações causais comprovadas com diferentes setores da Economia.

## 🛠️ Metodologia e Ferramentas

Utilizamos **Python** e as seguintes bibliotecas: **Pandas**, **Numpy**, **YFinance**, **Matplotlib e Seaborn**, **Statsmodels**, **Scipy**.


* **Validação Estatística:** **Testes de Permutação(Monte Carlo com dez mil simulações)** para filtrar correlações espúrias e validar a significância dos resultados.

* **Causalidade:** Teste de **Causalidade de Granger Bidirecional** para isolar a direcionalidade do risco, transformando a hipótese da influência em uma demonstração de liderança temporal.

* **PCA (Principal Component Analysis):** Para identificar os drivers ocultos do mercado.

* **Gestão de Risco:** Cálculo de métricas de cauda como **VaR (Value at Risk)** e **CVaR (Conditional VaR)**, utilizando **Bootstrap** para criar intervalos de confiança robustos, além da análise de **Drawdowns** históricos.

## 📊 Principais Resultados 

### 1. Cisco (2000) vs. Nvidia (2025)

Em 2000, a Cisco negociava a múltiplos de bolha (205x o lucro). A Nvidia, no entanto, apresenta lucros reais robustos (~\$100 bi) que justificam parte relevante do prêmio de risco.

Enquanto a Cisco colapsou **89%** sem recuperação plena, a Nvidia demonstra recuperação rápida de **drawdowns**.
 
### 2. Dupla Camada de Risco 

A análise de derivativos (Puts/Calls e Volatilidade Implícita) revelou que o ecossistema de IA é segmentado em dois grandes blocos:

* **Winners Complacentes:** Big Techs como Microsoft e Apple absorvem a narrativa de IA com volatilidade controlada e put/call ratio relativamente baixo (< 0.75), indicando postura confortável dos investidores em relação a essas empresas.

* **Winners Temidos:** Nvidia, Palantir e Broadcom concentram a convexidade de retorno, mas com alto medo embutido (IV > 0.7 e put/call ratio próximo ou acima de 0.90), indicando que o mercado precifica um risco de cauda não trivial.

### 3. Validação de Contágio 

* **Sincronia Setorial:** O Teste de Permutação (Monte Carlo) validou correlações robustas (p-value < 0.05) com a Economia Real. Destaque para a **Broadcom(AVGO)**, que apresentou **ubiquidade perfeita**, sincronizando com todos os 7 setores analisados. Diferente da Cisco (correlação intermitente), a IA sustenta correlações móveis acima de 0.6 de forma consistente.

* **Contágio Global:** Provamos estatisticamente que existem correlações significativas com **Bitcoin** e **Ibovespa**, provando que o "risco IA" conecta infraestrutura digital, criptoativos e mercados emergentes.

### 4. Causalidade de Granger 
* **Nvidia → Economia Real:** Confirmamos causalidade unidirecional de Nvidia para os setores Industrial e de Energia. Choques na oferta de chips propagam-se para a produção real.

* **NVDA ↔ PLTR:** Nvidia e Palantir mostram **independência causal** perfeita entre si, provando que o ecossistema de IA opera via paralelismo funcional (Hardware vs. Software) sem dependência hierárquica direta.

* **A Exceção:** O setor financeiro (XLF) manteve-se estatisticamente independente, indicando que o contágio é de natureza produtiva, e não puramente especulativa.

### 5. Risco de Cauda (Tail Risk)
* Apesar de alta volatilidade, as métricas de **CVaR** (Conditional VaR) mostram que o regime atual é mais disciplinado (40-60% de volatilidade anualizada) do que as explosões descontroladas da Cisco (>100%) em 2000.

### 6. Setor de Energia como Driver Oculto (PCA)

A análise de Componentes Principais revelou que o **PC1 (48.9% da variância do mercado)** é dominado pelo setor de **Energia (XLE)**, seguido por Nvidia e Palantir. Isso confirma que o gargalo físico (eletricidade para Data Centers) é a covariância primordial do ecossistema de IA.




