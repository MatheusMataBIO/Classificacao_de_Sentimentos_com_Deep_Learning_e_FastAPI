# Classificação de Sentimentos com Deep Learning + FastAPI

Este projeto treina um modelo de Deep Learning para **análise de sentimentos** (positivo ou negativo) com avaliações de texto, e disponibiliza o modelo como uma **API REST** utilizando `FastAPI`, com deploy gratuito via `Google Colab` e `ngrok`.

## 👤 Autor

### Matheus Silva da Mata

## 📌 Objetivo do Projeto

Desenvolver uma solução de Machine Learning completa, com foco em NLP:

- Classificar sentimentos de avaliações textuais
- Utilizar Keras (TensorFlow) + TF-IDF
- Expor modelo como API FastAPI
- Executar de forma gratuita e temporária no Google Colab

## 📊 Dataset

- Dataset com mais de **50.000 avaliações** de produtos
- Classes:
  - `Positivo`: score ≥ 4
  - `Negativo`: score ≤ 2
- Avaliações neutras (score = 3) foram descartadas

## ⚙️ Pipeline

1. Limpeza e padronização de texto
2. Engenharia de features com TF-IDF
3. Treinamento de rede neural (Keras)
4. Exportação de modelo e vetorizador
5. Criação de API com FastAPI
6. Deploy no Colab com ngrok
7. Testes via Swagger ou código

## 🚀 Deploy com FastAPI no Google Colab (via ngrok)

Você pode testar a API gratuitamente no Colab usando `ngrok` para obter uma URL pública.

### 🧪 2. Rodar a API (Google Colab)

#### 📦 Instale as dependências:

```python
!pip install fastapi nest_asyncio pyngrok uvicorn joblib --quiet
!pip install "tensorflow<2.15" --quiet

import nest_asyncio
from pyngrok import ngrok
import uvicorn
from IPython.display import display, HTML

nest_asyncio.apply()

ngrok.set_auth_token("SEU_AUTHTOKEN_AQUI")  # Adicione seu token

public_url = ngrok.connect(8000).public_url
print(f"✅ URL pública da API: {public_url}")
print(f"✅ Swagger: {public_url}/docs")

display(HTML(f'<a href="{public_url}/docs" target="_blank"><strong>🔗 Abrir Swagger UI</strong></a>'))

uvicorn.run(app, host="0.0.0.0", port=8000)

### Teste via Swagger

- Depois que rodar o código acima clique no link gerado e depois visit que irá abrir o swagger de teste 
- Clique na parte onde tem o json com "text" e escreva alguma frase (em inglês) e clique em executar no painel abiaxo irá mostrar a classificação e a probabilidade

Importante antes de testar você tem que criar seu próprio auto token:

# Autenticação com ngrok (obrigatório para gerar URL pública)
# Obtenha seu token gratuito em: https://dashboard.ngrok.com/get-started/setup

ngrok.set_auth_token("SEU_AUTHTOKEN_AQUI")

## Tecnologias usadas 

Python 3

TensorFlow / Keras

Scikit-learn

Joblib

FastAPI

pyngrok

Google Colab


