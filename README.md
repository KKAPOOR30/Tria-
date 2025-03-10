# CSCB09 Assignment 2, PID/FD Table Displayer

### Metadata
   Author: Kshitij Kapoor
   Date: 2025-03-09


### Introduction/Rationale
We have built a tool to display the tables used by the OS to keep track of open files, assignation of File Descriptors (FD), and processes. We will use files in the ```/proc``` directory for a Linux environment.

The tool takes in the following command line arguments and performs the corresponding tasks:

- Positional argument ``` PID ```: If provided, must be the first input. An integer value that represents a PID. Only data relative to that PID is displayed. If the PID does not exist an invalid pid error is printed. If no PID is provided the program finds all running PIDs
- ``` --per-process ```: Indicates that the per-process PID table should be displayed which shows all the running PIDs and their open FDs
- ``` --systemWide ```: Indicates that the system-wide table should be displayed which shows all running PIDs, their open FDs, and the filenames of the FDs 
- ``` --Vnodes ```: Indicates that the inode table should be displayed which shows all open FDs and the inode they point to. This is shown for all running processes so the FDs and inodes may repeat. Node, the same FD can point to a different inode in a different process. 
- ``` --composite ```: Indicates that the composite table should be displayed which shows all PIDs, their open FDs, the inodes, and the filenames. Note: filenames are shown last to make the table cleaner and easier to read than shown in the demo 
- ``` --summary ```: Indicates that a summary of all processes should be displayed which will show the PID and the number of FDs open ``` PID (FDs) ```: format 
- ``` --threshold=X ```: Sets a threshold of X, and displays all PIDs that have more than X FDs open. Same format as summary
- ``` --output_TXT ```: Indicates that the composite table should be written in a file called ``` compositeTable.txt ``` using ASCII. Note, if ``` --composite ``` is also called then the table will be printed in the command as well as in the file. 
- ``` --output_binary ```: Indicates that the composite table should be written in a file called ``` compositeTable.bin ``` in binary. Note, if ``` --composite ``` is also called then the table will be printed in the command as well as written to the file. 
- The program can receive multiple, arguments and the ordering repetition does not matter except for the PID positional argument. If none of ``` --per-process --systemWide --Vnode --composite --summary --threshold=X ``` are called then the program will run as if ``` --composite ``` was the only flag called.

### Description of how you solve/approach the problem
Explain in plain English and your OWN words how did you solve the problem.
Use sentences to explain the sequence of steps you took to work in this problem.


### Implementation
   4.i - Describe first in sentences how did you implement your code.
   4.ii - The modules you created and functions within them.
   4.iii - Describe the functions in sentences, e.g. this function does this and that and uses this and that sources, system calls, libraries, etc.
           DO NOT COPY the *documentation* from your code


### Include a pseudo-code of your code __OR__ flow chart or diagram of your program and corresponding functions' calls
    Refs.
    https://www.geeksforgeeks.org/what-is-pseudocode-a-complete-tutorial/
    https://en.wikipedia.org/wiki/Flowchart 

    https://draw.io





### Instructions on how to compile your code
Describe how to compile the code, dependencies with libraries.
For makefiles add details about the rules and what they do and how to use them



### Expected Results
Describe the expected functioning, functionalities and output of your code demonstrating for several cases and uses.



### Test Cases
Explain what cases you run to test your code, what unexpected outcomes you may have, e.g. if using a mistaken CLA.



## Disclaimers
Anything that must be disclaimed about your code.
E.g. my code will fail if the among of memory available on the system is less than 4GB.



### References
You must cite ALL references used while working on this project.
