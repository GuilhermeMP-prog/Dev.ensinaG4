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

[Bloco 6 — Análise gráfica comparativa da bolha Dotcom (Cisco)]

* **[Guilherme]**: Baixei e padronizei CSCO e S&P500; Identifiquei o pico da Cisco via idxmax(); Alinhei a data do índice ao pregão anterior com get_indexer("ffill"); Calculei o retorno acumulado da Cisco até o pico e comparei com o S&P; Plotei o retorno acumulado com linha marcada no pico. Primeira análise formal finalizada.

[Bloco 7 — Análise gráfica comparativa da “bolha da IA” (NVIDIA)]

* **[Guilherme]**:
Baixei algumas empresas de IA usando a função criada; Alinhei datas de cada ativo com o S&P500; Calculei retornos acumulados para cada ação; Montei subplots comparativos (empresa vs benchmark); Produzi tabela resumo com retornos e datas iniciais/finais de cada série.

[Bloco 8 — Estruturação geral e primeiro pipeline funcional do projeto]

* **[Guilherme]**:
Organizei o notebook, deixei todos os blocos separados por tema (S&P500, setores, dotcom, IA).
Padronizei a forma de plotagem, normalização das séries e tratamento das datas.


#DATA:2025-12-21

##ADIÇÕES

[Bloco 9 — Dados de EPS das 50 maiores empresas do SP500]
* **[Guilherme]**: Para analisar o lucro por ação das maiores empresas x e o retorno acumulado desde 2021, evidenciando que existe uma disparidade entre aqueles que de fato geram fluxo de caixa.

[Bloco 10 — Dados de EPS das 50 maiores empresas do SP500, destacando o ecossistema de IA]
* **[Guilherme]**: Evidenciando empresas como NVDA, PLTR e outras.

[Bloco 11 —  P/E atual do mercado e das empresas.]
* **[Guilherme]**: responde uma pergunta, será que somente nvda está esticada? será que ela é o foco? e as outras empresas do setor? e outras que não tem correlação tão explicíta?
[Bloco 12 —  Comparação de P/E da Cisco no auge da bolha, com NVDA e PLTR]
* **[Guilherme]**: percebe-se que P/E da cisco no auge, era muito maior que a da NVDA hoje, mas menor do que PLTR. Logo, acho que fica evidente que, NVDA tem lucro pra justificar os seus preços, expectativa e tals. Mas deve-se olhar para PLTR e outras emrpresas do ecossistema, como PLTR tem lucro MENOR e tem multiplo MAIOR do que cisco no auge da bolha.

#DATA:2025-12-28 

##ADIÇÕES

[Bloco 13 — Coleta básica de sentimento (PCR)] 
* **[Guilherme]**: Implementei a base do sentimento de mercado. O código acessa o vencimento de opções mais próximo e soma o Open Interest (contratos abertos) de Calls e Puts para calcular o Put/Call Ratio (PCR). É o termômetro inicial para ver o humor do mercado no curtíssimo prazo.

[Bloco 14 — Cruzamento de Momentum com Sentimento]
* **[Guilherme]**: Comecei a correlacionar o preço com as opções. O script calcula o retorno dos últimos 90 dias e joga num gráfico de dispersão contra o PCR. A ideia é caçar divergências: onde o preço subiu muito, mas o pessoal das opções já começou a comprar seguro (Puts).

[Bloco 15 — Visão Macro e Posicionamento Institucional (Full PCR)] 
* **[Guilherme]**: Evoluí o PCR para a visão "Full". Agora o código varre todos os vencimentos disponíveis da empresa, não só o mês que vem. Isso limpa o ruído das rolagens e mostra onde o "dinheiro grosso" das instituições está realmente posicionado. Usei o tamanho da bolha no gráfico para destacar onde a liquidez (Total OI) é maior, tipo na NVIDIA.

[Bloco 16 — O "Termômetro do Medo" (IV Ponderada)] 
* **[Guilherme]**: Versão mais sofisticada do pipeline. Adicionei a Volatilidade Implícita (IV) ponderada pelo Open Interest. Agora a cor das bolhas mostra se a opção está ficando caro ou barato. Com isso, ficou nítido que PLTR e AVGO estão em zona de alerta (muito esticadas com proteção subindo) e que a ORCL está com um sinal de fraqueza bem estranho no mercado de derivativos.

#DATA:2025-12-30

##ADIÇÕES
[Bloco 17 — Análise de Risco e Drawdown]

* **[Jonathan]**: Implementei a função de cálculo de Drawdown para mensurar a queda do topo histórico.
Utilizei a função 'get_close_series' implementada pelo Guilherme e gerei gráficos de área.
Comparei a queda da Cisco em 2000 com a volatilidade atual.
Pela análise, descobri que a Nvidia demonstrou uma rápida recuperação, ao passo que a Palantir apresentou drawdowns profundos e demorados, o que confirma sua maior fragilidade.

#DATA:2026-01-08

##ADIÇÕES
[Bloco 18 — Validação Estatística]

* **[Jonathan]**: Implementei o teste de permutação com 10.000 simulações.
Utilizei a função 'get_close_series' implementada pelo Guilherme para baixar os dados, usando Nvidia, Bitcoin e Ibovespa como ativos.
Hipótese nula: Não há relação entre os ativos.
O resultado foi um P_value de 0.0, portanto rejeitamos a hipótese nula. Com isso, é estatisticamente comprovado que existe uma relação entre Nvidia x Bitcoin e Nvidia x Ibovespa.

##DATA:2026-01-10


##ADIÇÕES


[Bloco 19 —Matriz de Significância Estatística]

* **[Guilherme]**: Implementando o cálculo de matrizes duplas: correlação ($r$) e significância ($p$-valor). Através da função pearsonr, transformei a análise visual em evidência quantitativa, permitindo filtrar o ruído de mercado e identificar relações estatisticamente válidas para a Seção 2.5 do Whitepaper.

Implementei o teste de permutação que o Jonathan utilizou para acrescentar mais rigor estatistico, com 10.000 iterações para construir distribuições nulas ($H_0$) por meio do embaralhamento de retornos do benchmark. Este processo gera um $p$-valor empírico que valida a influência sistêmica dos ativos de IA, diferenciando matematicamente a correlação real da aleatoriedade. A visualização por histogramas fornece a prova definitiva de que o acoplamento observado não é fruto do acaso.

[Bloco 20 — Matriz de Veracidade e Contágio Setorial]

* **[Guilherme]**: Calculei a correlação entre IA com os ETFs da economia real, aplicando 10.000 simulações de permutação para cada par. Implementei a Matriz de Veracidade, que utiliza um filtro estatístico para ocultar automaticamente qualquer relação com $p$-valor $> 0,05$. Esta técnica garante que apenas o contágio sistêmico validado seja exibido, confirmando que ausências na matriz (como NVDA x Utilities) representam ruído estatístico, blindando a argumentação contra falsos positivos.

[Bloco 21 - Evolução da Influência e Correlação Móvel]

* **[Guilherme]**: Implementei o cálculo de correlação móvel com uma janela de 21 dias úteis (um mês comercial) para monitorar a dinâmica temporal entre os drivers de IA e os pilares da economia real. Esta análise granular permite identificar mudanças de regime e picos de contágio ao longo do tempo, fornecendo a base para o estudo de janelas de estresse na Seção 2.5 do Whitepaper. A visualização destaca momentos em que a correlação rompe o patamar de 0,6, evidenciando períodos de acoplamento sistêmico severo.

[Bloco 22 - Validação de Contágio e Faixa de Significância]

* **[Guilherme]**: Integrei thresholds estatísticos à análise temporal, calculando o valor crítico de correlação ($r_{crit}$) para uma janela de 21 dias com 95% de confiança. Implementei uma "faixa de ruído" sombreada na visualização, permitindo distinguir visualmente períodos de contágio sistêmico real de flutuações aleatórias. Este avanço garante que as conclusões sobre a influência da IA nos setores da economia real sejam fundamentadas em rigor estatístico, blindando-se contra interpretações de dados sem significância

[Bloco 23 — Análise de Risco de Cauda: VaR e CVaR]

* **[Guilherme]**: Implementei a análise de risco de cauda por meio do Value at Risk (VaR) e do Conditional Value at Risk (CVaR/Expected Shortfall) com 95% de confiança. O código quantifica a severidade das perdas extremas para NVDA e PLTR, permitindo identificar a presença de caudas pesadas na distribuição de retornos por meio do diferencial entre o limite de perda e o déficit esperado. Esta métrica descritiva é fundamental, pois define a magnitude do risco de ruína em cenários de baixa probabilidade e alta severidade.

[Bloco 24 — Veracidade Histórica e Anatomia da Bolha Dot-Com]

* **[Guilherme]**: Apliquei os testes de permutação sobre os dados históricos de 1999 a 2001 para validar o regime de contágio dos líderes da época (Cisco e Microsoft). Através da matriz de veracidade mascarada, este bloco permite provar se a bolha de 2000 era um evento de risco isolado ou sistêmico. A análise estabelece o fundamento empírico para demonstrar se o acoplamento atual da IA com a economia real possui precedentes históricos ou se representa uma mudança estrutural inédita na arquitetura de risco.

[Bloco 25 — Marcador de Estresse CSCO vs Economia Real 2000]

* **[Guilherme]**: Implementei um diagnóstico de ponto crítico focado no ápice da bolha Dot-com (Março de 2000). O código combina a visualização de correlação móvel com um teste de permutação localizado para a janela específica do evento de estresse. Esta abordagem permite emitir um "veredito atuarial" sobre o estado do mercado naquele momento, separando o contágio sistêmico real do ruído estatístico. O resultado é a prova técnica de que, no seu epicentro, o colapso da Cisco em 2000 apresentava independência estatística em relação a diversos setores da economia real, fundamentando a comparação de vulnerabilidade estrutural com NVDA.

[Bloco 26 —  Severidade Histórica da Cisco (2000)]

* **[Guilherme]**: Fiz uma análise de severidade extrema para a Cisco Systems durante o período de 1999-2001, focando nas métricas de ruína absoluta. Calculei o VaR Histórico e o CVaR (Expected Shortfall) para definir o limite de pânico e a perda média em cenários de crash, além de processar o Drawdown Máximo para medir a erosão total de capital. Este bloco estabelece o "benchmark de desastre", permitindo comparar a gravidade da queda da era Dot-com com a resiliência ou vulnerabilidade dos ativos de IA atuais.

[Bloco 27 — Validação via Bootstrapping]

* **[Guilherme]**: Elevei a precisão estatística da análise de risco de cauda através da reamostragem por Bootstrap (1.000 iterações), definindo intervalos de confiança de 95% para o CVaR da Cisco. O código corrige vulnerabilidades técnicas anteriores, como a dimensionalidade de arrays no NumPy (via .flatten()) e a extração de escalares em objetos MultiIndex do Pandas (via .item()), garantindo resultados replicáveis e robustos. Esta etapa transforma a métrica de severidade em um dado científico, permitindo afirmar com segurança a magnitude do colapso histórico da era Dot-com e sua margem de erro

[Bloco 28 — Comparação de Estabilidade Sistêmica e Volatilidade]

* **[Guilherme]**: Implementei uma análise comparativa de volatilidade anualizada móvel (janela de 21 dias) para contrastar o regime da bolha Dot-Com com a atual era da IA. O código processa 1000 dias de dados históricos para NASDAQ e Cisco (1998-2002) contra os últimos 1000 dias de SP & 500 e NVIDIA. Esta visualização permite identificar se o patamar de incerteza atual da NVIDIA supera os níveis críticos observados no pico de Março de 2000, servindo como um barômetro de "estresse estrutural".

[Bloco 29 — Diagnóstico de Instabilidade e Volatilidade de PLTR]

* **[Guilherme]**: Implementei o cálculo de volatilidade anualizada móvel para a Palantir (PLTR), assegurando a estabilidade do script contra estruturas MultiIndex do Yahoo Finance por meio da seleção explícita da primeira coluna. O código estabelece um diagnóstico de instabilidade ao confrontar a volatilidade média recente do ativo com os patamares críticos da Cisco em 2000 ($60\%$). Esta análise é vital,servindo para demonstrar se o prêmio de risco exigido para ativos de "narrativa pura" de IA já atinge níveis de estresse equivalentes ao estouro da bolha Dot-com.

##DATA:2026-01-18


##ADIÇÕES

[Bloco 30 — Teoria da Causalidade de Granger]

* **[Guilherme]**: Incorporei a fundamentação teórica do Teste de Causalidade de Granger para elevar a análise de "correlação" para "precedência preditiva". Este método permite isolar a direcionalidade do risco, provando se os ativos de IA (NVIDIA) atuam como variáveis independentes que ditam o ritmo dos setores dependentes (drivers). Transformando a hipótese de influência em uma demonstração de liderança estatística temporal.



[Bloco 31 — Mapeamento de Hierarquia: Drivers vs. Followers]

* **[Guilherme]**: Finalizei os testes de causalidade comparando a Palantir (PLTR) com a NVIDIA e setores macro. Os resultados revelam que, ao contrário da NVIDIA, a PLTR não exerce liderança sobre a economia real, atuando como um "Follower de Sentimento" que reage passivamente a choques no setor de Energia. Esta distinção permite classificar os riscos do setor de IA em duas categorias na Seção 4: Riscos de Infraestrutura (Sistêmicos/Causais) e Riscos de Aplicação (Reflexivos/Voláteis), refinando o modelo de contágio do Whitepaper.

##DATA:2026-01-31


##MUDANÇAS
* **[Guilherme]**: Tornei os testes de granger mais precisos e com mais camadas de robustez estatística, vulgo ADF Test e VAR-LR. Além de ter alterado algumas representações de correlações móveis. Retirei o mapeamento de hierarquia por julgar que não fosse ser tão interessante para a proposta da pesquisa, o que desviaria o foco.



