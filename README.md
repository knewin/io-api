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
		"sincePublished" : DATE1,
		"untilPublished" : DATE1,
		"sinceCrawled" : DATE1,
		"untilCrawled" : DATE1
	},
	"newsId" : INTEGER [1..10],
	"fields" : STRING ["url", "id", "title", "subtitle", "author", "content", 
			"source_id", "source", "crawled_date", "published_date", 
			"lang", "images", "hat", "category", "locality", "page"],
	"gmt" : STRING (ex.: "-3", "-0200", "+01:00", "0600"),
	"groupSimilar" : BOOLEAN,
	"sort" : {
		"field": STRING ("published_date", "crawled_date", "frequency"),
		"order": STRING ("asc", "desc")
	}
}
```

## Response protocol
