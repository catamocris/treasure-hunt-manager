# Treasure Hunt Project 🏴‍☠️

**Treasure Hunt** is a C application that simulates a treasure hunt management system, using **operating system** concepts such as processes, signals and inter-process communication.
The application is composed of multiple processes that communicate with each other and manage treasure hunt data.

---

## Features

### Multi-Process Architecture
The application uses multiple processes created with `fork()`:
 - the **Hub** process: interacts with the user
 - the **Monitor** process: runs in the background and manages signals
 - the **Treasure Manager**: executed when data operations are needed.  
This structure separates the responsibilities between processes and simulates a real operating system environment.

### Inter-Process Communication
The processes communicate using:
- **Pipes** – standard file descriptors are used to send data between processes
- **Signals** – custom signal handlers used for process control and notifications
This allows the processes to work together and exchange information.

### Process Management
The program handles process termination correctly using `wait()` and `waitpid()` and avoids zombie processes using signal handling.

### Command Line Interface
The Hub implements a command line interface where the user can type commands to manage treasure hunts, view treasures and calculate scores.

### Score Calculation
The application includes a component that calculates the score for each treasure hunt using a separate module.

### File Management
Treasure hunt data is stored in files, and the program uses low-level file operations such as `open()`, `read()`, `write()` and `close()` to manage data.

---

## Usage

The main program is the Treasure Hub.
To start the application, run:
```bash
./treasure_hub
```
After starting the program, the user can type commands in the Hub interface (`>` prompt):

| Command | Description |
|---------|-------------|
| start_monitor | launches the background Monitor process |
| stop_monitor | safely stops the Monitor process |
| list_hunts | displays all available treasure hunts |
| list_treasures <hunt_name> | displays all treasures from a specific hunt |
| view_treasure <hunt_name> <treasure> | displays information about a specific treasure |
| calculate_score <hunt_name> | calculates and displays the score for a hunt |
| clear | clears the terminal screen |
| help | displays the list of commands |
| exit | exits the Hub (the monitor must be stopped first) |

## Example Session
```bash
> start_monitor
Monitor started.

> list_hunts
Hunt001
Hunt002

> list_treasures Hunt001
Treasure1
Treasure2

> calculate_score Hunt001
Score: 150

> stop_monitor
> exit
```
