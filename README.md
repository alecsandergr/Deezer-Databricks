# Deezer API

Esse projeto está sendo desenvolvido com o objetivo de aprendizado sobre a plataforma Databricks. Uma pipeline com a extração, carragemento e transformação será desenvolvida ao decorrer do projeto.

## Sumário

- [src](/src/)
- [databases](/databases/)
- [get_token](/get_token/)
- [Deezer API](#deezer-api)
- [Resumo](#resumo)
- [Aprendizados](#aprendizados)

## Resumo

Esse projeto foi baseado nos vídeos do Datasus do canal [Téo Me Why](https://www.twitch.tv/teomewhy). Contudo, a versão do Databricks utilizada por ele é a paga, assim, foram necessárias algumas mudanças para a adequação do projeto e não foi estabelecida uma maneira alternativa de automação. 

Uma outra API foi utilizada para a construção do projeto pessoal, a do Deezer. O objetivo foi a extração do histórico de músicas ouvidas e um ranking das músicas mais escutadas.

<img src="https://i.ibb.co/0cxvM3S/deezer-pipeline.png" alt="deezerpipeline" width=400>

## Estrutura do projeto

Para consultar os dados seguimos o padrão: `{database}.{tabela}`.

Assim, temos 1 database:

Bronze: Dados brutos a partir das fontes em formato Delta
<!-- Silver: Dados padronizados de forma mais fácil de leitura e utilização
Gold: Dados agregados em formato de relatórios para serem utilizados em ferramentas de visualização -->

Você pode consumir os dados da seguinte maneira com SQL:

```sql
SELECT *
FROM bronze.deezer_history
```

## Aprendizados

O foco foi entender o que é oferecido pelo Databricks e construir uma pipeline que funcionasse em uma versão paga com o mínimo de alterações possíveis, mas que ainda funciona na versão Community.

Uma das vantagens ao usar o Databricks é a possibilidade de construir toda a pipeline em um mesmo ambiente, fora a facilidade de se trabalhar com o Spark.

Além disso, também foram utilizadas classes para uma maior facilidade na manutenção do código e para que ele possa ser reutilizado em outros projetos.

## Criação das credenciais

Você pode seguir criar um APP em [deezer_developers](https://developers.deezer.com) com as seguintes configurações:

```
Application domain: http://www.example.com
Redirect URL after authentication: http://127.0.0.1:5000/deezer/login
Link to your Terms of Use: http://www.example.com
```

Depois basta criar um arquivo JSON que satisfaça o [código](/get_token/get_access_token.ipynb) de geração do token.