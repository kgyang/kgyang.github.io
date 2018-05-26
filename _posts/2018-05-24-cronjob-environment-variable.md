---
#layout: post
title:  "Set environment variables that crontab can uses"
---

I've added port forwarding rules in my home router so that I can access my raspberry pi at home from outside. But my home router does not have fixed WAN IP. Each time it reboots, the service provider assigns a different WAN IP. So I wrote a script of detecting WAN IP change and sending email of reporting the new WAN IP. The script works on raspberry pi's shell. So I added a cron job to run this script per hour. Unluckly, this script does not work when it is run by cron daemon. What's wrong with it?

Debugging shows the reason is that the script could not get mail information correctly from environment variables defined in .profile. Login process sources .profile and set these envrionment variables, but the cron job does not.

How to resolve it?

I found multiple solutions in this [stackoverflow link][reference]. The simplest is this:

    # 0 5 * * * . $HOME/.env_profile; /path/to/command/to/run


[reference]: https://stackoverflow.com/questions/2229825/where-can-i-set-environment-variables-that-crontab-will-use
