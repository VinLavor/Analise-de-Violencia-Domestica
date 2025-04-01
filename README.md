📌 Visão Geral

Este projeto realiza uma análise exploratória e preditiva de um conjunto de dados sobre violência doméstica, com o objetivo de:
✅ Identificar padrões nas vítimas e agressores.
✅ Prever níveis de violência com modelos de machine learning.
✅ Agrupar perfis de agressores usando técnicas de clustering.

Os dados foram coletados de formulários de avaliação de risco, contendo informações sobre agressões físicas, psicológicas, perfil socioeconômico e histórico de violência.
📂 Estrutura do Projeto

O projeto foi dividido em 4 etapas principais:

    📊 Preparação e Organização dos Dados

    🔍 Análise Inicial e Exploração

    📈 Visualização e Correlações

    🤖 Modelagem Preditiva e Clusterização

🔧 1. Preparação e Organização dos Dados
Objetivo

Transformar os dados brutos em um formato adequado para análise, tratando valores ausentes, corrigindo inconsistências e criando novas variáveis.
Processos Realizados
📌 Tratamento das Perguntas do Formulário

    Perguntas binárias (Sim/Não) foram convertidas em 0 e 1.

        Exemplo:

            "Você necessitou de atendimento médico após agressão?" → Atendimento médico (0 ou 1)

    Perguntas com múltiplas respostas foram transformadas em colunas separadas.

        Exemplo:

            "O agressor já praticou alguma destas agressões físicas?" → Colunas Chute (0/1), Empurrão (0/1), etc.

📊 Categorização da Violência

    Violência Leve: Chute, Empurrão, Puxão de cabelo, Soco, Tapa.

    Violência Média: Afogamento, Enforcamento, Estrangulamento, Sufocamento.

    Violência Pesada: Facada, Paulada, Queimadura, Tiro.

    Pontuação Total de Violência: Soma ponderada (leve=1, média=2, pesada=3).

🔍 Tratamento de Dados Ausentes

    Valores faltantes foram substituídos pela moda (valor mais frequente) de cada coluna.

✂️ Remoção de Redundâncias

    Colunas pouco informativas ou altamente correlacionadas foram removidas.

        Exemplo: "Não tenho filhos" (já representado em outras colunas).

🔍 2. Análise Inicial dos Dados
Objetivo

Entender a distribuição dos dados e identificar padrões iniciais.
Principais Descobertas
📊 Distribuição das Vítimas por Etnia

    Pardas: Maioria das vítimas (≈60%).

    Brancas e Pretas: Segunda maior ocorrência.

    Indígenas e Amarelas/Orientais: Menos representadas (possível subnotificação).

⚖️ Níveis de Violência

    Violência leve: Mais frequente.

    Violência grave: Menos comum, mas presente principalmente em vítimas pardas.

🚨 Ocorrências Policiais

    Baixo registro: A maioria das vítimas não registra ocorrência, mesmo em casos graves.

    Agressores que usam drogas/álcool: Maior probabilidade de registro policial.

📊 3. Análise Multivariada e Visualização
Objetivo

Identificar relações entre variáveis e comportamentos recorrentes.
Principais Insights
🔗 Correlações Entre Comportamentos do Agressor
Comportamento 1	Comportamento 2	Relação
Prisão domiciliar	Proibição de carreira	Forte
Comunicação insistente	Vigilância constante	Forte
Dependência financeira	Bloqueio financeiro	Forte
Separação recente	Conflito de guarda	Moderada
📉 Gráficos Principais

    Violência por Etnia

        Pardas sofrem mais violência em todos os níveis.

    Relação entre Separação Recente e Violência

        Mulheres que tentam se separar sofrem mais agressões.

    Impacto do Uso de Álcool/Drogas

        Agressores sob efeito de substâncias cometem mais violência grave.

🤖 4. Modelagem Preditiva e Clusterização
📌 Modelo 1: Regressão (XGBoost)

Objetivo: Prever o nível total de violência com base nas características do agressor e da vítima.
Resultados:
✅ R² = 82% (explica 82% da variação nos dados).
✅ MAE = 0.85 (erro médio baixo).
📌 Modelo 2: Random Forest

Melhoria em relação à regressão:
✅ R² = 85% (melhor ajuste).
✅ MAE = 0.78 (menor erro).
📌 Modelo 3: K-Means (Perfis de Agressores)

Número de Clusters: 3 (definido pelo método do cotovelo).
Perfis Identificados:

    Controlador e Ciumento

        Alta taxa de controle, ciúmes e agressões recentes.

    Agressor sob Efeito de Substâncias

        Uso de álcool/drogas associado a violência.

    Agressor Possessivo

        Prisão domiciliar, bloqueio financeiro e vigilância constante.

Índice Davies-Bouldin = 1.2 (clusters razoavelmente bem separados).
📌 Conclusões e Recomendações
Principais Achados

🔹 Perfil das Vítimas: Mulheres pardas são as mais afetadas.
🔹 Subnotificação: Poucas vítimas registram ocorrências policiais.
🔹 Perfil dos Agressores:

    Uso de substâncias aumenta gravidade da violência.

    Comportamentos controladores são frequentes.

Aplicações Práticas

🚨 Políticas Públicas:

    Campanhas de conscientização para vítimas pardas.

    Apoio psicológico e jurídico para mulheres em processo de separação.

🤖 Próximos Passos:

    Coletar mais dados de grupos sub-representados (indígenas, amarelas).

    Testar outros modelos (ex.: Redes Neurais).
