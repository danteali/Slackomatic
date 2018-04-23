
```
><><><><><><><><><><><><><><><><><><><><><
>< SLACKOMATIC - COMMAND LINE MESSENGER ><
><><><><><><><><><><><><><><><><><><><><><
```

**Send messages to Slack from the command line!**
Very useful for including in scripts etc to notify you on completion of tasks, errors, etc. 

Download and make executable:

```
wget https://raw.githubusercontent.com/danteali/Slackomatic/master/slack
chmod +x slack
```

Register a Webhook for SLack [here](https://my.slack.com/services/new/incoming-webhook)

Run script `./slack` without and optoins to see full instrcutions. 

At a minimum you have to pass a username (-u) and some text (-t) to display. And also the webhook you just registered (-w) but I would recommend editting the script and setting the WEBHOOK variable at the very top of the script.

Have fun!
