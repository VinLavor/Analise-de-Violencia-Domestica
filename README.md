# 📌 Visão Geral

Este projeto realiza uma análise exploratória e preditiva de um conjunto de dados sobre violência doméstica, com o objetivo de:
-✅ Identificar padrões nas vítimas e agressores.
-✅ Prever níveis de violência com modelos de machine learning.
-✅ Agrupar perfis de agressores usando técnicas de clustering.

Os dados foram coletados de formulários de avaliação de risco, contendo informações sobre agressões físicas, psicológicas, perfil socioeconômico e histórico de violência.
## 📂 Estrutura do Projeto

O projeto foi dividido em 4 etapas principais:

- 📊 Preparação e Organização dos Dados

- 🔍 Análise Inicial e Exploração

 - 🤖 Modelagem Preditiva e Clusterização

# 🔧 1. Preparação e Organização dos Dados / Qualidade de Dados (Etapas 1 e 2)
Objetivo

Nessa etapa, fiz a transformação das perguntas, que inicialmente estavam em formato de formulário, da sequinte maneira:
- Se a pergunta for binária (Resposta Sim ou Não), ela viraria uma só coluna, que poderia ter valor 0 ou 1.
- Se a pergunta for de múltipla escolha, cada uma de suas respostas viraria uma nova coluna, de valor 0 ou 1 para indicar qual era a resposta da pergunta
Exemplo:

"Você necessitou de atendimento médico após agressão?" → Atendimento médico (0 ou 1)


Exemplo:

"O agressor já praticou alguma destas agressões físicas?" → Colunas Chute (0/1), Empurrão (0/1), etc.

## 📊 Categorização da Violência
Nessa etapa, no intuito de diminuir um pouco o número de colunas do nosso dataset, categorizamos todos os tipos de violência sofridas em leve, média e pesada, e com base nessa clasificação aplicamos um peso para calcular a pontuação total de violência de cada vitíma:

Violência Leve: Chute, Empurrão, Puxão de cabelo, Soco, Tapa.

Violência Média: Afogamento, Enforcamento, Estrangulamento, Sufocamento.

Violência Pesada: Facada, Paulada, Queimadura, Tiro.

Pontuação Total de Violência: Soma ponderada (leve=1, média=2, pesada=3).

## 🔍 Tratamento de Dados Ausentes
Visto a presença de alguns dados ausentes, fiz uma análise de distribuição de cada uma das colunas e análisei a porcentagem de valores ausentes em cada coluna, chegando a conclusão que a melhor alternativa seria preencher os valores ausentes com a moda de cada coluna, visto que os valores ausentes eram muito poucos e esse método não adicionaria tanto viés a análise.

Valores faltantes foram substituídos pela moda (valor mais frequente) de cada coluna.

## ✂️ Remoção de Redundâncias
Algumas colunas foram removidas devido a não trazerem informações novas:

Exemplo: "Não tenho filhos" (já representado em outras colunas).

# 🔍 2. Análise Inicial dos Dados (Etapa 3)
Nessa etapa, realizei uma análise mais explorátoria dos dados, buscando relações e insights escondidos entre as características do dataset. Para isso observer a distribuição de violência em cada etnia, a presença de caractéristicas como uso de drogas ou álcool nas ocorrências policiais, entre outras análises, o que levou a algumas descobertas:
Principais Descobertas
## 📊 Distribuição das Vítimas por Etnia

Pardas: Maioria das vítimas (≈60%).

Brancas e Pretas: Segunda maior ocorrência.

Indígenas e Amarelas/Orientais: Menos representadas (possível subnotificação).

## ⚖️ Níveis de Violência

Violência leve: Mais frequente.

Violência grave: Menos comum, mas muito mais presente principalmente em vítimas pardas e pretas.

## 🚨 Ocorrências Policiais

Baixo registro: A maioria das vítimas não registra ocorrência, mesmo em casos graves.

Agressores que usam drogas/álcool: Maior probabilidade de registro policial.

## 📊 Outros Insights

Violência por Etnia: Pardas sofrem mais violência em todos os níveis.

Relação entre Separação Recente e Violência: Mulheres que tentam se separar sofrem mais agressões.

Impacto do Uso de Álcool/Drogas: Agressores sob efeito de substâncias cometem mais violência grave.

# 🤖 3. Modelagem Preditiva e Clusterização
Após essa análise, apliquei o dataset em 2 modelos de aprendizagem de máquina supervisionada com o intuito de, com base nas características da situação da vítima perante o agressor, prever qual seria o nível de violência sofrido por ela. Para isso utilizei primeiramente o XGBoost e em seguida o Random Forest Regressor.

## 📌 Modelo 1: Regressão (XGBoost)
Resultados:
✅ R² = 82% (explica 82% da variação nos dados).
✅ MAE = 0.85 (erro médio baixo).

O XGBoost foi relativamente bem, conseguindo um R2 de 82%.
## 📌 Modelo 2: Random Forest
Houve uma melhoria em relação à regressão:
✅ R² = 85% (melhor ajuste).
✅ MAE = 0.78 (menor erro).

## 📌 Modelo 3: K-Means (Perfis de Agressores)
Como terceiro modelo, usei o K-means, dessa vez com um novo objetivo, tentar descobrir perfis de agressão entre os agressores com base no nosso dataset. O K-means trouxe um resultado interessante utilizando 3 clusters, o que fora calculado com o método do cotovelo, chegando em 3 perfis principais de agressores:

Controlador e Ciumento
-Alta taxa de controle, ciúmes e agressões recentes.

Agressor sob Efeito de Substâncias
-Uso de álcool/drogas associado a violência.

Agressor Possessivo
-Prisão domiciliar, bloqueio financeiro e vigilância constante.

Índice Davies-Bouldin = 1.2 (clusters razoavelmente bem separados).
# 📌 Conclusões e Recomendações
Principais Achados

🔹 Perfil das Vítimas: Mulheres pardas são as mais afetadas.
🔹 Subnotificação: Poucas vítimas registram ocorrências policiais.
🔹 Perfil dos Agressores: uso de substâncias aumenta gravidade da violência e comportamentos controladores são frequentes.


# 🤖 Próximos Passos:

Coletar mais dados de grupos sub-representados (indígenas, amarelas).

Testar outros modelos (ex.: Redes Neurais).
