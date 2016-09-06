# News API

## Request protocol

The above JSON protocol shows the parameters available to search for news in Knewin.io API.

```
{
	"key" : STRING,
	"query" : STRING[1K],
  	"defaultOperator": STRING [OR, AND],
	"offset" : INTEGER,
	"filter" : {
		"sourceId" : INTEGER [1..n],
		"language" : [ 
			"pt", "en", "es", "fr", "de", "bg", "cs", "el", "et", 
			"fi", "hu", "it", "ja", "ko", "lt", "nl", "pl", "ro", 
			"ru", "sk", "sl", "so", "sv", "uk"
		],
		"sincePublished" : DATE,
		"untilPublished" : DATE,
		"sinceCrawled" : DATE,
		"untilCrawled" : DATE
	},
	"newsId" : INTEGER [1..10],
	"fields" : STRING ["url", "id", "title", "subtitle", "author", "content", 
			"source_id", "source", "crawled_date", "published_date", 
			"lang", "images", "hat", "category", "locality", "page"],
	"gmt" : STRING (ex.: "-3", "-0200", "+01:00", "0600"),
	"sort" : {
		"field": STRING ("published_date", "crawled_date", "frequency"),
		"order": STRING ("asc", "desc")
	}
}
```

*where:*

`key`: chave de autorização do cliente.

`query`: palavras que representam uma consulta (operadores AND, OR e NOT - default OR).

`defaultOperator`: possibilita definir o operador padrão a ser usado em uma consulta, com valores possíveis OR ou AND (default OR).

`offset`: posição inicial da lista de notícias recuperadas - descarta as notícias anteriores; a primeira notícia está na posição 0 (zero).

`filter`: parâmetros a serem usados para restringir a busca de notícias.

`sourceId`: lista de identificadores de fontes - máximo de 100 identificadores.

`language`: lista de linguagens para restringir a consulta.
	
`category`: filtrar por uma categoria da notícia.

`locality`: filtrar por uma localidade da notícia.

`page`: filtrar por uma página.

`sincePublished`: data1 inicial de publicação da notícia.

`untilPublished`: data1 final da publicação da notícia.

`sinceCrawled`: data1 inicial da coleta da notícia.

`untilCrawled`: data1 final da coleta da notícia.

`fields`: lista de campos a serem retornados a partir de uma consulta.

`gmt`: indica qual GMT deverá ser utilizado.

`sort`:
	`field`: indica o campo a ser utilizado para ordenar as notícias recuperadas ("published_date", "crawled_date", "frequency").
	
order: informa se a ordenação deverá ser ascendente (asc), do mais antigo para o mais novo, ou descendente (desc), do mais novo para o mais antigo.


1 O formato da data segue o padrão definido pelo W3C mas sem o time zone (eg.,  1997-07-16T19:20:30)


## Response protocol
