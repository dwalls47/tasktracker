# tasktracker
A glorified TODO list
- tasks to complete
-   sub tasks
- prerequisites / dependancies
- log time
- calendar
- reports
- API, so other application can integrate
 

Task table
- id_task
- id_task_parent (if 0 then a separate project) / for decomposition of tasks
- priority / order (unique in table)
- due_date
- task_name
- task_description
- keywords (used for selection and reporting)
- hours (hours to complete) / sum of subtasks
- username (assigned to)
- group (assigned to group or department)


Task Types (how should these be handle)
- recurring (a meeting every week)
- ticket (maybe these always fall under a certain "permanent" task (i.e. Tickets, Bugs)
- pinned (?)

Dependancy table
- id_task
- id_task_dependance
- 


Work Time table
- id_work_time
- username
- work_date
- work_hours
- 


Calendar table (for recording holidays to enable more accurate scheduling)
- id_calendar
- holiday_date
- holiday_name
- 


Use Cases
- User begins working on a task. At end of work period user records time spent on task and how much time remaining to complete task. If time remaining is 0, then task is complete.
- Report: Future schedule - A report which creates a calendar with estimated completion times for events. Recursively walk task trees based on keywords or depth.
- Report: Past work - A basic timesheet report
- Task is broad - Decompose the task into subtasks to better estimate completion time.
- Task is dependant on another task - dependancies override task prioritization
- Task has hard deadline / due date - due dates override task prioritization
- 

A scheduling algorithm
- Fudge factors. One could be hours in a day. Using six-hour days could help account for unforeseen delays.
- Due dates first (in order of due date, then priority). Tasks with due dates can only be pushed back (late completion) when there isn't time available to complete it (and its dependancies). Task with due dates can be pushed forward (early completion) as necessary. Holidays can be treated like an all-day task with a due date which cannot be moved to another time. (Example: Holiday on 6th; Two-day task due on 5th; Seven-day task due on 13th. The two-day task would be scheduled for 2nd-3rd; the seven-day task would be scheduled on 4th-5th, 9th-13th.)
- Dependancies second (in order of priority). All of a task's dependancies must be scheduled before the task.
- Everything else last (in order of priority). Fill in gaps and schedule remainder at end.
- The "hard" part: rescheduling conflicts.
- 


Development Priority
- Tasks without due dates and dependancies, and related future schedule report
- Tasks with due dates, and related future schedule report
- Tasks with dependances, and related future schedule report
- Holidays, and related future schedule report
- Work hours
- Task types
- 
