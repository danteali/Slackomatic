
```
><><><><><><><><><><><><><><><><><><><><><
>< SLACKOMATIC - COMMAND LINE MESSENGER ><
><><><><><><><><><><><><><><><><><><><><><
```

**Send messages to Slack from the command line!**

Very useful for including in scripts etc to notify you on completion of tasks, errors, etc. 

Register a Webhook for Slack [here](https://my.slack.com/services/new/incoming-webhook)

Download this script and make executable:

```
wget https://raw.githubusercontent.com/danteali/Slackomatic/master/slack
chmod +x slack
```

Run script `./slack` without any options to see full usage instructions. 

At a minimum you have to pass a username (-u) and some text (-t) to display. And also the webhook you just registered (-w) but I would recommend editting the script and setting the WEBHOOK variable at the very top of the script.

Have fun!


Usage...

```
=========
= BASIC =
=========
Basic messages simply show a message from a specified username.
    -u    Username ........ [REQUIRED] User/App to display that posts the message.
    -t    *Text ........... [REQUIRED] 'Basic' message text, shown above attachment content.
    -c    Channel ......... [Note 2] Specify Slack channel. If not defined the webhook's channel will be used (#notifications).
    -e    Emoji ........... [Note 7] Emoji image for sender, see: https://unicodey.com/emoji-data/table.htm

==============
= ATTACHMENT =
==============
Attachment messages include an additional 'attachment' displayed under the basic message detailed above.
    -T    Title ........... Title is displayed as larger, bold text near the top of a message attachment.
    -l    Title Link ...... [Note 8] Hyperlink for Title (must contain 'http' part).
    -m    *Message ........ The main text in a message attachment.
    -p    *Pretext ........ Text that appears above the message attachment block.
    -C    Color ........... [Note 3] Colour of vertical bar on left of attachment. See: http://www.color-hex.com/
    -a    Author .......... Text to display as author's name at the top of attachment.
    -b    Author Link ..... [Note 8] Hyperlink for Author text (must contain 'http' part).
    -B    Author Img URL .. URL to image to display on left of Author text. Will be resized to 16x16.
    -F    *Footer ......... Text to be displayed in small font at the bottom of the attachment.
    -f    Footer Img URL .. URL to image to be displayed beside the footer. Will be resized to 16x16.
    -I    Image URL ....... [Note 4] URL to image to display below the attachment. Will be resized to max 360x500.
    -i    Thumbnail URL ... [Note 4] URL to image to display as thumb on right side of attachment. Will be scaled to 75x75.
    -q    Fallback ........ Basic text to display if the attachment can not be displayed on user's device.
    -P    Priority ........ [Note 6] Some pre-configured message formats.

=========
= OTHER =
=========
    -w    Webhook ......... Set API Webhook variable within script (at very top) or pass one if not setting in script.
    -h    Help ............ Display this guidance.
    -x    Dry-run ......... Display payload to be sent to Slack but don't actually execute send command.


~~~~~~~~~
~ NOTES ~
~~~~~~~~~
    1 ... When supplying values for the options above, use double quotes to contain the text. Remember to escape (\) any quotes
          within your submitted text.
    2 ... The following channels are available in my Slack workspace (as of April 2018):
          #notifications (default as using this channels webhook) ; #alert ; #backup ; #media_stack ; #monitor ; #system
    3 ... Colors (-C) are specified in hex values, lookup here: http://www.color-hex.com/
          This script has several pre-defined colors built-in therefore the following can be specified as text instead of a hex value:
          green (#008000), orange (#FFA500), red (#FF0000), blue (#0000FF), purple (#800080), pink (#FFC0CB), yellow (#FFFF00)
    4 ... Both Image and Thumbnail can not be displayed in same message. Image will take precedence over thumnail if both are supplied.
    5 ... Any characters should be okay to be entered in any field but the following three characters must be substituted:
              > Replace the ampersand, &, with &amp;
              > Replace the less-than sign, < with &lt;
              > Replace the greater-than sign, > with &gt;
    6 ... A set of priorities (case-sensitive) have been defined in this script. Specify one of the following to apply a pre-defined 'template':
              > info : message prefix = 'INFO' ; color = blue ; emoji = :information_source: (blue 'i' sign)
              > success : message prefix = 'SUCCESS' ; color = green ; emoji = :heavy_check_mark: (green tick)
              > alert : message prefix = 'ALERT' ; color = red ; emoji = :warning: (yellow warning sign)
          Any of these pre-defined fields can be individually overridden by passing that cmd line option
    7 ... Some useful emojis: :film_frames:, :tv:, :iphone:, :computer:, :floppy_disk:, :file_folder:, :warning:,
          :no_entry:, :hourglass:, :heavy_check_mark:, :hankey:, :fire:, :inbox_tray:, :information_source:
    8 ... Links can also be email 'mailto's e.g. mailto:admin@testing.com
    9 ... 'Fields' and 'Actions' can also be sent via command line but this functionality has not been implemented here.

**********
* MARKUP *
**********
    Fields tagged with a '*' above can have Slack's markup applied to their content. Supported options:
        > *bold*
        > _italic_
        > ~strikethrough~
        > `inline code` - ticks need to be escaped with '\'
        > ```embedded code``` - ticks need to be escaped with '\'
```
