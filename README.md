# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```

## OUTPUT
![Screenshot 2024-03-27 142149](https://github.com/Lokeshreddya31/Linux-Process-API-fork-wait-exec/assets/144870682/f85ac12d-4951-4119-a08c-c507dca12029)


## C Program to create new process using Linux API system calls fork() and exit()
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
```

## OUTPUT
![Screenshot 2024-03-27 142213](https://github.com/Lokeshreddya31/Linux-Process-API-fork-wait-exec/assets/144870682/5c47cb25-fc47-4d27-b152-79417b517c2f)


## C Program to execute Linux system commands using Linux API system calls exec() family
```c
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```

## OUTPUT
![Screenshot 2024-03-27 142438](https://github.com/Lokeshreddya31/Linux-Process-API-fork-wait-exec/assets/144870682/47ac313f-71ad-4b6b-acd2-9c1f8cff79c1)
![Screenshot 2024-03-27 142504](https://github.com/Lokeshreddya31/Linux-Process-API-fork-wait-exec/assets/144870682/4cd969b2-1f4e-4a99-9ba4-2d84c7e630f0)
![Screenshot 2024-03-27 142540](https://github.com/Lokeshreddya31/Linux-Process-API-fork-wait-exec/assets/144870682/89c91a87-3676-4aa0-a23e-9fadd01daf9f)




# RESULT:
The programs are executed successfully.
