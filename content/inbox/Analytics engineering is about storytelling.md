# Analytics engineering is about storytelling
Greetings, I'm Winladriel, my cousin Winnie asked me to come here today to talk to you about something we both have a passion for, which is analytics engineering. Now you may not realize that analytics engineering is popular among the elf populations of middle earth, but i think by the end of this talk you'll understand why. You see elves, being immortal, value stories and song above all the other riches of the earth. And what we're here to absorb today is that analytics engineering is about stories.

To understand what this has to do with data though we need to understand why we look at data in the first place?

# What are stories?
Humans can't read data. This is why data literacy is a term, there is nothing natively, intuitively consumable about data to the human mind. What we can understand is:
1. The relationship between data points and entities.
2. The relationships between similar entities in a group.
3. The relationships between different groupings of entities.
4. The changing relationships of all of the above over time.
If we replace entities here with characters we have *story*

# Stories are patterns
Now this is all great for an elf, we're immortal beings who live immersed in natural splendor, beauty, and all that is fair. But mortal life can be a battle, we must conduct business and survive. The secret I'm here to share though is that, the same artistry used to write an ode to my ancestors Beren and Luthien, can be extrapolated out to a process that works just as well for understanding customers purchasing jewels and armor on your mortal internet.

This is because stories are also patterns. If we recall why we look at data, we see that understanding the threads of patterns that form the fabric of our stories is what weaves these possibilities.

The internal rhythms of stories within themselves that create the texture of patterns, and moreover, the relationships between stories, in whole or in part, and with the stories of our own lives, add layers of meta patterns. For example, one of the most well known of your world is Joseph Campbell's Hero's Journey. It looks like this, various steps are taken, obstacles are overcome to reach some kind of new, more desirable state.

It also happens, this is the very same story, perhaps a little more relatable to your day-to-day.

To take this meta-patterning further and explore just how fundamental storytelling is to analytics engineering, we're going to walk through telling one of the most famous tales of my world, that of Frodo and the Ring of Power. 

To do so, we'll use a tool we developed with the dwarf lords for recording scrolls of their merchants' dealings in selling precious goods to the kingdoms of men. We call it dwarves buried treasure.

# An example: overview of the data
* Elders, to save themselves paper and time writing, used shorthand to reference things in other tables 
* Creating relationships and entities - with the magic we have at our disposal now, this is no longer necessary so let's get all of our characters into one table
* Unioning and denormalizing - the rangers keep different logs than the hobbits (number of breakfasts)
* Weapons - need to create a history over time, thankfully the elders did this with a snapshot, current weapon, weapon history model
* After modeling we have:
	* Characters
* Events - append-only log - i did a similar process to bring together logs from Lothlorien, those of Rohan, lost scrolls from Saruman, the list goes on.
* Events applied to relationships and entities create stories
* Making a more readable events view - denormalizing
* After modeling we have:
	* Events
	* Characters -- both tell complete stories
* We can create views on top of these complete stories to look at specific aspects:
	* Orcs slain chart
	* Fellowship Story chart - Sankey i think, ideally

Here are 3 principles for thinking like the storyteller you are:
1. Put away the broom, pick up the pen -- language and naming is a foundational part of analytics engineering. Let's apply the same care to naming our work. (tweet about cleaning data) - it's not cleaning, it's setting the stage. we're not limited to fixing inconsistencies, we can apply any single table transformations we want in the staging layer to craft the characters, places, and events we need.
2. Think in characters, places, and events. Our marts layers is designed to contain stories. Fact and dimension are less useful concepts in these days of denormalization than stories. Make the customers table the story of the customers, no matter if you have to aggregate and denormalize facts on to it or fan out history to do so. Make the orders table tell the whole story of each order, even if you need to denormalize much of the user table onto it. 
3. Let stories guide and unify your work. In a world of nearly limitless possibilities, where analytics engineers have ever increasing powers, we have to be disciplined as custodians of our organization's stories. It's our responsibility to ensure that people are creating, developing, sharing, and understanding within the same world. It's better to go the harder route of getting three departments working together inside of the same rich, challenging, complex story than to craft three separate narratives or focus solely on letting people write their own. That's undoubtedly still a battle at most orgs, but that, as this first, genre-creating, paradigm-shifting generation of data storytellers and information authors is your story write.