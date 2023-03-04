# Patternary Operators pt 1: The Next Generation

Stories and time are inextricably linked. Without time stories cannot unfold. Without stories time is unmarked and imperceptible. 

Often, in the passing of time, we experience some stories multiple times. We see something we've seen before, form a story about it, and predict that story will happen again. When it does, the story and prediction are reinforced, and if this loop continues long enough we perceive a *pattern*.

I'm not telling you this because I put too many functional mushroom extracts in my tea this morning. I'm telling you this because *stories and patterns are the vital elements of analytics engineering*. Not cloud warehouses or statistics, not even dbt. No, stories and patterns are the most important things, because they are how human beings actually use data to make decisions. The power of dbt stems mainly from the unprecedented new storytelling abilities it infuses into people working with data, like a bite from a radioactive SQL query.

Now, stories as the true output of data is not a particularly new idea, but luckily, that is not in fact what we're here to talk about today. What we're going to discuss is the more mysterious observation that, if we look closely, there exist stories and patterns *within* the very framework we're using to create our stories. Not only that, if we look at several of these frameworks, for example a set of 5 dbt projects, we'll see higher level patterns emerging _across_ their individual internal stories. These meta-stories are often referred to as *design patterns* in more established fields like software engineering, and it's time we started talking about them more deeply in analytics engineering.

Rather than load you up with more theory at this point, we're going to explore several of these design patterns hands on through the rest of this series. As we apply them to various industries and use cases, the goal is that you'll begin to develop a sensitivity for perceiving them in many contexts, and an intuition for applying them to help tell the stories you want to tell with your data. This is truly the heart of analytics engineering as a craft.

To start with, we're going to look at a pattern I call a 'cohort generator'. We'll discuss what this looks like in the abstract later, but let's start with an example.

I have a table of orders and users in my ecommerce platform [Jaffle Shop?]. Users is a slowly changing dimension, orders an append-only fact. Classic. Simple. Beautiful. What could be better? 

[Preview data]

Well, it turns out marketing wants to understand how many users are buying at least one jaffle per month (JPMs at the corporate office, a crucial Jaffle Shop metric). They'd also like to know which users are not buying a jaffle per month. In fact, it would be helpful to segment out which users have purchased their first jaffle and when as well, and which users were buying a jaffle every month and then stopped. Oh, and if we could identify which users were buying a jaffle per month, stopped, then started again, that'd be great.

What patterns can you identify in the above requests already? This is a good place to start. Depending on your data modeling experiences you may notice that a lot of what we're looking to do is group and label users based on actions they've taken over time. You may also notice that we seem to be moving towards some labels like new jaffle eaters, active jaffle eaters, and churned jaffle eaters -- concepts you'd usually find in subscription-like businesses.

Unfortunately, these concepts don't exist in our data as-is. The  Jaffle Shop has yet to becoming a streaming subscription service. Thankfully though, we have dbt, so we're going to craft these groups for ourselves, and this where the cohort generator pattern comes into play.

A cohort generator, at its most basic, takes a type of entity (a person, a store location, a particular vehicle, a website) and a list of events (jaffles eaten, mattresses sold, deliveries made, pageviews) then, based on flexible business logic you design with your stakeholders, groups them into cohorts and outputs the history of their cohort membership over time.

Before we dive into coding this in dbt, it's always a good idea to map out our desired output in a spreadsheet and work backwards. Not only does this help us clarify our own thinking, it gives us a chance to align with our stakeholders on the end product, saving us potential surprises, rework, and muttering curses under our breath down the road. 

We think we want something that looks like this [example output table]

Some features to note about this: we have one or more rows for every user who has bought at least one jaffle and each row has a `valid_from` and `valid_to` timespan bounding the time this user was in the specified group. These timespans are contiguous for each user from their first jaffle order to the present, the current status being indicated by a NULL `valid_to`. This type of history is often called **mutually exclusive and completely exhaustive** or MECE (mee-cee).

So now that we know what we want to build, how do we do it?
[Code examples walking through doing this]

What's amazing about the table that emerges from this is that *we* designed this. Often cohort analysis uses simple groupings like new users based on signups, but our cohort generator gives us much richer, more flexible options that we created based on what *we* wanted to see in our data. 

Want to look at marketing spend against lapsed jafflers from Q1 vs. Q2, no problem, because we've already used dbt to abstract out that complex grouping logic. Want to change the window of our 'active' jafflers to 3 months instead of 1? Just edit one variable.

