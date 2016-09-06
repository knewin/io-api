# News API

## Request protocol

The above JSON protocol shows the parameters available to search for news in Knewin.io API.

```
{
	"key" : STRING,
	"query" : STRING[1K],
	"offset" : INTEGER,
  	"defaultOperator": STRING [OR, AND],
	"fields" : STRING ["url", "id", "title", "subtitle", "author", "content", 
			"source_id", "source", "crawled_date", "published_date", 
			"lang", "images", "hat", "category", "locality", "page"],
	"gmt" : STRING (ex.: "-3", "-0200", "+01:00", "0600"),
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
	"sort" : {
		"field": STRING ("published_date", "crawled_date", "frequency"),
		"order": STRING ("asc", "desc")
	}
}
```

*where:*

Field | Description
----- | -----------
`key` | the key authorization
`query` | the boolean query (operators AND, OR e NOT - default OR)
`defaultOperator` | the default boolean operator (OR or AND) - default OR
`offset` | the start position

Filter field | Description
------------ | -----------
`sourceId` | a list of source identifications (max 100)
`language` | a list of languages
`sincePublished` | the since published date
`untilPublished` | the until published date
`sinceCrawled` | the since crawled date
`untilCrawled` | the until crawled date
`fields` | a list of field to be returned
`gmt` | the GMT to be used


Sort field | Description
---------- | -----------
`field` | the field to be used to sort the result set (`published_date`, `crawled_date`, `frequency`)
`order` | the oorder bo be sorted (asc or desc)


*__IMPORTANT__: Date format based on W3C pattern (eg.,  1997-07-16T19:20:30)*


## Response protocol
