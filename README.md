## Meu Primeiro Sistema de Recomendação de Filmes 🎬

Este projeto foi criado para demonstrar como podemos desenvolver um sistema de recomendação de filmes utilizando correlação e similaridade de conteúdo. O sistema usa Python e algumas bibliotecas de machine learning para calcular a similaridade entre filmes com base em suas descrições e gêneros.

Para visualizar o Dataset no Kaggle, [Clique aqui](https://www.kaggle.com/datasets/ahsanaseer/top-rated-tmdb-movies-10k?fbclid=IwAR2MpWrWpcw2QNCv_FZg2l0sjBh9xAvhrqtnZBO9K-QS6PHI1aHkdB6qLa0).

Funcionamento
Este sistema de recomendação é baseado em conteúdo. Ele calcula a similaridade de cada filme no dataset com um filme selecionado e retorna os mais semelhantes. A similaridade é calculada usando a similaridade de cosseno.

Exemplo de Uso
Para executar o sistema de recomendação, execute o código abaixo:

```
import pandas as pd
```
```
import pickle
```

# Carregar dados e matriz de similaridade

```
movies_df = pd.read_pickle('movies_list.pkl')
```
```
similarity_matrix = pickle.load(open('similarity.pkl', 'rb'))
```


# Função de recomendação
```
def recomendar_filme(titulo, top_n=5):
    try:
        idx = movies_df[movies_df['title'] == titulo].index[0]
        scores = list(enumerate(similarity_matrix[idx]))
        scores = sorted(scores, key=lambda x: x[1], reverse=True)
        top_filmes = [movies_df.iloc[i[0]]['title'] for i in scores[1:top_n+1]]
        return top_filmes
    except IndexError:
        return "Filme não encontrado!"
```
        
Exemplo de recomendação
print(recomendar_filme("O Poderoso Chefão"))

# Estrutura do Projeto

- movies_list.pkl - Arquivo com a lista de filmes e informações.

- similarity.pkl - Matriz de similaridade calculada entre os filmes.

- recomendar_filme.py - Script principal com a lógica de recomendação.

- README.md - Este arquivo, com instruções sobre o projeto.

- Este README serve como guia básico para entendimento e uso do sistema de recomendação.

