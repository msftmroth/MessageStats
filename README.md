# MessageStats

NOTE:  Thanks to Neil Johnson, who maintained the article and the script for years!
NOTE:  Thanks to Josh Bryant, this script has now been updated to collect data from Exchange 2007, 2010 and 2013 servers.  
       I have updated the link in this article to point to the new script - thanks Josh!
NOTE:  And finally thanks to Rob Campbell who has written the script


One of the nice things since Exchange 2007 is that we can interrogate the message tracking logs via PowerShell.  
This provides us with a nice way to query what the Exchange Server is doing.  
Usefully the message tracking logs include sufficient information for us to approximate our user profile data to give a sizing a proper base.

NOTE: **This information is vital for performing good quality Exchange server scaling.**

## Getting Started

The script basically works by parsing the messaging tracking logs of your Exchange Servers and then tabulates the information into a CSV file for analysis in Excel.  
To provide some data to parse I configured a loadgen test against 10 mailboxes with a heavy profile, this should approximate to around 80 messages received and 20 sent per user.

The MessageStats script has a single command line parameter which controls how many days back it will look in the tracking logs.  
The script only parses a single days worth of data, the value you provide helps you tell the script which day to process, so 1 will process yesterdays logs.


### Prerequisites

You need the script, (https://github.com/msftmroth/MessageStats/blob/master/MessageStats/MessageStats.ps1) and an Exchange PowerShell.



## Usage

Copy the script to a temp directory, and run it:

```

.\MessageStats.ps1

```

You will get output for every server that will be parsed:

```
Creating a new session for implicit remoting of "Get-AcceptedDomain" command...

Started processing ExServer-01
Processed 1570 log records in 2.8214287 seconds
   Average rate: 556 log recs/sec.

Started processing ExServer-02
Processed 1558 log records in 2.9480638 seconds
   Average rate: 528 log recs/sec.

Started processing ExServer-03
Processed 1878 log records in 4.0387736 seconds
   Average rate: 465 log recs/sec.

Run time was 16.9054231 seconds.
Email stats file is email_stats_2019_04_04.csv
DL usage stats file is DL_stats.csv


```

Outout will be in the same directory:

CSV file with the Mailbox stats data:
email_stats_YYYY_MM_DD.csv

CSV file with the Distribution List stats data:
DL_stats.csv


## Built With

* [PowerShell](https://docs.microsoft.com/en-us/powershell/) - The one and only

## Contributing




## Authors


See also the list of [contributors](https://github.com/msftmroth/MessageStats) who participated in this project.
* Written by **Rob Campbell** - 03/02/2011 - https://devblogs.microsoft.com/scripting/use-powershell-to-track-email-messages-in-exchange-server/
* Updated by **mjolinor** - 02/24/2011
* Updated by **Josh M. Bryant** - 10/8/2014 - to work with Exchange 2013
* Moved to github and fixed some stuff by **Marco Roth** - 04/04/2019 






