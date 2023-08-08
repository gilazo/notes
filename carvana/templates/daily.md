## daily reminders
> [!IMPORTANT]
> Don't forget to pray

## daily tasks
> [!TODO]
> These dailys tasks are tracked in the [[kanban/daily kanban]]

```dataviewjs
const offset = '<% tp.date.now() %>';
dv.taskList(dv.page("carvana/kanban/daily work kanban").file.tasks.where(t => dv.equal(t.due, dv.date(dv.current().file.name))))
```


## daily log
> [!SUMMARY]
> The daily log for later reflection
