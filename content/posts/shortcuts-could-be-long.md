---
title: "Shortcuts could be long"
date: 2021-02-24T22:58:07-08:00
draft: false
---

Yesterday my manager pinged me at 5pm about an urgent task. He's a big advocate of work life balance, so if he asks you something at 5pm, it must be important.

The task was straightforward. To not revealing anything about the business, all I could say is that it's an analogy of "for all tables, find all rows where column `fruit` = `BlueBerry`".

"The task is urgent. It's 5 pm. What's the *shortcut*?" - I thought.

"No way I would write a script now. Let's get the task done." - I reminded myself of [that xkcd](https://xkcd.com/1205/).

Since the query was simple, and not all tables contain the column `fruit`, so my shortcut was opening DataGrip, visually checking each table to see if they have that column, and executing this query `select count(*) from <table> where fruit = 'BlueBerry'`.

It sounded easy-peasy and it just required some patient, right? Turned out it was not a shortcut at all.

As we didn't create index for those columns, the query took 2 minute per table. I had to open many DataGrip query consoles and fired up a spreadsheet to keep track of the progress.

And worse, half way done I noticed that there was a table where the column was `fruit_code`, not `fruit`. Shit! I must have missed similar columns. Now I had to restart the progress. And now it was a big mess.

If I had not made a shortcut, if I had put more thoughts and "over-engineered" it, I would've written a script that queried the catalog to find the tables containing `%fruit%`-like column, then ran the `select count(*)` for each of those tables. I would be able to run the select queries in parallel after I realized they were slow. If I made a mistake, I would be able to correct it by modifying and re-running the script. These were many benefits of a proper script, and I haven't talked anything about reusability.

This was not the first time my short term solutions had caused more harm than good. There's nothing wrong with taking shortcuts when the time is tight. My mistakes are setting completion time expectation too tight, and letting that fake urgency affects my judgements.

Let's talk about deadline. Almost all deadlines in American corporates are artificial. Teams delay their projects all the time, and even if they deliver it's usually a simplified version compared to their plan. If I had to simplify my job, it would be displaying some data from a database to some business persons' screens. What could go wrong if I take several more hours to complete a task? If a task were that important and urgent to them, they would have create a high severity ticket and escalate it.

Urgency does have benefits. For me it could ignite some fire and make me focus easier. But be mindful when you start taking shortcuts. It's not the shortcuts that are harmful, it's the lazy thinking you start having when you say yes to shortcuts. Lazy thinking could lead you to the longer roads, and sometimes the wrong ones.
