
build a table to understand user purchase patterns in terms of churn -- churn is not a fixed concept for a non-subscription service, so this is requires a few steps. we need to analyze customer purchase patterns. we need to determine, among repeat buyers, what the typical purchase cadence is. from there, we can determine what time spans constitute status changes, and what those statuses are. there are quite a few decisions to be made in how we approach that alone. 

from there we actually need to build a new model that brings together users and purchase events into a pseudo-subscription like table that labels them as active, churned, reactivated. This would be a MECE table plotting out each users' status over time.

very doable, and an ideal piece of work for an analytics engineer, but not an insignificant dedication of time.

stakeholders requesting this have thrown around terms like 'increasing LTV', 'increasing purchase velocity', 'increasing active buyers', etc

that all sounds great, and we know how to build it, so let's do it right? here's where we PAUSE. 

while we *do* measure a lot of the things being mentioned, we haven't determined really which of them we're focused on, nor have we determined what the scale of the impact we expect to have on any of them. maybe LTV goes up next quarter and we all feel warm and fuzzy about it. who gets the credit for that? do we even remember by then that we built this thing that would potentially impact LTV? what if simultaneously purchase velocity went down? 

we have to push for clarity in the goals of a new data product (a new table with new reports built on it *is* a data product). this is where process steps in to save us. rather than putting the onus to pushback on data team members, if we have a process in place as part of shipping new products that is baked into development, the expectation is not individual. this makes it easier to send the stakeholders back to think harder about what *actions* they are going to take and *decisions* they are going to make with this data. we're talking practical, operational things here: are they going to look for trends and cohorts and use that to tweak the ad spend strategy? are they going to email blast lapsed buyers? these may be more likely to have different outcomes, and forces them to zero in and the most important thing they want to impact. for our example, let's keep it simple and say they're going to use it to email lapsed buyers with a discount code, and they've determined they think they have the best bet at increasing purchase velocity. now it's back to us. sitting together we can look at discount code response over the past couple years and formulate a target. let's say we think we're going to increase purchase velocity by 5% within 6 months of this approach. rather than just write than down somewhere to manually track it, as we've offloaded it into our development process, we'll automatatically track it. here's how:

datatest
{{ ref thing }}

the key here is we're not testing the model we're building, we're testing a separate metric that already exists, but relating it to that table, and via tag, to that team, and to this subset of tests (which we will want to separate from our other types of bespoke tests).

we can run this set of tests every morning before standup, or every week before our team meeting, it's up to the team to decide. they will return WARNS for all of our products which failed to hit that target.

we can do so many things with this! we can figure out which teams or areas of the business we're failing to work with effectively. we have an automated record of how our efforts are working. we're getting feedback on if we're setting our targets well or should be spending more time on pre-analysis. and best of all, we've created a consistent, cooperative, impersonal process for pushing back on requests until they are clear and measurable. and it's easy! it's right in our development flow with a quick bespoke test.

if you find yourself struggling to push back on requests or track the results of your teams efforts -- give this method a try! i'd love to hear about the results and any ideas for improving this method.