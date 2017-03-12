# scheduledosx

Running a task as scheduled even multiple times a day on OS X

- launchd is used to register a task at scheduled time
- pmset is used to wake up a OS X machine 
- pmset needs to be run after every running of a task for the next wakeup


# launchd
launchd is a tool or system which replace crond or cron job system in osx. (Refer http://www.launchd.info)
You can run a task by putting a task desription file (xml plist file) in ~/Library/LaunchAgents.
Each description plist file contains information about a program or script to run. 
You can schedule the running of a program using 'StartCalendarInterval' specifications in plist file.

For example.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
  "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.example.happybirthday</string>
    <key>ProgramArguments</key>
	<array>
        <string>path/to/your/program_to_run</string>
        <string>param1</string>
    </array>
    <key>StartCalendarInterval</key>
    <dict>
        <key>Hour</key>
        <integer>0</integer>
        <key>Minute</key>
        <integer>0</integer>
    </dict>
</dict>
</plist>
```

For more information on these values, see the manual page for launchd.plist.




# pmset 
Using pmset you can scheudle a osx machine to wake up at a specific time. (Check 'man pmset' for more details)

## pmset basic examples
pmset schedule wakeorpoweron "06/07/2007 07:00:00"

## pmset repeat example
pmset repeat wakeorpoweron MTWRFSU 06:45:00

**pmset** can set only one 'repeated schedule' on a machine.

