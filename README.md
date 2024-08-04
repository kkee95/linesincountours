# Projeto de Pesquisa: Mapeamento de Imagens de Grãos Intermetálicos da Liga de Alumínio 355

## Descrição

Este projeto de pesquisa teve como objetivo mapear e analisar imagens de grãos intermetálicos da liga de alumínio 355 utilizando microscopia. A partir das imagens coletadas, extraímos informações detalhadas sobre as áreas dos grãos, resultando em um dataframe com as áreas médias dos grãos. Utilizamos esses dados para criar um modelo de aprendizado de máquina (machine learning) que pode prever características dos materiais com base nas áreas dos grãos.

## Estrutura do Projeto

- **images/**: Diretório contendo as imagens microscópicas dos grãos intermetálicos.
- **data/**: Diretório contendo os dados extraídos, incluindo o dataframe com as áreas dos grãos.
- **notebooks/**: Jupyter notebooks utilizados para análise e criação do modelo de aprendizado de máquina.
- **src/**: Código-fonte do projeto, incluindo scripts para processamento de imagem e treinamento do modelo.
- **README.md**: Este arquivo de documentação.

## Metodologia

### 1. Coleta de Imagens

As imagens dos grãos intermetálicos foram coletadas usando um microscópio de alta resolução. A liga de alumínio 355 foi preparada adequadamente para obter imagens claras e detalhadas dos grãos.

### 2. Processamento de Imagem

Utilizamos o Fiji (ImageJ) para processar as imagens. Os passos incluíram:
- **Conversão para escala de cinza**: As imagens foram convertidas para 8-bit.
- **Aplicação de threshold**: Um threshold foi aplicado para isolar os grãos.
- **Separação dos grãos**: A ferramenta Watershed foi usada para separar grãos que estavam tocando.
- **Análise de partículas**: Utilizamos a função `Analyze Particles` para medir as áreas dos grãos.

### 3. Extração de Dados

Os dados resultantes do processamento de imagem foram exportados para um dataframe contendo as áreas dos grãos em micrômetros quadrados. Este dataframe foi salvo como um arquivo CSV para análise posterior.

### 4. Análise de Dados e Modelagem

Usamos Python e bibliotecas como pandas e scikit-learn para analisar os dados e criar um modelo de aprendizado de máquina. O objetivo do modelo era prever características dos grãos com base nas áreas médias.

#### Passos para a Análise e Modelagem:

1. **Carregar os dados**:
    ```python
    import pandas as pd

    df = pd.read_csv('data/areas_graos.csv')
    ```

2. **Análise exploratória**:
    ```python
    print(df.describe())
    ```

3. **Criação do modelo de aprendizado de máquina**:
    ```python
    from sklearn.model_selection import train_test_split
    from sklearn.ensemble import RandomForestRegressor

    # Dividir os dados em treino e teste
    X = df[['area_media']]
    y = df['caracteristica_alvo']  # Supondo que temos uma coluna alvo
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

    # Treinar o modelo
    model = RandomForestRegressor()
    model.fit(X_train, y_train)

    # Avaliar o modelo
    score = model.score(X_test, y_test)
    print(f'Score do modelo: {score}')
    ```

## Resultados

Os resultados mostraram que as áreas médias dos grãos podem ser usadas efetivamente para prever características importantes dos materiais. O modelo de aprendizado de máquina desenvolvido apresentou uma boa performance, indicando que as áreas dos grãos são um parâmetro significativo para análise de materiais da liga de alumínio 355.

## Conclusão

Este projeto demonstrou a eficácia do uso de técnicas de processamento de imagem e aprendizado de máquina para analisar e prever características de grãos intermetálicos em ligas metálicas. O uso de microscopia combinado com análise automatizada pode acelerar significativamente a pesquisa e desenvolvimento de novos materiais.

## Como Citar

Se você usar este projeto em sua pesquisa, por favor, cite da seguinte forma:
Santos Keven, 2023. Mapeamento de Grafos como Método Alternativo para Análise Dimensional de Microestruturas. URL do Reposítório


## Contato

Para mais informações, entre em contato com [Keven Santos] - [keven.santos@ufrpe.br].
