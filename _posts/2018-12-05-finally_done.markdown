---
layout: post
title:      "FINALLY DONE"
date:       2018-12-05 23:18:25 +0000
permalink:  finally_done
---


After a month long hiatus from the program due to career changes, I dove back into the CLI Data Gem Project. 
My first surprise was getting an HTTP redirect error with the website I was trying to use. Looking into this provided helpful information on scraping practices,  the anti-scraping measures websites can employ, and redirection loops. My issue seemed to fall into the third category, and though there is a gem that can be installed to remedy this, I figured since I was just starting I could pick a different site. 
So I chose Wikipedia; it seemed like a safe option given the scraping tutorials online that utilize it. 
What I needed was a list of science fiction novels that were all links to the actual information about the book. This was  a little difficult to find, since many of the "top science fiction novels of all time" types of articles did not go one level deeper, and just had  the novel information on the same page. 
I wanted to be able to randomly pull any one of those titles, and give the user the option of getting more information (author, summary, date etc) on it. I didn't just want one long numbered list, but rather a randomized suggestion tool, kind of like a very, very basic version of https://www.whichbook.net/.  
My second big error to contend with was a NoMethod error, which I found the solution for after going through a dizzying bunch of Stackoverflow questions. 
The CLI seems to be functioning properly now, so hopefully it doesn't throw any new errors my way when it's judgement time.
