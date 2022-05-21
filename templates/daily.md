## daily reminders
> [!IMPORTANT]
> Don't forget to pray

## daily tasks
> [!TODO]
> These dailys tasks are tracked in the [[daily kanban]]

```dataviewjs
const offset = '<% tp.date.now() %>';
dv.taskList(dv.page("kanban/daily kanban").file.tasks.where(t => dv.equal(t.due, dv.date(dv.current().file.name))))
```

## daily log
> [!SUMMARY]
> The daily log for later reflection
