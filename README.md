📋 Dashboard de Controle de Demandas e Processos

<img width="1312" height="743" alt="PAINEL CONTROLE DE DEMANDAS BI " src="https://github.com/user-attachments/assets/7d4a0ac2-f471-4ae6-9392-0dac7b6f8570" />


Este projeto consiste em uma solução de Business Intelligence para o monitoramento de fluxos processuais administrativos. O objetivo é fornecer visibilidade sobre o volume de entradas/saídas, cumprimento de prazos e distribuição de carga de trabalho por áreas responsáveis.

🚀 Tecnologias Utilizadas
Power BI (Visualização e Modelagem)

DAX (Cálculo de métricas de performance)

Excel/CSV (Fonte de dados)

Figma (Deisgn de interface e Background customizado) 

📊 O Problema de Negócio
A gestão de processos exige rastreabilidade rigorosa. A falta de um painel centralizado dificultava identificar gargalos em etapas específicas (como "Assinatura de Contrato" ou "Publicação de Portaria") e o monitoramento de processos atrasados em relação à data limite.

🛠️ Estrutura dos Dados
A base de dados é composta por colunas detalhadas que permitem granularidade na análise:

Nº do Processo: Identificador único.

Área Demandante/Interna: Fluxo de responsabilidade entre departamentos.

Etapa/Assunto: Detalhamento do ciclo de vida do processo.

Situação: Status atual (Em Andamento, Concluído).

🧮 Inteligência de Dados (Medidas DAX)
Para extrair insights reais, foram desenvolvidas medidas personalizadas. Abaixo, os principais destaques técnicos:

1. Taxa de Conclusão
Métrica fundamental para entender a eficiência do fluxo.

Snippet de código
%_CONCLUIDOS = 
DIVIDE(
    [Processos_CONCLUIDOS], 
    [Total_Processos], 
    0
)
2. Monitoramento de Atrasos
Cálculo dinâmico que compara a data de conclusão com o limite acordado.

Snippet de código
ATRASADOS = 
SUMX(
    'Planilha1', 
    IF('Planilha1'[DATA CONCLUSÃO DEMANDA] > 'Planilha1'[DATA LIMITE ATENDIMENTO], 1, 0)
)
3. Gestão de Estoque (Backlog)
Controle de processos que ainda requerem ação da equipe.

Snippet de código
Processos_Em_Andamento = 
CALCULATE(
    COUNTROWS('Planilha1'),
    'Planilha1'[SITUAÇÃO] = "EM ANDAMENTO",
    ALL('Planilha1') 
)
📈 Insights Gerados
Visibilidade de SLA: Identificação exata de quais áreas possuem maior volume de processos fora do prazo.

Categorização por Bens: Análise de demandas focadas em "Bens Permanentes" vs "Consumo".

Fluxo de Entrada/Saída: Balanceamento de carga de trabalho mensal.
