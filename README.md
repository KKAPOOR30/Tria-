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
- Step 1: Understanding the problem, needed to read the requirements carefully and thoroughly before beginning to work on it.
- Step 2: Researching, trying to see what data I need, where to get it from, and what to use to get and store this data. Read through multiple man pages, including ones provided on course website, did external research on the internet, asked TAs for advice, etc.
- Step 3: Coming up with a solution, because of the nature of the problem, I decided to first store all the required data and then print it depending on the input later. Since it was unknown how much data is to be stored, I used linked lists and created my own CDTs for FDs and PIDs to meet my storing and printing needs.
- Step 4: Reading input, wrote the part of the tool that will read the command line prompts and run the required code depending on the input.
- Step 5: Getting the data, used the ``` /proc, /proc/<PID>/ ``` directories, and the ``` /proc/<PID>/fd ``` files to read the data. Used many IO funtions and used the ``` stat(), readlink() ``` functions to extract the data. The data was then stored using the CDTs that were created
- Step 6: Displaying data, whatever data was to be displayed had already been stored, and what was to be displayed was already read and understood, from the inputs so helper functions were made for each of the display tables that will be discussed later
- Step 7: Freeing all the allocated data, all the data that was stored in CDTs and linked lists had to be released
- Step 8: Testing, the code was run multiple times using many different types of inputs and any bugs and issues found were fixed.

### Implementation
   4.i - Describe first in sentences how did you implement your code.
   4.ii - The modules you created and functions within them.
   4.iii - Describe the functions in sentences, e.g. this function does this and that and uses this and that sources, system calls, libraries, etc.
           DO NOT COPY the *documentation* from your code


### Include a pseudo-code of your code
```
def main(int argc, char**argv){
  initializing variables
  
  for (arguments){
    Read arguments and process them
    change initialized values based on inputs
    check for invalid inputs
    #For example, if --composite is a parameter, make the composite variable true so we later know, composite is to be displayed
  }

  if (pid provided){
    Get data for that pid using get_single_data(pid)
  }  otherwise {
    get all pid data using get_all_data()
  }

  if (per-process is true) {
    run print_per(head) function
  } 
  if (systemWide is true) {
    run print_system(head) function
  } ... Similarly do the same for the other input flags ...

  free all the allocated memory
}
```
    
### Instructions on how to compile your code
A makefile is provided that should take care of all compilations.
- ``` make all ``` will compile the .c file and create/compile the showTables executable file
- ``` make clean ``` can be used to delete all the object file and the executable file made by the ``` make all ``` command.
- Once the executable is created it can be run by using the ``` ./showTables ``` command and any flags as stated above can be added after with spaces in between 


### Expected Results
Describe the expected functioning, functionalities and output of your code demonstrating for several cases and uses.



### Test Cases
Explain what cases you run to test your code, what unexpected outcomes you may have, e.g. if using a mistaken CLA.



## Disclaimers
Anything that must be disclaimed about your code.
E.g. my code will fail if the among of memory available on the system is less than 4GB.



### References
You must cite ALL references used while working on this project.
