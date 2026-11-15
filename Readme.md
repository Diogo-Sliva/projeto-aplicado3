Sistema de Recomendação Personalizada de Filmes Utilizando Filtragem Colaborativa

Projeto desenvolvido na disciplina Projeto Aplicado III – Banco de Dados (2026.2) do curso de Tecnologia em Banco de Dados da Universidade Presbiteriana Mackenzie.

Integrantes (Grupo Projeto 17)

Daniel Silva Souza Filho — RA: 10737593

Diogo Ferreira da Silva — RA: 10737944

Links de Entrega e Demonstração

Notebook no Google Colab: Acessar Projeto_Aplicado_III_Etapa_4.ipynb

Sobre o Projeto e Alinhamento com os ODS (ONU)

Este projeto implementa e avalia um sistema de recomendação personalizada de filmes utilizando a base pública MovieLens Latest Small (README da base), disponibilizada pelo GroupLens Research da University of Minnesota (100.836 avaliações, 610 usuários e 9.742 filmes cadastrados).

A proposta vincula-se ao Objetivo de Desenvolvimento Sustentável 4 (Educação de Qualidade) da Agenda 2030 da ONU, especificamente à Meta 4.7, ao empregar algoritmos de filtragem colaborativa como mecanismos de curadoria e descoberta de conteúdos culturais alinhados aos interesses dos usuários.

Pipeline e Modelos Implementados

Análise Exploratória e Preparação: Verificação de integridade dos arquivos ratings.csv e movies.csv (sem valores nulos ou duplicados) e divisão em treino (80% — 80.668 avaliações) e teste (20% — 20.168 avaliações) com random_state=42. Filmes com nota $\ge 4,0$ são definidos como relevantes.

Baseline de Popularidade: Recomenda os 10 filmes com maior volume de avaliações no conjunto de treinamento ainda não assistidos pelo usuário-alvo.

Filtragem Colaborativa Baseada em Usuários (Inicial): Constrói a matriz usuário-item ($610 \times 8.983$), calcula a similaridade do cosseno entre usuários, seleciona os $K=50$ vizinhos mais próximos e estima a nota pela média ponderada para filmes avaliados por ao menos 3 vizinhos.

Filtragem Colaborativa Ajustada (Com Regularização): Aplica amortecimento bayesiano sobre a média ponderada para evitar que filmes avaliados por poucos vizinhos recebam pontuações artificialmente infladas:


$$\text{Score} = \frac{n \cdot \text{previsão} + 10 \cdot 3,5}{n + 10}$$

Síntese dos Resultados Alcançados (Top-10)

Modelo Avaliado

Precision@10

Recall@10

NDCG@10

Variação NDCG@10 vs. Baseline

Baseline de Popularidade

0,1215

0,1026

0,1579

Referência (0,00%)

Filtragem Colaborativa (Inicial)

0,0230

0,0308

0,0273

-82,71%

Filtragem Colaborativa Ajustada (Regularizada)

0,1486

0,1413

0,2050

+29,83%

Como Executar Localmente

Clone este repositório e instale as dependências (pandas, numpy, matplotlib, scikit-learn).

Execute o notebook Projeto_Aplicado_III_Etapa_4.ipynb no Jupyter Lab ou diretamente no Google Colab (o script realiza o download automático da base MovieLens Latest Small).

Referências Principais

ALFAIFI, Yousef H. Recommender Systems Applications: Data Sources, Features, and Challenges. Information, v. 15, n. 10, art. 660, 2024.

ALJUNID, Mohammed Fadhel et al. A collaborative filtering recommender systems: Survey. Neurocomputing, v. 617, art. 128718, 2025.

GOOGLE INC. Recommendation Systems – Machine Learning, 2023.

GROUPLENS RESEARCH. MovieLens Datasets, University of Minnesota.

McAULEY, J. Recommender Systems and Personalization Datasets, 2023.

NAÇÕES UNIDAS. Objetivos de Desenvolvimento Sustentável (ODS).