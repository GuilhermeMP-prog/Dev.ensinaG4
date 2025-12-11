#Registro de mudanças
*Arquivo atualizado semanalmente*
---
#DATA:2025-10-27

###ADIÇÕES
* **[Marco]**:Criação do arquivo CHANEGELOG.md para o acompanhamento do projeto


###MUDANÇAS




###REMOÇÕES

#DATA:2025-11-29
##ADIÇÕES
* **[Guilherme]**:Foi discutido o tema do projeto e as bases de dados que serão usadas para tal, além de começar a separar artigos que já tenham feito análises semelhantes.

#DATA:2025-12-05
##ADIÇÕES
* **[Jonathan]**: Criação dos arquivos requirements.txt com as dependências e main.ipynb com os imports e configuração dos gráficos.



#DATA:2025-12-10
##ADIÇÕES
[Bloco 1 — Coleta inicial e visualização do S&P500]

* **[Guilherme]**: Baixei a série histórica do S&P500 para vários períodos (1970–2025 e 1990–2006).
Testei comportamento do yfinance, identifiquei quando ele entrega MultiIndex, filtrei a coluna Close e gerei gráficos simples para validar a estrutura dos dados.

[Bloco 2 — Análise setorial inicial]

* **[Guilherme]**: Baixei os ETFs setoriais XLF, XLE, XLV, XLY e XLK para ver como setores diferentes se comportaram perto da bolha dotcom.
Fiz limpeza básica (ffill + dropna) e normalizei preços.
Gerei gráficos comparativos entre setores para uma visualização inicial de possíveis padrões de contágio.

[Bloco 3 — Primeiros testes com empresas da bolha dotcom]

* **[Guilherme]**: Baixei e normalizei séries de CSCO, MSFT e ORCL para comparar visualmente o comportamento dessas empresas antes e durante a bolha.
Plotagem simples para entender movimentos e padrões iniciais.

[Bloco 4 — Coleta preliminar das empresas do ecossistema de IA]

* **[Guilherme]**: Comecei a análise moderna com empresas diretamente ligadas ao boom da IA:
NVDA, AAPL, MSFT, ORCL, PLTR, IBM e AVGO.
Normalizei as séries, gerei gráficos e fiz comentários sobre fundamentos (lucro recorde da NVIDIA, crescimento do setor etc.).
Essa versão foi apenas para visualização e entendimento inicial do subsetor.

[Bloco 5 — Função de download de dados]

* **[Guilherme]**: Criei a função get_close_series, que ajuda ao importar alguns dados do yfinance.
Agora qualquer ativo baixa no formato correto (sempre uma Series), independente se o yfinance entrega DataFrame normal, MultiIndex ou Series.

[Bloco 6 — Análise gráfica da bolha Dotcom (Cisco)]

* **[Guilherme]**:
* Baixei e padronizei CSCO e S&P500;
* Identifiquei o pico da Cisco via idxmax();
* Alinhei a data do índice ao pregão anterior com get_indexer("ffill");
* Calculei o retorno acumulado da Cisco até o pico e comparei com o S&P;
* Plotei o retorno acumulado com linha marcada no pico.
* Primeira análise formal finalizada.

[Bloco 7 — Análise completa da “bolha da IA” (NVIDIA)]

* **[Guilherme]**:
Baixei algumas empresas de IA usando a função criada; Alinhei datas de cada ativo com o S&P500; Calculei retornos acumulados para cada ação; Montei subplots comparativos (empresa vs benchmark); Produzi tabela resumo com retornos e datas iniciais/finais de cada série.

[Bloco 8 — Estruturação geral e primeiro pipeline funcional do projeto]

* **[Guilherme]**:
Organizei o notebook, deixei todos os blocos separados por tema (S&P500, setores, dotcom, IA).
Padronizei a forma de plotagem, normalização das séries e tratamento das datas.


