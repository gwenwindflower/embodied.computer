## Books that I'm paused on
```dataview
TABLE 
	title as "Title",
	genre_1 as "Genre 1",
	rating AS "Rating"
FROM "reading/books"
WHERE status = "Paused"
SORT rating DESC
```
