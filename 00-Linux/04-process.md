### Process-management
Processes are the programs that are running on your machine. They are managed by the kernel and each process has an ID associated with it called the process ID (PID). This PID is assigned in the order that processes are created.

```ps```

This shows you a quick snapshot of the current processes:

- PID: Process ID
- TTY: Controlling terminal associated with the process (we'll go in detail about this later)
- STAT: Process status code
- TIME: Total CPU usage time
- CMD: Name of executable/command

```ps aux```
-   a -all processes running

-   u -shows more details about the processes
-   x -ists all processes that don't have a TTY associated with it


Another very useful command is the ```top``` command, top gives you real time information about the processes running on your system . By default you'll get a refresh every 10 seconds. Top is an extremely useful tool to see what processes are taking up a lot of your resources.
### kill process

``` kill -9 <PID>```

### Find Specific process
Filtering Specific Processes
You can filter the output using grep to find a specific process. For example, to find processes related to apache2:
```
ps -ef | grep apache2
```


***more***:
[process-management](https://linuxjourney.com/lesson/monitor-processes-ps-command)
