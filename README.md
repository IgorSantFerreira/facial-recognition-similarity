# Reconhecimento facial por similaridade de cossenos

**Python · DeepFace · FaceNet512 · NumPy · OpenCV**

Protótipo acadêmico de visão computacional desenvolvido na FIAP. A proposta é reconhecer uma pessoa a partir de uma foto de teste, comparando sua representação facial com fotografias de referência.

## Como funciona

Usei **cinco identidades**, com **quatro fotografias de referência e uma de teste por pessoa** (25 imagens no experimento).

O processo é simples:

1. Detectar a região do rosto na imagem.
2. Utilizar o **FaceNet512 pré-treinado** para extrair um *embedding* facial.
3. Calcular a **similaridade de cossenos** entre o teste e as quatro referências de cada identidade.
4. Selecionar a pessoa com a **maior similaridade média**.

**Decisão técnica:** utilizei um modelo pré-treinado e comparação de embeddings, em vez de treinar uma rede neural do zero com uma base pequena. O notebook implementa a comparação e a avaliação em Python.

## Resultados

O experimento registrou **5 acertos em 5 fotografias de teste (100% na amostra avaliada)**.

Os resultados numéricos estão em [`resultados/`](./resultados/), incluindo a matriz de similaridades. Uma das identidades apresentou similaridade relativamente baixa, mesmo tendo sido classificada corretamente.

**Importante:** 100% em cinco testes não representa desempenho esperado em produção nem comprova segurança biométrica.

## Como executar

1. Abra [`Reconhecimento_Facial_FIAP.ipynb`](./Reconhecimento_Facial_FIAP.ipynb) no VS Code ou Jupyter.
2. Execute a célula de instalação das dependências. Na primeira execução, o DeepFace pode precisar baixar os pesos do modelo.
3. Crie a pasta `fotos/` ao lado do notebook, seguindo esta estrutura para **cinco pessoas**:

```text
fotos/
├── pessoa_01/
│   ├── treino/  # 4 imagens
│   └── teste/   # 1 imagem
├── pessoa_02/
├── pessoa_03/
├── pessoa_04/
└── pessoa_05/
```

4. Execute as demais células para gerar a classificação e os arquivos em `resultados/`.

**As fotografias não estão neste repositório por privacidade.** Para reproduzir o experimento, é necessário fornecer imagens próprias ou de uso autorizado.

## Limitações

A amostra é pequena e contém apenas identidades conhecidas. O protótipo não define limiar de rejeição, não testa pessoas desconhecidas e não possui prova de vida contra fotos ou vídeos. A seleção de uma região facial quando há múltiplas detecções também é uma heurística do experimento, não uma regra segura para uso real.

**Autor:** Igor Santana Ferreira · [igor.sant.ferreira@gmail.com](mailto:igor.sant.ferreira@gmail.com)
