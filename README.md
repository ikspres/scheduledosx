# scheduledosx

Running a task as scheduled even multiple times a day on OS X

- launchd is used to register a task at scheduled time
- pmstat is used to wake up a OS X machine 
- pmstat needs to be run after every running of a task for the next wakeup
