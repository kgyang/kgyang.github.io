---
#layout: post
title:  "Summarize Coding Work"
---

In the beginning of year of 2018, I had a thought to see how much work I did since joined company. To see how much coding might be an interesting thing. So I spent several days on writing a script to do such thing. The following decribes the way.


Basic Principle
---------------
We use clearcase as version control, and JIRA as issue tracking. JIRA allows me to get all of the issues I've resolved and each issue contains the check-in history in clearcase. Then I can use tools such as 'diff' to work on check-in history to get the coding statictics. 

Steps
-----
1. Use following query rules to filter out JIRA issues:

        (resolver = currentUser()) OR (assignee = currentUser() AND (project = xxx OR project = yyy) ORDER BY key DESC 

2. Export the query result to a file with CSV format.
3. Parse the query result file to get all check-in history.
4. For each check-in, calculate the code insertions and deletions and save them to a summary file:

        stats=$(diff -u --strip-trailing-cr <preversion> <checkinversion> | diffstat | tail -1)
        insertions=$(sed -n 's/.* \([[:digit:]]*\) insertion.*/\1/p' <<< $stat)
        deletions=$(sed -n 's/.* \([[:digit:]]*\) deletion.*/\1/p' <<< $stat)

5. Add up all insertions and deletions in the summary file.

Here is the result:

    Year    Issues  Files   Insertions      Deletions
    2018    1       3       31              29
    2017    53      362     14877           10663
    2016    49      278     15135           13083
    2015    66      266     16716           10604
    2014    53      270     18040           9318
    2013    36      336     26192           13666
    2012    48      274     8007            6720
    2011    16      65      3250            2026
    Total   322     1854    102248          66109



