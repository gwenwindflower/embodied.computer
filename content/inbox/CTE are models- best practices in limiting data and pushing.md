# CTEs in the fractal DAG: best practices in limiting data and pushing transformations upstream to optimize performance

fractal-like 
Seminal article CTEs are passthroughs [link] - some interpreted this, understandably, as throw whatever you want at the query optimizer and it will be fine.

In real world scenarios, more nuanced.

Overarching idea, limit the data output as far upstream as possible always:
	- columns selected
	- ranges selected (time ranges most common)
Treat every CTE as a small scale component model. CTEs are the model components that chained together make up models, models are the larger components that, chained together make up data transformations. Like atoms, molecules, and proteins. Certain governing principles apply across the different scales.

Original guidance stands, but we want to elaborate on when and where these principles are most important.

Particularly, joins and column selection.

Benchmarks from original article, benchmarks reflecting "rebuttal" article, benchmarks reflecting "real world" data.

All 3 should reflect single table, column subset selections in single table, and joins.