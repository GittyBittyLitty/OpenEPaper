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