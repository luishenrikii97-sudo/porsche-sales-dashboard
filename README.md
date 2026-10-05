# 🏎️ Porsche Sales Performance Dashboard

Dashboard interativa de vendas desenvolvida para o desafio prático da DIO. O projeto transforma uma planilha sanitizada de 100 vendas da marca Porsche num painel web dinâmico, acessível via navegador e sem dependências do Excel.

🔗 **Link da Dashboard Online:** https://luishenrikii97-sudo.github.io/porsche-sales-dashboard/

---

## 📌 Perguntas de Negócio Respondidas

1. **Qual é o modelo responsável pelo maior volume de faturamento?**
   - *Objetivo:* Avaliar a representatividade financeira de cada linha de veículos (ex: 911 vs. SUV Cayenne/Macan) para direcionar esforços comerciais.
2. **Qual é a distribuição dos métodos de pagamento preferidos pelos clientes?**
   - *Objetivo:* Entender o perfil de liquidez dos compradores (PIX, Financiamento e À Vista) para calibrar condições financeiras no atendimento.
3. **Qual é a evolução do volume de vendas segundo o ano de fabricação do veículo?**
   - *Objetivo:* Mapear a aderência do estoque entre veículos 0km e seminovos recentes no portfólio.

---

## 🛠️ Tratamento Prévio da Base de Dados

Antes da integração com a IA, a planilha passou pelo seguinte fluxo de sanitização:
- **Filtro de Colunas:** Manutenção exclusiva das colunas sanitizadas (`modelo`, `cidade`, `estado`, `ano`, `preco` e `metodo_pagamento`).
- **Formatação de Valores:** Remoção de símbolos de moeda (`R$`) e separadores de milhar na coluna `preco`, garantindo tipo numérico puro (`float`).
- **Normalização do Ano:** Conversão da coluna `ano` para inteiro simples sem formatação de data.
- **Limpeza de Fórmulas:** Copiado e colado apenas os valores brutos para eliminar quebras de fórmula.

---

## 🤖 Engenharia de Prompt e Iterações

O desenvolvimento do front-end foi realizado via IA generativa utilizando a seguinte abordagem:

### Prompt Inicial
> *"Atue como um Desenvolvedor Front-end e BI Sênior. Crie uma dashboard interativa em um único arquivo HTML contendo Tailwind CSS e Chart.js. O estilo deve ser Dark Mode inspirado na marca Porsche (fundo #0E0E10, destaques vermelho carmim #D5001C). Adicione 3 KPIs no topo (Receita, Vendas, Ticket Médio), 3 filtros interativos (Modelo, Estado e Pagamento) e 3 gráficos para responder às perguntas de negócio. Incorpore a base sanitizada diretamente em JSON no JavaScript."*

### Refinamentos e Ajustes
- **Reatividade:** Ajustada a função de escuta dos filtros (`addEventListener`) para recarregar simultaneamente os KPIs e destruir/recriar as instâncias dos gráficos do Chart.js.
- **Responsividade:** Configurada a grade usando o sistema de grid do Tailwind para manter a usabilidade em dispositivos móveis.

---

## 📊 Funcionalidades
- **KPIs Dinâmicos:** Cálculo em tempo real de Receita Total, Volume Vendido e Ticket Médio.
- **Filtros Cruzados:** Filtragem simultânea por Modelo, Estado (UF) e Forma de Pagamento.
- **Visualização Gráfica:** Gráfico de barras para faturamento por modelo, gráfico de rosca para métodos de pagamento e gráfico de linha para ano do veículo.
