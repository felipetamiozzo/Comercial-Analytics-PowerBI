
```markdown
# 📊 Comercial Analytics - Dashboard Gerencial

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![UI/UX](https://img.shields.io/badge/UI/UX-Design-FF007F?style=for-the-badge)

Este repositório contém um dashboard gerencial de alto nível para análise de performance comercial. O projeto simula a experiência fluida de um aplicativo web (App-like experience) através de uma navegação interativa e refinamento visual de primeiríssima linha.

O foco foi transformar dados brutos em insights estratégicos e operacionais claros, utilizando técnicas avançadas de DAX, HTML/CSS incorporado e modelagem Star Schema.

## 🎯 Objetivo e Contexto de Negócio
O objetivo é fornecer à diretoria e às equipes de operações comerciais uma ferramenta ágil para o monitoramento de KPIs críticos. O painel permite identificar gargalos na margem de lucro, gerenciar sazonalidade de vendas e ranquear a performance regional e individual dos vendedores, tudo em um layout intuitivo e focado na experiência do usuário.

## 📂 Estrutura do Repositório

```text
📦 Comercial_Analytics
 ┣ 📂 Comercial_Analytics.Report         # Arquivos de projeto do relatório
 ┣ 📂 Comercial_Analytics.SemanticModel  # Metadados do modelo semântico
 ┣ 📂 assets                             # Capturas de tela e plano de fundo poligonal
 ┣ 📂 data                               # Amostra do dataset e dicionário de dados
 ┣ 📂 dax_scripts                        # Códigos DAX HTML/CSS dos botões e títulos
 ┣ 📜 Comercial_Analytics.pbip           # Arquivo de Projeto do Power BI (Source Control)
 ┣ 📜 Comercial_Analytics.pbix           # Arquivo executável completo do Power BI
 ┗ 📜 README.md                          # Documentação do projeto

```

## 🚀 Navegação e Experiência do Usuário (UI/UX)

A interface foi desenhada para guiar o usuário em uma jornada analítica.

**1. Home (Capa Interativa)**
Esta tela funciona como um HUB central. Os botões foram desenvolvidos com medidas DAX incorporando HTML/CSS para criar efeitos corporativos de *Glassmorphism*, sombras e Hover Effects dinâmicos (ao passar o mouse).

## 📈 Análise Geral e KPIs Chave (Visão Executiva)

Esta visão consolida os principais indicadores para uma rápida tomada de decisão da diretoria.

**Principais Insights e Métricas Chave:**

* **Faturamento Total de R$ 359k:** Mostra um crescimento sólido de +2.3% MoM (Mês sobre Mês).
* **Crescimento do Volume de Vendas:** Aumento de +3.6%, totalizando 457 vendas.
* **Lucro Líquido de R$ 290k:** Alta de +2.1% MoM, com uma margem de lucro saudável.
* **Alerta de Ticket Médio (-1.3%):** Identificação de uma leve queda MoM, sugerindo a necessidade de rever estratégias de precificação ou mix de produtos.
* **Análise de Mix:** A categoria "Eletrodomésticos" lidera o faturamento com R$ 193 mil. "Brastemp" é o fabricante com maior performance (R$ 93 mil). O segmento "Doméstico" concentra a maior parte das vendas.

## 📅 Gerenciamento de Sazonalidade e Tendências (Visão Temporal)

Esta análise foca em entender como as métricas se comportam ao longo do tempo.

**Principais Insights e Métricas Chave:**

* **Picos de Faturamento em JAN (+50%) e SET (+36%):** Identificação de meses com alta performance sazonal.
* **Alerta de Margem de Lucro:** Mostra uma tendência de queda no final do ano, com um ponto de atenção em AGO.
* **Quedas de Faturamento MoM:** Monitoramento das variações negativas em JUN (-29%) e AGO (-36%).
* **Monitoramento de Margem e Custos:** A comparação entre "Faturamento", "Custos" e "Margem" permite antecipar problemas de rentabilidade.
* **Análise Combinada:** O gráfico de linhas duplas permite correlacionar Volume de Vendas e Ticket Médio para entender o impacto total no faturamento mensal.

## 👤 Performance Regional e de Vendedores (Visão Operacional)

Foco em métricas para a gestão de equipes e estratégias geográficas.

**Principais Insights e Métricas Chave:**

* **Concentração Geográfica SP e RJ:** São Paulo lidera o faturamento com R$ 184 mil, seguido pelo Rio de Janeiro com R$ 107 mil. Estes dois estados concentram a maior parte do resultado comercial.
* **Análise de Top Performers:** O vendedor André Pereira lidera com R$ 87 mil em faturamento, destacando-se significativamente da média da equipe.
* **Análise de Lojas:** O gráfico de dispersão permite identificar lojas com alta performance de vendas e margem de lucro, facilitando a identificação de *outliers* de sucesso.

## 🛠️ Destaques Técnicos

* **Integração HTML/CSS no DAX:** Desenvolvimento de componentes visuais 100% customizados e interativos (hover effect dinâmico), superando as limitações visuais nativas do Power BI para criar uma experiência de aplicativo.
* **Inteligência de Tempo no DAX:** Cálculos avançados para medição de variações Mês sobre Mês (MoM) de Faturamento, Lucro, Volume e Ticket Médio.
* **Governança de Medidas:** Implementação de *Display Folders* (Pastas de Exibição) para uma estruturação lógica e limpa de medidas, visando escalabilidade e manutenção do código corporativo.
* **Modelagem Star Schema:** Organização do modelo semântico otimizado para performance.

---
