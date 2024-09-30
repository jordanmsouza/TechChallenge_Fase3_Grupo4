# Fine-Tuning de Modelos de Linguagem para Geração de Descrições de Produtos

Este repositório contém um script para realizar o **fine-tuning** (ajuste fino) de **modelos de linguagem pré-treinados** (LLMs - *Large Language Models*) de código aberto, com o objetivo de gerar descrições estilizadas de produtos a partir de seus títulos. O script utiliza a biblioteca `unsloth` para carregar modelos de linguagem grandes e eficientes em memória, como o **Mistral 7B** quantizado em 4 bits, e o framework `trl` (Transformers Reinforcement Learning) para realizar o fine-tuning com a técnica **LoRA** (*Low-Rank Adaptation*).

## Objetivo

O objetivo deste projeto é demonstrar como ajustar um modelo de linguagem pré-treinado para uma tarefa específica de geração de texto, utilizando um conjunto de dados de produtos com seus títulos e descrições. Com isso, busca-se melhorar a capacidade do modelo de gerar descrições detalhadas e estilizadas a partir de um título fornecido.

## Funcionalidades

* **Fine-tuning de um modelo LLM** (Mistral 7B quantizado em 4 bits) utilizando a biblioteca `unsloth` e o método LoRA.
* **Formatação de um dataset** de produtos para treinamento, extraindo títulos e descrições.
* **Treinamento do modelo** com o dataset formatado utilizando o framework `trl`.
* **Inferência com o modelo ajustado** para gerar descrições de produtos a partir de títulos fornecidos.

## Dependências

* **Python 3.8** ou superior.
* **Google Colab** (recomendado para execução).
* **Bibliotecas Python**:
    * `unsloth`: Biblioteca para manipulação de modelos de linguagem grandes e eficientes em memória.
    * `trl`: Framework para treinamento de modelos com reforço (*Transformers Reinforcement Learning*).
    * `transformers`: Biblioteca para modelos de linguagem pré-treinados.
    * `datasets`: Biblioteca para manipulação de conjuntos de dados.
    * `torch`: Biblioteca para computação numérica e aprendizado de máquina.
    * `accelerate`: Biblioteca para aceleração de treinamento em múltiplos dispositivos.
    * `bitsandbytes`: Biblioteca para quantização de modelos em 8 bits e 4 bits.
    * `xformers`: Biblioteca para otimizações de eficiência de memória em transformers.

## Instruções

1. **Clonar o repositório:**

   ```bash
   git clone https://github.com/jordanmsouza/TechChallenge_Fase3_Grupo4.git
2. **Preparar o dataset:**

* Certifique-se de ter um arquivo JSON contendo dados de produtos com os campos `"title"` e `"content"`, onde `"title"` é o título do produto e `"content"` é a descrição.  
* Coloque o arquivo JSON na pasta `/content/drive/MyDrive/trn.json/` dentro do seu Google Drive, que será montado no Google Colab.

3. **Executar o script:**

* Abra o notebook `TechChallenge_Fase3_Grupo4.ipynb` no Google Colab.
* Execute as células do notebook em ordem, seguindo as instruções fornecidas.

4. **Ajustar o modelo:**

* O script carrega o modelo pré-treinado, formata o dataset e realiza o fine-tuning utilizando a técnica **LoRA**.  
* O fine-tuning é configurado com parâmetros otimizados, como número de passos de treinamento, taxa de aprendizado e parâmetros do LoRA, visando melhorar a performance do modelo.

5. **Testar o modelo ajustado:**

* Após o fine-tuning, o script testa o modelo com um exemplo de título e exibe a descrição gerada.  
* Você pode fornecer títulos personalizados para gerar novas descrições.

## Detalhes Técnicos

### Fine-Tuning com LoRA
**LoRA** (*Low-Rank Adaptation*) é uma técnica que permite ajustar modelos de linguagem grandes de forma eficiente, adicionando matrizes de baixo rank (menor complexidade) às camadas do modelo, reduzindo o número de parâmetros a serem treinados. Isso é especialmente útil para modelos grandes, tornando o treinamento mais rápido e economizando memória.

### Quantização em 4 Bits
Para tornar possível o treinamento e a inferência de modelos grandes em ambientes com recursos limitados (como o Google Colab), utilizou-se a **quantização em 4 bits**. A quantização reduz a precisão dos pesos do modelo, diminuindo o consumo de memória e permitindo que modelos maiores sejam carregados na GPU disponível.

### Modelos Utilizados
Optou-se por utilizar o modelo **"unsloth/mistral-7b-v0.3-bnb-4bit"**, que é uma versão otimizada e quantizada em 4 bits do modelo Mistral 7B, fornecendo um bom equilíbrio entre capacidade e eficiência.

## Resultados

Realizaram-se testes de geração das descrições dos produtos **antes** e **depois** do fine-tuning:

### Antes do Fine-Tuning
Antes do ajuste fino, o modelo gera descrições genéricas e com poucos detalhes, não capturando bem as especificidades dos produtos.

**Exemplo:**

![image](https://github.com/user-attachments/assets/de98cd3a-c1ac-4cca-b689-3118424386c3)
![image](https://github.com/user-attachments/assets/794dba0c-b88e-4379-a1d7-625e9b58f65e)


### Depois do Fine-Tuning
Após o fine-tuning, o modelo é capaz de gerar descrições mais detalhadas e estilizadas, refletindo melhor as características dos produtos.

**Exemplo:**

![image](https://github.com/user-attachments/assets/d085c2e7-728c-4c92-a721-f82f82f0cc01)
![image](https://github.com/user-attachments/assets/590e6507-f6ab-4aa2-9933-0cf342b756bd)


O modelo treinado é salvo na pasta `/content/drive/MyDrive/trn.json/lora_model/` do Google Drive, podendo ser reutilizado para gerar descrições de produtos futuros a partir de seus títulos.

## Contribuições
Contribuições são bem-vindas! Se você encontrar algum problema ou tiver sugestões de melhoria, por favor, abra uma issue ou envie um pull request.
