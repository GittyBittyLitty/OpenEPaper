These are some example Google Apps Scripts that can be used to display various things.

# Google Calendar
To use Google Apps Script to get all events for the next day and return them via JSON in a web app, you can follow these steps:
* Create a new Google Apps Script project by going to [https://script.google.com](https://script.google.com) and clicking on "New project".
* Paste the following code into the editor:
```js
function getEventsForNextDay(days) {
  var start = new Date();
  start.setHours(0, 0, 0, 0);
  var end = new Date();
  if (days == undefined) days = 1;
  end.setDate(end.getDate() + parseInt(days, 10));
  var calendars = CalendarApp.getAllCalendars();
  var events = [];
  for (var i = 0; i < calendars.length; i++) {
    var calendar = calendars[i];
    var eventsInCalendar = calendar.getEvents(start, end);
    for (var j = 0; j < eventsInCalendar.length; j++) {
      var event = eventsInCalendar[j];
      events.push({
        calendar: i,
        title: event.getTitle(),
        start: Math.floor(event.getStartTime().getTime() / 1000),
        end: Math.floor(event.getEndTime().getTime() / 1000),
        isallday: event.isAllDayEvent()
      });
    }
  }
  events.sort(function(a, b) {
    return a.start - b.start;
  });
  return JSON.stringify(events);
}

function doGet(e) {
  if(!e) { 
    e = {parameter: {days: 1}};
  }
  const params = e.parameter;
  var content = getEventsForNextDay(params.days);
  var output = ContentService.createTextOutput(content);
  output.setMimeType(ContentService.MimeType.JSON);
  return output;
}
```
This App Script calls the `getEventsForNextDay()` function to get the events in JSON format, creates a text output with the JSON content, sets the MIME type to JSON, and returns the output.

* Deploy the web app by clicking on "Deploy > New Deployment" in the script editor
* Choose "Web app" as the deployment type
* Set the access to "Anyone, even anonymous"
* click on "Deploy"
* Make sure to take note of the web app URL generated by Google.
* Test the web app by visiting the web app URL in a web browser. You should see the events for the next day in JSON format.

# Google Task List (ToDo List)
This is a script for displaying your Google task list.
It uses the [[JSON-Template|Json-template]] to generate a list of tasks.
You can specify the used font by appending `?font=0` up to `?font=3` to the App Scripts URL

```js
const fonts = [
  {name: "t0_14b_tf", startY: 13, height: 13, maxItems: 9, maxLength: 80},
  {name: "7x14_tf", startY: 14, height: 14, maxItems: 9, maxLength: 80},
  {name: "glasstown_nbp_tf", startY: 14, height: 14, maxItems: 9, maxLength: 80},
  {name: "fonts/bahnschrift20", startY: 0, height: 20, maxItems: 6, maxLength: 30},
];

function getTasksOfTaskList(taskListId) {
  var tasks = [];
  try {
    tasks = Tasks.Tasks.list(taskListId).items;
  } catch (err) {
    // console.log('Failed with an error %s', err.message);
  }
  return tasks;
}

function getAllTaskListTasks() {
  var tasks = [];
  try {
    const taskLists = Tasks.Tasklists.list();
    if (!taskLists.items) {
      return tasks;
    }
    for (let i = 0; i < taskLists.items.length; i++) {
      const taskList = taskLists.items[i];
      const taskListTasks = getTasksOfTaskList(taskList.id);
      for (let i = 0; i < taskListTasks.length; i++) {
        tasks.push(taskListTasks[i]);
      }
    }
  } catch (err) {
    // console.log('Failed with an error %s ', err.message);
  }
  return tasks;
}

function getTasks(fontNumber) {
  if(!fontNumber || fontNumber >= fonts.length)
  {
    fontNumber = 0;
  }
  const font = fonts[fontNumber];

  const tasks = getAllTaskListTasks();
  var events = [];
  var x = 0;
  var y = font.startY;
  for (let i = 0; i < tasks.length; i++) {
    const task = tasks[i];
    events.push({text: [x, y, task.title, font.name, 1]});
    y += font.height;
    if(events.length >= font.maxItems)
    {
      break;
    }
  }
  return JSON.stringify(events);
}

function doGet(e) {
  if(!e)
  {
    e = {parameter: {font: 0}};
  }
  const params = e.parameter;
  var content = getTasks(params.font);
  var output = ContentService.createTextOutput(content);
  output.setMimeType(ContentService.MimeType.JSON);
  return output;
}
```

# RSS Feeds
This is a workaround for the currently used RSS implementation of the OEPL AP, which does work well with each and every RSS feed.
To fix this issue the following script can be used to let Google Apps Script parse the RSS feed data and provide it as [[JSON-Template|Json-template]].
To use this script append one or both of the following options to the Apps Script URL:
* `font=0` up to `font=3` for font selection
* `url=https://www.myrssfeed.de/rss.xml` to provide the RSS feed

Examples:
* `<Apps Script URL>?font=2` (this will default to the URL configure in the Apps Script)
* `<Apps Script URL>?font=2&url=https://rss.golem.de/rss.php?feed=RSS2.0` (golem.de rss feed)

```js
const fonts = [
  {name: "t0_14b_tf", startY: 13, height: 13, maxItems: 9, maxLength: 80},
  {name: "7x14_tf", startY: 14, height: 14, maxItems: 9, maxLength: 80},
  {name: "glasstown_nbp_tf", startY: 14, height: 14, maxItems: 9, maxLength: 80},
  {name: "fonts/bahnschrift20", startY: 0, height: 20, maxItems: 6, maxLength: 30},
];

const defaultUrl = "https://www.tagesschau.de/infoservices/alle-meldungen-100~rss2.xml";

function getRssFeed(fontNumber, url) {
  if(!url)
  {
    url = defaultUrl;
  }
  if(!fontNumber || fontNumber >= fonts.length)
  {
    fontNumber = 2;
  }

  var feed = UrlFetchApp.fetch(url).getContentText();
  feed = XmlService.parse(feed);
  const items = feed.getRootElement().getChild("channel").getChildren("item");

  const font = fonts[fontNumber];

  var events = [];
  var x = 0;
  var y = font.startY;
  for (var i in items) {
    const text = items[i].getChild("title").getValue().substring(0, font.maxLength); 
    events.push({text: [x, y, text, font.name, 1]});
    y += font.height;
    if(events.length >= font.maxItems)
    {
      break;
    }
  }
  return JSON.stringify(events);
}

function doGet(e) {
  if(!e)
  {
    e = {parameter: {font: 1, url: defaultUrl}};
  }
  const params = e.parameter;
  const content = getRssFeed(params.font, params.url);
  var output = ContentService.createTextOutput(content);
  output.setMimeType(ContentService.MimeType.JSON);
  return output;
}
```