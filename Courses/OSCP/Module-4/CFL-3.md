# Linux Process and Job Management

Every command or tool executed in Linux consumes CPU time and system memory. Managing how these processes run, pause, and terminate is essential for maintaining control over operational tools.

---

## 1. Foreground vs. Background Processes

When a command takes a long time to execute, it locks the terminal session (Foreground). To keep using the terminal, you can send the process to the background.

* **Run a command in the background (`&`):**
  Appended to the end of any command to execute it immediately in the background, freeing up the terminal shell.
  ```bash
  sleep 1000 &
  ```
* **`jobs`** : Displays an active list of background tasks managed by the current terminal session.
  * Note: The `+` sign indicates the most recently added job, while the `-` sign indicates the job added just before it.

---

## 2. Managing Background Jobs

* **`fg %<job_number>`** : Brings a background job back to the foreground (e.g., `fg %1`). Running `fg` without parameters will bring back the latest job marked with `+`.
* **`Ctrl + Z`** : Pauses/Suspends a running foreground process and sends it to the background in a "Stopped" state.
* **`bg`** : Resumes a paused background job, keeping it running in the background.

---

## 3. Persistent Processes (Surviving Terminal Closure)

Standard background jobs are tied to the current terminal session. If the terminal closes, the jobs receive a `SIGHUP` signal and terminate.

* **`nohup <command> &`** : Runs a command that is immune to hangups (`SIGHUP`). The job continues running even if the terminal window is closed.
  ```bash
  nohup sleep 9000 &
  ```
* **`disown`** : Used if you forgot to use `nohup`. 
  * *Procedure:* Pause the running task with `Ctrl + Z`, resume it in the background using `bg`, and then execute `disown` to detach it from the terminal session.
  * *Note:* While persistent processes survive terminal closure, they are completely wiped out upon a system reboot.

---

## 4. Monitoring Processes

* **`ps aux`** : Displays a comprehensive snapshot of all actively running processes across the entire operating system.
* **Filtering specific processes:**
  ```bash
  ps aux | grep sleep
  ```
  *This assists in locating the critical **PID** (Process ID) needed for termination.*

---

## 5. Terminating Processes (How to Kill a Process)

To terminate a process, you must target its unique Process ID (PID) using signals.

**Syntax:** `kill -<signal_number> <PID>`

### Essential Kill Signals:
* `kill -1 <PID>` (**SIGHUP**) : Reloads or hangs up the process.
* `kill -2 <PID>` (**SIGINT**) : Interrupts the process (equivalent to pressing `Ctrl + C`).
* `kill -15 <PID>` (**SIGTERM**) : The default termination signal. Requests the process to clean up and shut down gracefully.
* `kill -9 <PID>` (**SIGKILL**) : Forcefully kills the process immediately, even if it is stuck executing inside the kernel space.

### Mass Termination Utilities:

If multiple processes of the same tool are running, killing them manually by PID is inefficient.

* **`killall -9 <process_name>`** : Forces immediate termination of all active processes that match the exact name specified.

   ```bash
  killall -9 sleep
  ```
* **`pkill <pattern>`** : Terminates any process whose name partially matches the specified pattern or keyword.

  ```bash
  pkill slee
  ```
