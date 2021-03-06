# GoogleCalendarBirthdayNotifications
Receive email notifications before your contacts birthday.

## How to setup

### Enable the calendar
First of all you need to enable your contacts birthday calendar in you Google Calendar (see [this](https://support.google.com/calendar/answer/6084659?hl=en)).

### Create the script
Copy the content of [this file](https://raw.githubusercontent.com/GioBonvi/GoogleCalendarBirthdayNotifications/master/code.gs).  
Open [Google Script](https://script.google.com) and login if requested, then paste the code into the page.

### Customize the script
Now read carefully the code you've pasted. At the beginning of the file you will find some lines you need to modify along with many lines of instructions. Edit the values as explained.  
You must adjust the values of these variables:

-   myGoogleEmail
-   myEmail
-   calendarId
-   myTimeZone
-   notificationHour
-   anticipateDays
-   lang

Now click File->Save in the menu and enter a name for the script (it doesn't really matter, just name it so that you'll recognize if you find it in the future).

### Activate API for the script
Now that the script is saved in you Google Drive we need to activate it. To do so click the menu Resources->Advanced Google services.  
In the popup which will open set "Google Calendar API" to "enabled" (click the switch on its row on the right). We are almost done! Click on the link which says "Google API Console": you will be taken to another page. In this page search for "Google Calendar API" and open it. Now click "Enable" at the top of the window and close this page.

### Grant rights to the script
This should be enough to enable the app to do its work: now the last step is granting it the rights it needs. To do so click on the menu Run->start. You will be prompted to "Review authorizations": do it and click "Allow".  
You might receive a first email immediately: the following ones will be sent at the hour you secified.  
From this moment on you will always receive an email before any of your contacts' birthday (You should have set how many hours before at the beginning).

### Bonus (Translation)
If you want to add a new translation of the notifications, open your script, find the line ```var i18n``` and have a look at the structure of the translation object and at the instructions at the end.

To add a new language:

-   find the block of code which represents one existing translation and copy it, for example:
```
'el' : {
  'UNKNOWN': 'ΑΓΝΩΣΤΟΣ',
  ...
  'send email now': 'στείλτε email τώρα',
},
```
-   paste it just below itself, like this:
```
'el' : {
  'UNKNOWN': 'ΑΓΝΩΣΤΟΣ',
  ...
  'send email now': 'στείλτε email τώρα',
},
'el' : {
  'UNKNOWN': 'ΑΓΝΩΣΤΟΣ',
  ...
  'send email now': 'στείλτε email τώρα',
},
```
-   replace the language code of your translation with your language code and proceed to translate every item in the list, leaving the string on the left of the `:` unchanged and translating the one on the right, like this:
```
'el' : {
  'UNKNOWN': 'ΑΓΝΩΣΤΟΣ',
  ...
  'send email now': 'στείλτε email τώρα',
},
'it' : {
  'UNKNOWN': 'SCONOSCIUTO',
  ...
  'send email now': 'invia email ora',
},
```

If you want to share your translation with other users please open an issue or a pull request on the [GoogleCalendarBirthdayNotifications GitHub's project page](https://github.com/GioBonvi/GoogleCalendarBirthdayNotifications). I will be glad to add your translation to the script.

### Bonus (Stop notifications)
To stop receiving these notifications simply open the script (which you'll find [in Google Drive](https://drive.google.com/drive/) if you haven't moved it) and click the menu Run->stop.

## Bug and error reporting, help requests
First of all _before submitting a new error, bug or help request_, please, __verify that you followed [the instructions](https://giobonvi.github.io/GoogleCalendarBirthdayNotifications/) to the letter.__

To report a bug or an error or to request help with this script please use [this project GitHub issue page](https://github.com/GioBonvi/GoogleCalendarBirthdayNotifications/issues).
I will be notified immediately and will provide help as soon as possible. It is easier for me if you test the latest version from the master branch
of the github repo for the bug, but if that is too confusing I should still be able to help as the logs will include the version number you are using.

In the text of the message please include:
-   A __meaningful description of the problem__. What did you do? What happened? What did you expect to happen instead?
-   A __full copy of any error message you received or of the thing that went wrong__. Please be advised that it could contain personal information such as your email: obscure or remove them as alla the issues and relative messages are publicly visible.
-   The __complete _log_ of the script__. To obtain it open your script, find the line which reads `var sendLog = false;` (it is in the _DEBUGGING OPTIONS_ part, just below the _MANDATORY CUSTOMIZATION_ at the top of the script) and change it to read `var sendLog = true;`. Now click "Run" > "normal" in the menu at the top of the page. You should now receive an email with the complete log of the script.
-   To disable the logging and stop receiving log emails just change `var sendLog = true;` back to `var sendLog = false;` again.

I really need these informations: without them I will not be able to help you.

### Bonus (Test)
If you want to test the script, but in these days none of your contacts have a birthday you can use the ```test()``` function.

To do so, open the script and edit the `fakeTestDate` variable in the debugging configuration section. You just need to replace the example date
with the date you want to test, then click "Run" > "test" in the menu at the top of the page. If everything went right you should receive a
birthday notification exactly like if today was the date you set.

## License
GoogleCalendarBirthdayNotifications is licensed under the MIT license (see the [LICENSE FILE](https://github.com/GioBonvi/GoogleCalendarBirthdayNotifications/blob/master/LICENSE)).

## Credits
The main idea of this script was inspired by ajparag's response to this exact problem, which he posted in the [Google Help Forum](https://productforums.google.com/d/msg/calendar/OaaO2og9m5w/2VgNNNF5BwAJ).

Huge thanks to [rowanthorpe](https://github.com/rowanthorpe), who completely refactored the code adding many amazing features I had never thought of.
