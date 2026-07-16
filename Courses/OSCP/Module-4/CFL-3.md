# Managing Processes:

* Any command run get some time from CPU and memory.
* Sometime this command execute in terminal and can't write another command at same time.
* Only write "&" in last of command and this will work in background.

Ex: sleep 1000 & -> will give IDP to you

* To see this jobs run in background use command:
  "jobs"
  Find "+" for last add and "-" for before it.

* To see all processes work on CPU use:
  "ps aux"

Ex: ps aux | grep sleep

* Now we know how we can make it work in bg. How can return to it? Use:
  "fg %<number for it>"
  "+" / "fg" only for last jobs add.

* To return it again to background:
  Ctrl + Z then "bg"

* But when we close terminal and open it again we not find any job in background.
* To add it to bg and work also when close terminal write "nohup" before command:
  "nohup sleep 9000 &"

* If you forget write "nohup" and the job is running, absolutely click "ctrl + z", when it stopped in the background write "bg" then write "disown".

* Now we can't return for this jobs again when close terminal and open new one.
* But also when reboot all delete.

## How to kill process

Use "ps aux" and find process ID for your process.

* Command: "kill <ID-process>"
  This as default make terminated for process "-15"

* Command: "kill -1 <ID>" make Hangup
* Command: "kill -2 <ID>" make Interrupt
* Command: "kill -9 <ID>" make killed, also if work in kernel.

* Want to close Group of process:
  for i in {<From ID>..<To_ID>}; do kill -9 $i; done
  But this is not efficient so:

  Use: killall -9 sleep
  All with name sleep will killed.

Also:
  "pkill slee"
  Any process have "slee" in his name.

