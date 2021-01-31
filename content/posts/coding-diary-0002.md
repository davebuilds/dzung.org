---
title: "Coding Diary 0001"
date: 2021-01-31T17:50:19-08:00
draft: true
---

Today I've completed a Python script that automates scheduling my calendar. I feed the script my todo list, where each item contains an estimate column which estimates how much time do I need for the task.

I've started practicing time blocking recently and I like it so far. My todo list is practically zero now. If something is important enough, I'll block some time in my calendar. If not I just toss it out.

However it's a huge pain to reschedule things when I fail to follow the schedule.

The script uses Google Calendar Python Api to fetch my calendar, find free blocks, then insert my todo items.

To block out busy times, I hard-code them inside the script.

I have been working on this script on and off for a couple of days. I didn't want to spend to much time but working with time was tricky for me. Some tasks that I spent the most time was finding a list of free time blocks for a day given some predefined rules for busy blocks, and (2) fitting my to do list to those blocks. I ended up writing lot of unit tests for the code because I wasn't confident with my implementation. Using Google Calendar Python api was surprisingly easy despite the api felt weird.

If I continue practicing time blocking in future, I'll try to make a web UI for the script to make it easier to use.
