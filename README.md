# 📊 Projeto Power BI - Análise de Vendas, Lucro e Logística - Lab 2 - Data Science Academy

## 📌 Sobre o Projeto

Este projeto foi desenvolvido como parte de um exercício prático com múltiplas tabelas relacionais, onde o desafio foi construir um dashboard no Power BI capaz de responder perguntas estratégicas relacionadas a vendas, lucro, transporte e comportamento do mercado.

A proposta envolvia também identificar possíveis falhas de relacionamento entre tabelas e aplicar boas práticas em modelagem de dados, garantindo que os resultados fossem consistentes e confiáveis.

---

## 📁 Estrutura dos Dados

O projeto foi construído a partir de **quatro tabelas** principais:

- `Clientes`
- `Pedidos`
- `Vendas`
- `Produtos`

Antes de iniciar a visualização dos dados, foi necessário realizar a **modelagem relacional**, validando:

- Relacionamentos (cardinalidade 1:* e *:1)
- Remoção de duplicatas
- Tipagem e transformação de dados no **Power Query**

> 💡 Todos os relacionamentos foram ajustados na aba **Relationship View**, com análise prévia de duplicidades, cardinalidade e modelo de negócio.

---

## ❓ Perguntas Respondidas no Dashboard

### 1. 💸 Qual foi o total de valor de venda considerando cada modo de envio dos pedidos?
- **Gráfico usado:** Cascata  
- **Configuração:**  
  - Eixo Y: `Valor Venda` (tabela Vendas)  
  - Categoria: `Modo Envio` (tabela Pedidos)

---

### 2. 🌍 Quais mercados tiveram o maior custo médio de envio dos produtos vendidos?
- **Gráfico usado:** Treemap  
- **Configuração:**  
  - Categoria: `Mercado` (tabela Clientes)  
  - Valores: `Custo Envio` (tabela Vendas, agregado como **média**)

---

### 3. 🎯 A empresa manteve a média de 350 no valor de venda em Abril/2014?
- **Gráfico usado:** Indicador / Velocímetro  
- **Configuração:**  
  - Valor: `Valor Venda` (agregado como **média**)  
  - Meta: 350 (configurado no eixo do velocímetro)

- **Filtro adicional:**  
  - **Segmentação de dados:** `Data Pedido` (filtrado para Abril/2014)  
  - Permitiu analisar se a meta foi superada ou não.

---

### 4. 📈 Qual categoria de produto apresentou maior lucro médio?
- **Cálculo de Lucro:**  
  - Criada nova coluna: `Lucro = Valor Venda - Custo Envio`

- **Gráfico usado:** Rosca  
- **Configuração:**  
  - Legenda: `Categoria` (tabela Produtos)  
  - Valores: `Lucro` (agregado como **média**)

---

### 5. 🔍 Qual foi o comportamento da margem de lucro ao longo do tempo?

- **Cálculo da Margem de Lucro:**  
  - Criada nova coluna em DAX:
    ```DAX
    Margem_Lucro = ROUND(DIVIDE(Vendas[Lucro], Vendas[Valor Venda]) * 100, 2)
    ```
- **Gráfico usado:** Linha  
- **Configuração:**  
  - Eixo X: `Data Pedido` (tabela Pedidos)  
  - Eixo Y: `Margem_Lucro` (agregado como **média**)

---

## 🧩 Modelagem e Transformações

- Ajuste de cabeçalhos incorretos no Power Query (`Usar primeira linha como cabeçalho`)
- Detecção e remoção de dados duplicados nas chaves de relacionamento
- Aplicação correta de **cardinalidades**:
  - 1:* entre Produtos e Vendas
  - 1:* entre Pedidos e Vendas
- Criação de colunas calculadas e medidas com **DAX**
- Uso de **M Language** nas transformações automáticas do Power Query

---

## 📚 Aprendizados

- Importância da modelagem de dados antes da visualização
- Validação de relacionamentos entre tabelas para garantir integridade nas análises
- Criação de colunas calculadas com DAX e transformação com M Language
- Escolha apropriada de gráficos para perguntas específicas
- Interatividade com segmentações de dados para análises temporais e comparativas

---

