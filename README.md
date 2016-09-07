# News API

## Request protocol

The above JSON protocol shows the parameters available to search for news in knewin.io API.

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

Field | Required | Description
----- | -------- | -----------
`key` | yes | the key authorization
`query` | yes | a boolean query (max 1024 characters)
`defaultOperator` | no | the default boolean operator (OR or AND) - default OR
`offset` | no | a start position - default 0 (zero)
`gmt` | no |  the GMT to be used - default UTC
`fields` | no | a list of fields - default all fields
`filter` | no | to filter the result set
`sort` | no | to sort the result set - default crawled date, descendent order - from newer to older

Filter field | Required | Description
------------ | -------- | -----------
`sourceId` | no | a list of source identifications (max 100)
`language` | no | a list of languages
`sincePublished` | no | a since published date
`untilPublished` | no | a until published date
`sinceCrawled` | no | a since crawled date
`untilCrawled` | no | a until crawled date


Sort field | Required | Description
---------- | -------- | -----------
`field` | yes | the field to be used to sort the result set (possible values: `published_date`, `crawled_date`, `frequency`)
`order` | yes | the order to be sorted (possible values: `asc` or `desc`)


*__IMPORTANT__: Date format is based on W3C pattern (eg., 1997-07-16T19:20:30)*


## Response protocol

The above response shows the JSON returned from a search in knewin.io API.

```
{
	"num_docs": INTEGER,
	"start":  INTEGER,
	"count": INTEGER,
	"hits": [	
		{
			"url": STRING,
			"id": INTEGER,
			"domain": STRING,
			"title": STRING,
			"subtitle": STRING,
			"author": STRING,
			"content": STRING,
			"source_id": STRING,
			"source": STRING,
			"source_locality": [
				{
					"country": STRING,
					"state": STRING, 
					"city": STRING
				}
			]
			"crawled_date": DATE,
			"published_date": DATE,
			"lang": STRING,
			"image_hits": [
				{
					"url": STRING,
					"caption": STRING,
					"credit": STRING
				}
			],
			"category": STRING,
			"hat": STRING,
			"locality": STRING,
			"page": STRING,
		}
	]
}
```
