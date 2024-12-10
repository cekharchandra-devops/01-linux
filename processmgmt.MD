# process management

a sequence of steps to be executed to complete a task..


```
ps -ef | grep nginx
```

***foreground vs background***

sleep 10 --> it blocks the terminal. run in foreground

how can we run a process in background (sleep 100 &)

to list which process consumes howmuch cpu, memory

```
top
```

to kill the process

```
kill <pid>
```
to force kill
```
kill -9 <pid>
```

# Network Managment
--------------

```
netstat -lntp
```