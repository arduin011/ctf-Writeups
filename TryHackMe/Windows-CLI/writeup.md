
Windows Command Line 
BASIC COMMAND LINES*	
- ver = to check the current version of the hardware
- systeminfo = to get the information from the current system
- hostname = to see who is the user
- set = to check your path from the command line
- more = to pipe the output if its too long then press space for next information
- CTRL + C = to exit the current command
- cls = to clear the command prompt screen
- help = to provide information for specific command

NETWORK CONFIGURATION*
- ipconfig = to check your network information
- ipconfig/all = more information about your network configuration
- ping "targer_name" = to see device you can interact with
- tracert = traces the network route traversed to reach the target
- nslookup = looks up a host or domain and return its Ip address
- netstat = list of connections you have been stablished
- netstat -abon 
-a displays all established connections and listening ports
-b shows the program associated with each listening port and established connection
-o reveals the process ID (PID) associated with the connection
-n uses a numerical form for addresses and port numbers

MANAGING FILES AND DISK MANAGEMENT*
- dir - Lists the contents of the current directory.
- dir /a - Includes hidden and system files in the directory listing.
- dir /s - Lists all files in the directory and subdirectories.
- dir /b - Outputs a bare list of filenames in the directory.
- cd = to target wanted directory
- tree = to visually represent the child directories and subdirectories
- type = to view the text files in the given file
- move = to move a file to another file
- mkdir NewFolder - Creates a new directory named "NewFolder".
- rmdir OldFolder - Removes the directory named "OldFolder" (must be empty).
- * (wildcard) - Matches multiple files in commands (e.g., dir *.txt to list all text files).

TASK & PROCESS MANAGEMENT*
- tasklist - Lists running processes (use filters to narrow results when needed).
- taskkill /PID <pid> - Terminates a process by its PID (use /F to force if necessary).
- tasklist /? = for more information and command related to tasklist
- tasklist /FI "imagename eq "wanted_process" = /FI is used to set the filter image name equals to your given or wanted process.

ADDITION:
- chkdsk: checks the file system and disk volumes for errors and bad sectors.
- driverquery: displays a list of installed device drivers.
- sfc /scannow: scans system files for corruption and repairs them if possible.
- /? = can be used with most commands to display a help page



