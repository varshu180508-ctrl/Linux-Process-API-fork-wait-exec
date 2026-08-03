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

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
#include<stdio.h>
#include<unistd.h>
#include<sys/wait.h>
int main(){
    int pid = fork();
    if(pid == 0){
        printf("I am child, my PID is %d\n",getpid());
        printf("My parent PID is: %d\n",getppid());
        sleep(2);
    }
    else{
        printf("I am parent, my PID is %d\n",getpid());
        wait(NULL);
    }
}
```



##OUTPUT

<img width="217" height="176" alt="Screenshot 2026-08-03 144432" src="https://github.com/user-attachments/assets/07ebece2-be21-4c58-945e-b10a033bd69d" />







## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family



#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
    pid_t pid;
    int status;

    pid = fork();

    if (pid == 0)
    {
        printf("Running ps with execlp\n");
        execl("/bin/ps", "ps", "ax", NULL);

        // Executes only if execl() fails
        perror("execl");
        exit(1);
    }
    else if (pid > 0)
    {
        wait(&status);

        if (WIFEXITED(status) && WEXITSTATUS(status) == 0)
        {
            printf("child exited successfully\n");
        }
        else
        {
            printf("child did not exit successfully\n");
        }
    }
    else
    {
        perror("fork");
    }

    return 0;
}






















##OUTPUT


<img width="367" height="287" alt="Screenshot 2026-08-03 144808" src="https://github.com/user-attachments/assets/5ebadeec-7684-434f-b1fe-7eca6a9e54ab" />















<img width="392" height="281" alt="Screenshot 2026-08-03 144846" src="https://github.com/user-attachments/assets/a8e0ec97-4f6f-4c8c-947a-3f01b37879b0" />


















# RESULT:
The programs are executed successfully.
