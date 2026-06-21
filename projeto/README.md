# DataView: Exploração e Análise de Dados de Vendas 📊

## 1. Contextualização do Projeto
Este é um miniprojeto de Análise de Dados desenvolvido para gerar insights estratégicos a partir de um histórico de vendas. O objetivo principal foi atuar como um Analista de Dados Júnior, recebendo um dataset bruto com inconsistências estruturais, e aplicar um pipeline completo de limpeza, transformação e análise com foco em uma reunião trimestral da diretoria.

## 2. Diferenciais do Projeto 💡
Além das exigências técnicas básicas, este projeto conta com duas entregas de alto valor para o negócio:
* **Relatório Executivo Automatizado:** O script não apenas gera gráficos, mas traduz as métricas de negócio (Ticket Médio, Sazonalidade e Segmentação) em insights e recomendações diretas em formato de texto para facilitar a tomada de decisão gerencial.
* **Análise Multivariada (Pairplot):** Utilização avançada da biblioteca Seaborn para cruzar simultaneamente Preço, Quantidade e Receita, agrupados por região geográfica, revelando padrões complexos de comportamento de compra em uma única visualização.

## 3. Decisões Técnicas e Arquitetura
O código foi estruturado de forma profissional, seguindo o padrão de **Pipeline Modular**, onde cada etapa da análise é encapsulada em funções reutilizáveis. Os principais tratamentos aplicados foram:
* **Limpeza Inicial:** Remoção de valores nulos em colunas financeiras e correção de datas inválidas usando coerção. Espaços extras em strings foram tratados com Expressões Regulares (Regex).
* **Tratamento de Outliers (IQR):** Utilizamos o método do Intervalo Interquartil. O pipeline gera duas versões dos dados: a **v1 (com outliers)** e a **v2 (sem outliers)**. Optou-se por utilizar a versão tratada para a geração do Relatório Executivo e gráficos finais, garantindo que anomalias não distorcessem o Ticket Médio.
* **Segmentação:** Clientes foram segmentados em categorias (Bronze, Prata, Ouro) usando funções Lambda (`lambda`), revelando padrões de concentração de receita.

## 4. Estrutura de Diretórios
A organização do projeto segue boas práticas de engenharia de dados:

```
/data
  /raw                    # Dataset original gerado intencionalmente sujo
  /processed
    /v1_com_outliers      # Dados limpos, mas mantendo anomalias
    /v2_outliers_tratado  # Dados limpos e sem anomalias (Base oficial)
  /final                  # Tabela final enriquecida para futuros modelos de IA
/outputs
  /graficos               
    receita_por_mes.png
    top_produtos.png
    dist_regiao.png
    pairplot_multivariado.png # [Diferencial]
  estatisticas_gerais.json    # Resumo estatístico gerado via NumPy
  metricas_por_mes.csv        # Agregações mensais
  segmentacao_clientes.csv    # Classificação de clientes VIP
dataview.ipynb                # Notebook principal com o pipeline documentado
README.md                     # Documentação do projeto
```

## 5. Tecnologias Utilizadas
* **Python 3**
* **Pandas:** Manipulação de dados, agrupamentos e limpeza.
* **NumPy:** Cálculos estatísticos diretos e lógicas condicionais vetorizadas.
* **Matplotlib & Seaborn:** Visualização de dados simples e multivariada.
* **Regex (re) & Datetime:** Tratamento de strings e manipulação temporal.

## 6. Como Executar
1. Clone este repositório.
2. Certifique-se de ter as bibliotecas instaladas executando no terminal: `pip install pandas numpy matplotlib seaborn`
3. Abra o arquivo `dataview.ipynb` na sua IDE de preferência (Jupyter, VS Code) ou faça o upload no Google Colab.
4. Execute a célula final que contém a função principal do pipeline. Todo o fluxo de limpeza, gráficos e a estrutura de pastas serão gerados automaticamente.