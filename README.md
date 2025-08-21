# Superlota-o-de-Leitos-Hospitalares.ipynb
Projeto EBAC em parceria com a Sematrix
# 🏥 Superlotação de Leitos Hospitalares – Visualização e Análise

> **Objetivo:** analisar a ocupação de leitos no Brasil, apontar estados críticos, principais causas de internação, sazonalidade e recomendações de gestão.  
> Visualização interativa no **Looker Studio** e modelo simples de previsão em **Python (Colab)**.

---

## 🔗 Visualização (Looker Studio)
- Dashboard público: https://lookerstudio.google.com/reporting/15fa1cdb-20b1-42c7-998b-349ccb4dd072

---

## 📥 Coleta de Dados
- Base utilizada: `data/dados_hospitalares_corrigidos.csv` (derivada de planilha Google Sheets).
- Variáveis:
  - `AnoMes` (data)
  - `Estado` / `UF_Brasil_ISO` (para mapa)
  - `Internacoes`, `Leitos_Disponiveis`
  - `Tempo_Medio_Internacao` (dias)
  - `Taxa_Ocupacao` (%)
  - `Leitos_por_100mil`
- Observações:
  - Tipos numéricos ajustados (decimais/inteiros).
  - Criação de `AnoMes` (data) e `UF_Brasil_ISO` (ex.: BR-SP) para mapa.
  - Padronização para leitura no Looker.

---

## 🧹 Modelagem
- **Tratamento**: limpeza, padronização de tipos, criação de campos calculados.
- **Métricas no dashboard**:
  - **Taxa de Ocupação (%)** = Internações / Leitos_Disponiveis × 100
  - **Leitos por 100 mil hab.**
  - **Tempo médio de internação (dias)**
- **Visualizações**:
  - KPIs principais
  - Série temporal (Taxa_Ocupacao por `AnoMes`, filtrável por Estado)
  - Mapa preenchido por UF (heatmap)
  - Barras – Top CIDs (principais causas)
  - Tabela dinâmica (ranking por Estado)
  - Página de alertas (limites de 80% e 90%)
- **Modelagem Preditiva (Python)**:
  - Algoritmo: Regressão Linear (didático).
  - Preditoras: `Mes_num` (tempo) + `Internacoes`.
  - Saída: previsão de **Taxa_Ocupacao** para 6 meses.
  - Notebook: `notebooks/previsao_ocupacao_leitos.ipynb`.

---

## 📊 Resultados (prints do dashboard)
| KPIs | Série Temporal | Mapa | Barras (CID) |
|---|---|---|---|
| ![kpi](file:///C:/Users/Jo%C3%A3o/Downloads/Looker%20-%20Prints.pdf) | ![serie](file:///C:/Users/Jo%C3%A3o/Downloads/Looker%20-%20Prints.pdf) | ![mapa](file:///C:/Users/Jo%C3%A3o/Downloads/Looker%20-%20Prints.pdf) | ![barras](file:///C:/Users/Jo%C3%A3o/Downloads/Looker%20-%20Prints.pdf) |

---

## 🧠 Conclusões
- **Estados mais críticos:** maiores taxas de ocupação e permanência longa → risco de superlotação.
- **Doenças que mais pressionam leitos:** respiratórias (pneumonia/asma), crônicas (diabetes), infecciosas agudas.
- **Sazonalidade:** inverno (jun–ago) eleva internações respiratórias; epidemias sazonais intensificam o risco.
- **Recomendações de gestão:**
  - Redistribuir recursos para estados críticos.
  - Ativar **leitos temporários** em picos sazonais.
  - **Monitorar continuamente** via dashboard.
  - **Prevenção** (vacinação e controle de crônicos) para reduzir demanda.

---

## 👨‍💻 Autor
**João Vitor Ferreira Freitas**  
- 📧 E-mail: freitasfj1999@gmail.com 
- 🔗 LinkedIn: https://www.linkedin.com/in/jo%C3%A3o-vitor-ferreira-freitas-37837a20b/
