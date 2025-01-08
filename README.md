# dio
Repositório para tarefas do bootcamp de Azure
# Exercício: Bike Rental Prediction with Azure Machine Learning

Este documento descreve a execução do exercício "Explore Automated Machine Learning in Azure Machine Learning", que consiste em usar o recurso de AutoML no Azure para treinar e avaliar um modelo de aprendizado de máquina. O objetivo do modelo é prever o número de aluguéis de bicicletas em um determinado dia com base em variáveis sazonais e meteorológicas.

---

## Contexto da Atividade

O exercício propõe as seguintes etapas principais:

1. **Criação do workspace no Azure Machine Learning (AML):** Configurar um ambiente para hospedar os recursos necessários.
2. **Treinamento do modelo:** Usar AutoML para experimentar diferentes algoritmos e parâmetros, selecionando o melhor modelo.
3. **Deploy e teste do modelo:** Implantar o modelo treinado em um endpoint de inferência em tempo real e realizar testes.

O exercício deveria durar cerca de 35 minutos para execução completa, mas a atividade foi limitada ao treinamento devido à indisponibilidade da máquina virtual requerida para o deploy.

---

## Etapas Executadas

### 1. Criação do Workspace no Azure Machine Learning

- Acessei o [portal do Azure](https://portal.azure.com) e criei um recurso de AML com as seguintes configurações:
  - **Grupo de recursos:** Criado ou selecionado previamente.
  - **Região:** Leste dos EUA.
  - **Nome único do workspace:** Definido.
  - **Configurações adicionais:** Conta de armazenamento, Key Vault e Application Insights configurados automaticamente.

### 2. Configuração de Permissões

- Adicionei o papel **Azure AI Administrator** no controle de acesso (IAM) para garantir permissões necessárias no workspace.

### 3. Treinamento do Modelo com AutoML

#### Configuração do Job

- Criei um novo job AutoML com as seguintes configurações:
  - **Nome do experimento:** `mslearn-bike-rental`
  - **Tarefa:** Regressão
  - **Dataset:**
    - **Fonte de dados:** Arquivo CSV com dados históricos de aluguel de bicicletas.
    - **Coluna alvo:** `rentals` (número de aluguéis).
  - **Configurações adicionais:**
    - Modelos permitidos: RandomForest e LightGBM.
    - Métrica primária: NormalizedRootMeanSquaredError.
    - Número máximo de iterações: 3.
    - Divisão de validação: 90% treino / 10% validação.
    - Tipo de validação: Train-validation split.

#### Execução do Job

- O AutoML iniciou automaticamente as iterações, avaliando diferentes combinações de parâmetros para os modelos permitidos.

#### Resultados

- O modelo com melhor desempenho utilizou o algoritmo LightGBM, com métrica **NormalizedRootMeanSquaredError** atingindo um valor satisfatório dentro do limite estabelecido no job.
- Métricas e gráficos, como o histograma de resíduos e gráfico `predicted_true`, foram analisados para validar a performance do modelo.

### 4. Deploy do Modelo

- **Status:** Não concluído.
  - **Motivo:** A máquina virtual requisitada para o deploy (Standard_DS3_v2) não estava disponível. Testei outras configurações de máquinas virtuais, mas o deploy não foi bem-sucedido.

---

## Limitações e Observações

1. **Indisponibilidade de recursos:** A execução foi interrompida na etapa de deploy devido à falta de máquinas virtuais apropriadas.
2. **Tempo de execução:** Apesar de algumas restrições, o treinamento foi concluído dentro do tempo estimado.
3. **Próximos passos:** Com acesso a máquinas virtuais compatíveis, será possível realizar o deploy e testar o endpoint.

---

