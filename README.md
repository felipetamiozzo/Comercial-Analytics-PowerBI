
# Comercial Analytics | PowerBI

![Capa do Projeto](assets/capa.jpg) 

## 📋 Visão Geral do Projeto
Este projeto de Análise de Dados foi desenvolvido para monitorar indicadores estratégicos de vendas, faturamento e performance comercial. Seguindo padrões de mercado em nível de excelência, o dashboard transforma dados brutos em insights acionáveis, entregando à diretoria e aos gestores uma ferramenta ágil para identificar gargalos na margem de lucro e ranquear a performance regional e individual.

O projeto se destaca por simular a experiência fluida de um aplicativo web (App-like experience), utilizando técnicas avançadas de inteligência de tempo no DAX, formatações condicionais de alto nível e customizações de interface inovadoras usando HTML e CSS nativamente dentro do Power BI.

---

## 📁 Estrutura do Repositório
O projeto foi organizado para facilitar a compreensão do fluxo de dados, versionamento e manutenção:

```text
📁 Comercial_Analytics
 ┣ 📂 assets                             # Prints e imagens do dashboard
 ┣ 📂 data                               # Base de dados original / Dicionário
 ┣ 📂 dax_scripts                        # Lógica avançada de cartões HTML/CSS e MoM
 ┣ 📂 Comercial_Analytics.Report         # Metadados do relatório (.pbip)
 ┣ 📂 Comercial_Analytics.SemanticModel  # Metadados do modelo semântico (.pbip)
 ┣ 📄 Comercial_Analytics.pbip           # Projeto (Versão técnica versionada)
 ┣ 📄 Comercial_Analytics.pbix           # Projeto (Versão clássica)
 ┗ 📄 README.md                          # Documentação completa do projeto

```

---

## 🎯 Estrutura de Análise (Módulos)

O dashboard foi projetado como uma aplicação interativa, dividida em um HUB central e 3 pilares analíticos:

1. **Capa Interativa (Home):** Ponto de partida com navegação guiada por botões HTML interativos.
2. **Visão Executiva:** Resumo de alto nível (Faturamento, Lucro, Volume, Ticket Médio) e composição de vendas por categoria e fabricante.
3. **Visão Temporal:** Acompanhamento de sazonalidade, evolução Mês a Mês (MoM) de faturamento e correlação de margem de lucro vs. custos.
4. **Visão Operacional:** Avaliação de performance geográfica (por estado) e ranqueamento dos Top 5 Vendedores e lojas de destaque.

---

## 🖥️ Telas do Dashboard e Métricas Chave

### 1. Visão Executiva

**Principais Insights do Módulo:**

* **Faturamento Total:** R$ 359,3 mil (Crescimento sustentável de +2.3% MoM).
* **Lucro Líquido:** R$ 290,8 mil (+2.1% MoM), demonstrando excelente rentabilidade frente aos custos operacionais.
* **Volume vs Ticket:** Foram registradas 457 vendas (+3.6%). O Ticket Médio ficou em R$ 786,23, apresentando um leve alerta de queda (-1.3%) que exige atenção nas estratégias de *upsell*.
* **Análise de Mix (Top Performers):** A categoria "Eletrodomésticos" domina as receitas (R$ 193 mil), com a marca "Brastemp" liderando o faturamento individual de fabricantes (R$ 93 mil).

### 2. Visão Temporal

**Principais Insights do Módulo:**

* **Sazonalidade e Picos:** Identificação clara de meses com altíssima performance, com picos de crescimento de faturamento em Janeiro (+50%) e Setembro (+36%).
* **Controle de Margem de Lucro:** A margem manteve-se estável acima de 80% na maior parte do ano, sofrendo quedas sensíveis nos meses de Agosto e Dezembro (ponto focal de investigação de custos).
* **Variações Críticas:** Quedas acentuadas de faturamento mês a mês foram detectadas em Junho (-29%) e Agosto (-36%).

### 3. Visão Operacional

**Principais Insights do Módulo:**

* **Dominância Regional (Sudeste):** São Paulo (R$ 184 mil) e Rio de Janeiro (R$ 107 mil) concentram quase a totalidade das receitas comerciais.
* **Top Performers (Vendas):** O vendedor André Pereira isolou-se em primeiro lugar, convertendo R$ 87 mil em faturamento, apresentando uma performance muito superior à média da equipe de vendas.
* **Oportunidade e Alinhamento:** O gráfico de dispersão revela a correlação entre margem e desempenho bruto das lojas, evidenciando unidades de negócio que requerem planos de ação específicos.

---

## ⚙️ ETL e Tratamento de Dados (Power Query)

Os dados brutos passaram por um rigoroso processo de estruturação para compor um modelo Star Schema otimizado para performance:

* **Tabela Fato (`Vendas`):**
* Tipagem estrita de dados financeiros e operacionais (Faturamento, Custos, Comissão).
* Criação de chaves substitutas para relacionamento seguro com as dimensões.


* **Dimensão de Tempo (`dCalendario`):**
* Tabela gerada dinamicamente (Relacionamento 1:N).
* Extração de features temporais auxiliares (Ano, Mês, Num_Mes) essenciais para as análises de Inteligência de Tempo (Time Intelligence).



---

## 🧠 Modelagem e Linguagem DAX

O projeto utiliza um modelo relacional otimizado, governança rigorosa de medidas via *Display Folders* (Pastas de Exibição) e conceito de *Measure Branching*. Abaixo, algumas das principais métricas desenvolvidas:

**Lógica de Negócios (Measure Branching):**

```dax
Faturamento Total = SUM(Vendas[ValorVenda])
Custo Total = SUM(Vendas[Custo])
Total Comissão = SUM(Vendas[Valor Comissão ])

Lucro Líquido = [Faturamento Total] - [Custo Total] - [Total Comissão]
Margem de Lucro % = DIVIDE([Lucro Líquido], [Faturamento Total], 0)

```

**Inteligência de Tempo e Variações (MoM):**

```dax
Faturamento Mês Anterior = 
CALCULATE(
    [Faturamento Total],
    DATEADD(dCalendario[Date], -1, MONTH)
)

Var % Faturamento = 
DIVIDE(
    [Faturamento Total] - [Faturamento Mês Anterior],
    [Faturamento Mês Anterior]
)

```

**Formatação Condicional Avançada via Variáveis:**

```dax
-- Exemplo de estrutura condicional aplicada dentro dos cartões HTML
VAR Indicador =
IF(
    ISBLANK(Perc), "",
    IF(Perc >= 0,
        "<div style='color:#6EEB83;'> ▲ " & FORMAT(Perc,"0.0%") & "</div>",
        "<div style='color:#FF8A80;'> ▼ " & FORMAT(ABS(Perc),"0.0%") & "</div>"
    )
)

```

---

## 🎨 UI/UX e Data Storytelling

* **HTML Content no DAX:** Criação de componentes visuais 100% customizados, superando limitações nativas da ferramenta.
* **App-Like Experience:** Utilização de *Glassmorphism* (Brilho interno e transparências), gradientes em botões e efeitos dinâmicos (*Hover effects* que reagem ao passar o mouse).
* **Paleta Estratégica:** Layout *clean* com contraste bem definido entre os tons de azul e roxo institucionais para guiar a atenção aos KPIs, com uso semântico de verde/vermelho para indicadores de performance.

---

## 🚀 Como Visualizar

1. Faça o clone: `git clone https://github.com/felipetamiozzo/Comercial_Analytics.git`
2. Abra o arquivo `Comercial_Analytics.pbix` no Power BI Desktop.

---

## 👨‍💻 Autor

**Felipe Tamiozzo** | *Analista de Dados*

* [LinkedIn](https://www.linkedin.com/in/felipetamiozzo/)
* [GitHub](https://github.com/felipetamiozzo)

```

