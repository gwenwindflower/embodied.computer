## Books that I'm currently reading
```dataview
TABLE
	title,
	rating,
	author,
	status
FROM "reading/books"
WHERE status = "Currently reading"
SORT rating DESC
```
