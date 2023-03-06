Data modeling is the process by which data is transformed into narrative.

Humans are story machines, and we need patterns to form stories. Unlike computers, humans do not have the ability to find patterns in large quantities of raw data.

We need tools and processes by which we can do that, and collectively those tools and processses are called 'data modeling'.

While writing SQL to transform the data (in a ELT or ETL paradigm) is the aspect of data modeling that is typically focused on, it's only one part of the process. Gathering requirements, developing contracts, and building semantic represenations of the objects you transform the data into are crucial parts of the process as well.

Let's focus on building semantic represenations of our transformed objects.

To infuse purpose into our data transformations, we need to craft surfaces for people to interact with and animate the stories within. In practical terms, this looks like connecting models to dashboards, notebooks, and ML in flexible and accurate ways. Metrics, exposures, bringing usage nodes into our concept of the DAG -- these are all methods by which we can build these semantic surfaces for people to explore.

At present, this work is often treated as a post-step to data modeling, when in fact, as [Josh Devlin points out](https://www.linkedin.com/posts/josh-devlin_datamodeling-datamodelling-activity-7038354656720277504-bfjn?utm_source=share&utm_medium=member_desktop), they're crucial and integrated parts of the modeling process. Without these steps, we're writing a book without publishing it.

The good news is, increasingly, dbt provides robust tooling for this part of the modeling process. The semantic layer and data contracts are becoming easier to build directly from within dbt, yielding powerful integrative effects with the transformation work happening on the physical layer.

Our models (in the expansive sense described above), need to be in evolving conversation with those acting on the narratives they generate. If we consider building our static objects via SQL models to be the end of our model lifecycle, we're missing out on some of the most vibrant opportunties for collaboration, impact, and collective sense-making.

The collaborative and collective aspects of the data modeling process are essential. Unlike writing a novel, storytelling in data modeling is [tasked with finding useful narratives that move us towards our goals](https://www.gwenwindflower.com/blog/1). and functions collaboratively. We respond and refine based on how our readers bring these stories into their day-to-day lives. We can emphasize certain locations, write more about certain characters, or correct where we've accidentally deviated from what happened. As the semantic layer expands, this kind of feedback loop will increasingly be implemented in that flexible and actionable layer, making this step of data modeling even more important.

dbt is the best data modeling tool presently available, and it's crucial that it continues to expand its feature set to encompass the entire lifecycle of data modeling in an integrated way. dbt should be a a tool for crafting meaningful narrative through every phase of data modeling from raw data to collaborators acting on the stories that are uncovered.