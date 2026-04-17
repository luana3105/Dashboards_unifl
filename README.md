# 🍷 Wine Quality Explorer — Dashboard Interativo

> **Exploração e Visualização de Dados em Dashboards Interativos**  
> Dataset: Wine Quality — UCI Machine Learning Repository

---

## Sumário

1. [Introdução e Justificativa do Dataset](#introdução-e-justificativa-do-dataset)
2. [Metodologia e Ferramentas](#metodologia-e-ferramentas)
3. [Análise Exploratória Inicial](#análise-exploratória-inicial)
4. [Visualizações Criadas e Interpretações](#visualizações-criadas-e-interpretações)
5. [Interatividade Implementada](#interatividade-implementada)
6. [Conclusão e Insights Obtidos](#conclusão-e-insights-obtidos)
7. [Como Executar](#como-executar)
8. [Referências](#referências)

---

## Introdução e Justificativa do Dataset

### O Problema

A avaliação da qualidade de um vinho é tradicionalmente subjetiva — realizada por sommeliers e especialistas que atribuem notas sensoriais. A questão central deste projeto é: **é possível prever e entender a qualidade de um vinho a partir de suas propriedades físico-químicas mensuráveis?**

Este dashboard responde a essa pergunta através de visualizações interativas que permitem ao usuário explorar as relações entre composição química e qualidade percebida, sem necessidade de conhecimento técnico prévio.

### O Dataset Escolhido

O **Wine Quality Dataset** foi criado por P. Cortez et al. (2009) e está disponível no UCI Machine Learning Repository. Ele contém dados de vinhos da região do **Vinho Verde, em Portugal**, e é composto por:

| Subconjunto | Amostras | Características |
|-------------|----------|-----------------|
| Vinho Tinto | 1.599 | 12 variáveis |
| Vinho Branco | 4.898 | 12 variáveis |
| **Total** | **6.497** | **12 variáveis** |

#### Variáveis do Dataset

| Variável | Descrição | Unidade |
|----------|-----------|---------|
| `fixed acidity` | Acidez fixa (tartárica) | g/dm³ |
| `volatile acidity` | Acidez volátil (acética) | g/dm³ |
| `citric acid` | Ácido cítrico | g/dm³ |
| `residual sugar` | Açúcar residual | g/dm³ |
| `chlorides` | Cloretos (cloreto de sódio) | g/dm³ |
| `free sulfur dioxide` | Dióxido de enxofre livre | mg/dm³ |
| `total sulfur dioxide` | Dióxido de enxofre total | mg/dm³ |
| `density` | Densidade | g/cm³ |
| `pH` | pH | — |
| `sulphates` | Sulfatos | g/dm³ |
| `alcohol` | Teor alcoólico | % vol. |
| `quality` | **Nota de qualidade** (variável alvo) | 0–10 |

#### Por que este dataset?

- **Relevância prática**: a indústria vinícola é economicamente significativa e a garantia de qualidade é um desafio constante;
- **Riqueza analítica**: 11 variáveis preditoras contínuas oferecem múltiplos ângulos de análise;
- **Comparabilidade**: dois subconjuntos (tinto e branco) permitem análises comparativas;
- **Qualidade dos dados**: ausência de valores nulos, dados limpos e bem documentados;
- **Benchmark reconhecido**: amplamente utilizado na literatura de Machine Learning, facilitando a validação de resultados.

---

## Metodologia e Ferramentas

### Stack Tecnológica

O dashboard foi desenvolvido inteiramente em **HTML5 + JavaScript puro**, sem dependência de servidor back-end, garantindo portabilidade máxima.

| Ferramenta | Versão | Uso |
|------------|--------|-----|
| **Chart.js** | 4.4.1 | Gráficos interativos (barras, dispersão, radar) |
| **HTML5/CSS3** | — | Estrutura e estilização responsiva |
| **JavaScript ES6+** | — | Lógica de dados, filtros e interatividade |
| **Google Fonts** | — | Tipografia (DM Sans + DM Serif Display) |

> **Alternativa com Python**: o mesmo dashboard pode ser reproduzido em **Streamlit** com **Plotly** usando as estatísticas reais do dataset. Os dados utilizados nesta versão são estatisticamente representativos do dataset original (médias, desvios-padrão e correlações extraídas do dataset real do UCI).

### Metodologia de Desenvolvimento

```
1. Coleta e compreensão do dataset (UCI Repository)
       ↓
2. Análise exploratória estatística (médias, correlações, distribuições)
       ↓
3. Identificação dos insights mais relevantes
       ↓
4. Design do dashboard (hierarquia visual, paleta, layout)
       ↓
5. Implementação das visualizações
       ↓
6. Adição de interatividade e filtros
       ↓
7. Testes e refinamento visual
```

### Decisões de Design

- **Tema escuro vinícola**: fundo escuro com dourado e bordô evoca a identidade visual do universo dos vinhos;
- **Tipografia editorial**: DM Serif Display para títulos cria contraste com o sans-serif dos dados;
- **Hierarquia visual clara**: KPIs no topo → controles → gráficos → insights;
- **Responsividade**: grid CSS com breakpoints para uso em diferentes dispositivos.

---

## Análise Exploratória Inicial

### Estatísticas Descritivas

#### Vinho Tinto (n = 1.599)

| Variável | Média | Desvio Padrão | Min | Max |
|----------|-------|---------------|-----|-----|
| Acidez fixa | 8.32 | 1.74 | 4.6 | 15.9 |
| Acidez volátil | 0.528 | 0.179 | 0.12 | 1.58 |
| Ácido cítrico | 0.271 | 0.195 | 0.0 | 1.0 |
| Açúcar residual | 2.54 | 1.41 | 1.2 | 15.5 |
| pH | 3.311 | 0.154 | 2.74 | 4.01 |
| Álcool | 10.42 | 1.07 | 8.4 | 14.9 |
| **Qualidade** | **5.64** | **0.81** | **3** | **8** |

#### Vinho Branco (n = 4.898)

| Variável | Média | Desvio Padrão | Min | Max |
|----------|-------|---------------|-----|-----|
| Acidez fixa | 6.85 | 0.84 | 3.8 | 14.2 |
| Açúcar residual | 6.39 | 5.07 | 0.6 | 65.8 |
| SO₂ total | 138.36 | 42.5 | 9.0 | 440 |
| Álcool | 10.51 | 1.23 | 8.0 | 14.2 |
| **Qualidade** | **5.88** | **0.89** | **3** | **9** |

### Padrões Identificados na EDA

1. **Distribuição de qualidade**: ambos os subconjuntos seguem uma distribuição aproximadamente normal, centrada entre 5 e 6;
2. **Desbalanceamento de classes**: notas extremas (3 e 9) são raras — menos de 1% das amostras;
3. **Álcool como preditor**: correlação de +0.48 (tinto) e +0.44 (branco) com qualidade;
4. **Acidez volátil negativa**: correlação de -0.39 (tinto) — excesso de ácido acético é indesejável;
5. **Diferenças entre tipos**: vinhos brancos têm muito mais açúcar residual e SO₂ total que os tintos.

---

## Visualizações Criadas e Interpretações

### 1. KPIs (Indicadores-Chave de Desempenho)

**Tipo**: Cards de métricas  
**Localização**: Topo do dashboard

Exibe em destaque: número de amostras, nota média, percentual de alta qualidade (≥7), teor alcoólico médio e número de variáveis. Os valores se atualizam dinamicamente ao alternar entre vinho tinto, branco ou ambos.

**Interpretação**: O painel de KPIs dá ao usuário uma visão rápida e contextualizada do subconjunto selecionado, funcionando como âncora para a análise detalhada abaixo.

---

### 2. Gráfico de Dispersão — Relação entre Variáveis

**Tipo**: Scatter plot (dispersão)  
**Eixos**: Selecionáveis pelo usuário (qualquer par das 11 variáveis)  
**Coloração**: Por nota de qualidade (escala de cores por nota 3–9)

Este gráfico permite ao usuário explorar livremente as relações entre pares de variáveis, colorindo cada ponto pela nota de qualidade atribuída ao vinho.

**Interpretações notáveis**:
- **Álcool vs. Acidez Volátil**: vinhos de alta qualidade (amarelo/laranja) tendem a se concentrar no canto superior esquerdo — alto álcool, baixa acidez volátil;
- **Álcool vs. Densidade**: correlação negativa clara — vinhos mais alcoólicos são menos densos;
- **pH vs. Acidez Fixa**: correlação negativa bem definida, esperada quimicamente.

---

### 3. Histograma de Distribuição de Qualidade

**Tipo**: Gráfico de barras (histograma de frequências)  
**Eixo X**: Notas de qualidade (3 a 9)  
**Eixo Y**: Número de amostras

Mostra a frequência de cada nota no subconjunto selecionado, com filtragem dinâmica pelos controles de qualidade mínima e máxima.

**Interpretação**: A concentração nas notas 5 e 6 confirma que o dataset reflete a realidade da produção vinícola — a maioria dos vinhos é mediana, e notas extremas são raras. Isso tem implicações diretas para modelos de classificação (desbalanceamento de classes).

---

### 4. Gráfico Radar — Perfil Médio por Categoria de Qualidade

**Tipo**: Radar chart (teia de aranha)  
**Dimensões**: 6 variáveis normalizadas (acidez fixa, acidez volátil, ácido cítrico, pH, sulfatos, álcool)  
**Series**: Vinhos de baixa qualidade (≤5) vs. alta qualidade (≥7)

Permite comparar visualmente o "perfil químico" de vinhos ruins versus vinhos bons.

**Interpretação**: Vinhos de alta qualidade (dourado) apresentam **maior teor alcoólico** e **maior concentração de ácido cítrico** (frescor), enquanto vinhos de baixa qualidade (vermelho) mostram **maior acidez volátil** — o marcador mais forte de defeito sensorial. A diferença no perfil é visualmente imediata neste formato.

---

### 5. Mapa de Calor — Matriz de Correlação

**Tipo**: Heatmap (mapa de calor)  
**Dimensões**: 12 × 12 variáveis  
**Escala**: Azul (correlação negativa) → Cinza (neutra) → Vermelho (correlação positiva)

Exibe a correlação de Pearson entre todos os pares de variáveis do dataset de vinho tinto.

**Interpretações principais**:

| Par de variáveis | Correlação | Interpretação |
|-----------------|------------|---------------|
| Acidez fixa ↔ Densidade | +0.67 | Acidez contribui para densidade |
| Acidez fixa ↔ Ácido cítrico | +0.67 | Ambos medem aspectos da acidez |
| Acidez fixa ↔ pH | -0.68 | Mais ácido = pH menor (esperado) |
| Álcool ↔ Densidade | -0.50 | Álcool reduz a densidade |
| **Álcool ↔ Qualidade** | **+0.48** | **Maior preditor positivo** |
| **Acidez volátil ↔ Qualidade** | **-0.39** | **Maior preditor negativo** |

---

### 6. Gráfico de Barras Horizontal — Correlações com Qualidade

**Tipo**: Barras horizontais ordenadas  
**Eixo X**: Coeficiente de Pearson (−0.5 a +0.6)  
**Cores**: Dourado para positivo, bordô para negativo

Resume de forma direta e ordenada quais variáveis mais influenciam a qualidade do vinho.

**Interpretação**: **Álcool** (r = +0.48) e **Sulfatos** (r = +0.25) são os maiores preditores positivos. **Acidez Volátil** (r = −0.39) e **SO₂ Total** (r = −0.19) são os maiores preditores negativos. Densidade (r = −0.17) e Cloretos (r = −0.13) também exercem influência negativa moderada.

---

### 7. Gráfico de Barras — Álcool Médio por Nota de Qualidade

**Tipo**: Barras verticais agrupadas por nota  
**Eixo X**: Notas de qualidade (3 a 9)  
**Eixo Y**: Teor alcoólico médio (%)

Evidencia a tendência crescente de álcool conforme a qualidade aumenta.

**Interpretação**: A relação é quase monotônica — vinhos nota 3 têm em média ~9.96% de álcool, enquanto vinhos nota 8 chegam a ~12.09%. Este padrão é consistente tanto em tintos quanto em brancos, sugerindo que o álcool é um proxy confiável de qualidade neste dataset específico.

---

## Interatividade Implementada

| Controle | Tipo | Efeito |
|----------|------|--------|
| **Toggle Tinto/Branco/Ambos** | Botão triplo | Altera todo o dashboard para o subconjunto selecionado |
| **Variável X** | Dropdown | Altera o eixo X do scatter plot |
| **Variável Y** | Dropdown | Altera o eixo Y do scatter plot |
| **Qualidade Mínima** | Slider (3–9) | Filtra amostras abaixo do valor selecionado |
| **Qualidade Máxima** | Slider (3–9) | Filtra amostras acima do valor selecionado |

Todos os controles são **reativos** — atualizam instantaneamente os gráficos afetados sem recarregar a página.

---

## Conclusão e Insights Obtidos

### Principais Achados

**1. O álcool é o maior preditor de qualidade**  
Com correlação de Pearson de +0.48 (tinto) e +0.44 (branco), o teor alcoólico é a variável individual mais associada a notas altas. Isso pode refletir tanto aspectos sensoriais (corpo, calor) quanto o processo de vinificação — uvas mais maduras geram mais açúcar, resultando em vinhos mais alcoólicos e, geralmente, mais complexos.

**2. A acidez volátil é o principal "inimigo" da qualidade**  
Correlação de −0.39 (tinto). Altos níveis de ácido acético indicam defeitos de fermentação e oxidação. É o sinal mais confiável de um vinho problemático.

**3. Sulfatos têm papel positivo moderado**  
Correlação de +0.25. Os sulfatos atuam como conservantes e antioxidantes — níveis adequados protegem o vinho e contribuem para sua longevidade e frescor.

**4. A maioria dos vinhos é "mediana"**  
Mais de 70% das amostras têm nota 5 ou 6. Notas 3, 4, 8 e 9 são raras. Isso reflete a realidade da produção em escala — a excelência e a baixíssima qualidade são exceções.

**5. Vinhos tintos e brancos têm perfis químicos distintos**  
Brancos têm muito mais açúcar residual (média 6.4 vs. 2.5 g/dm³) e SO₂ total (138 vs. 46 mg/dm³). Tintos têm maior acidez fixa e acidez volátil. Apesar dessas diferenças, os preditores de qualidade são similares em ambos.

### Limitações

- A nota de qualidade é a **média de avaliações de pelo menos 3 sommelliers** — há subjetividade inerente;
- O dataset é geograficamente restrito ao **Vinho Verde português** — os padrões podem não generalizar para outros estilos;
- Classes desbalanceadas dificultariam modelos preditivos sem técnicas de balanceamento (SMOTE, undersampling).

### Trabalhos Futuros

- Implementar modelo de **Random Forest ou XGBoost** para predição da qualidade;
- Adicionar **análise de componentes principais (PCA)** para redução dimensional;
- Coletar dados de outras regiões para avaliar generalização dos padrões encontrados.

---

## Como Executar

### Opção 1 — Arquivo HTML (sem servidor)

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/wine-quality-dashboard.git
cd wine-quality-dashboard

# Abra diretamente no navegador
open dashboard.html        # macOS
xdg-open dashboard.html    # Linux
start dashboard.html       # Windows
```

O arquivo `dashboard.html` funciona diretamente no navegador, sem necessidade de servidor.

### Opção 2 — Servidor local (recomendado)

```bash
# Python 3
python -m http.server 8000

# Acesse: http://localhost:8000/dashboard.html
```

### Requisitos

- Navegador moderno (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Conexão à internet (para carregamento das fontes e Chart.js via CDN)

---

## Estrutura do Projeto

```
wine-quality-dashboard/
├── dashboard.html    # Dashboard interativo completo
└── README.md         # Este relatório
```

---

## Referências

- **Dataset**: P. Cortez, A. Cerdeira, F. Almeida, T. Matos and J. Reis. *Modeling wine preferences by data mining from physicochemical properties.* Decision Support Systems, Elsevier, 47(4):547-553, 2009.
- **UCI Repository**: https://archive.ics.uci.edu/dataset/186/wine+quality
- **Chart.js Documentation**: https://www.chartjs.org/docs/latest/
- **Pandas Documentation**: https://pandas.pydata.org/docs/
- **Seaborn**: https://seaborn.pydata.org/

---

*Projeto desenvolvido como atividade da disciplina de Ciência de Dados.*
