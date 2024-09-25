# Fine-Tuning de Modelos de Linguagem para Descrição de Produtos

Este repositório contém um script para fine-tuning de modelos de linguagem de código aberto para gerar descrições estilizadas de produtos a partir de seus títulos. O script utiliza a biblioteca `unsloth` para carregar modelos de linguagem grandes e eficientes em memória, como o Meta-Llama 3.1-70B, e o framework `trl` para realizar o fine-tuning com a técnica LoRA (Low-Rank Adaptation).

## Objetivo

O objetivo deste projeto é demonstrar como ajustar um modelo de linguagem pré-treinado para uma tarefa específica de geração de texto, utilizando um conjunto de dados de produtos e seus títulos e descrições.

## Funcionalidades:

* Fine-tuning de um modelo LLM (Meta-Llama-3.1-70B) utilizando o framework Unsloth e o método LoRA.
* Formatação de um dataset de produtos para treinamento, extraindo títulos e descrições.
* Treinamento do modelo com o dataset formatado utilizando o framework trl.
* Inferência com o modelo fine-tuned para gerar descrições de produtos a partir de títulos.

## Dependências

* Python 3.8 ou superior
* Google Colab (recomendado)
* Bibliotecas Python:
    * `unsloth`
    * `trl`
    * `transformers`
    * `datasets`
    * `torch`
    * `accelerate`
    * `bitsandbytes`
    * `xformers`

## Instruções

1. **Clonar o repositório:**

```bash
git clone https://github.com/seu-usuario/fine-tuning-produtos.git
```

2. **Preparar o dataset:**

* Certifique-se de ter um arquivo JSON contendo dados de produtos com os campos "title" e "content".
* Coloque o arquivo JSON na pasta `/content/drive/MyDrive/trn.json/` dentro do seu Google Colab.

3. **Executar o script:**

* Abra o notebook `fine_tuning_produtos.ipynb` no Google Colab.
* Execute as células do notebook em ordem.

4. **Ajustar o modelo:**

* O script irá carregar o modelo pré-treinado, formatar o dataset e realizar o fine-tuning utilizando a técnica LoRA.

5. **Testar o modelo ajustado:**

* Após o fine-tuning, o script irá testar o modelo com um exemplo de título e exibir a descrição gerada.

## Resultados

O modelo ajustado será salvo na pasta `/content/drive/MyDrive/trn.json/lora_model/`. Você pode utilizar este modelo para gerar descrições de produtos a partir de seus títulos.

## Contribuições

Contribuições são bem-vindas! Se você encontrar algum problema ou tiver sugestões de melhoria, por favor, abra uma issue ou envie um pull request.