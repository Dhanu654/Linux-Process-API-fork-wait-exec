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
cat>pidcheck.c
~~~
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
~~~
gcc -o pidcheck.o pidcheck.c

./pidcheck.o














## OUTPUT

![ex2i](https://github.com/user-attachments/assets/6f37a125-0bd4-4468-9e65-efd5c0a746fa)

ps
## OUTPUT

![ex2ii](https://github.com/user-attachments/assets/1adb61e3-b290-4221-aeb5-05cc89e558b4)











## C Program to create new process using Linux API system calls fork() and exit()

cat > forkcheck.c
~~~
#include <stdio.h>
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
~~~

gcc -o forkcheck.o forkcheck.c

./forkcheck.o








## OUTPUT

![ex2iii](https://github.com/user-attachments/assets/bc933d56-a6a2-4584-be4a-41f843790410)

![ex2iv](https://github.com/user-attachments/assets/e513371b-3c67-4d4b-baa1-5b9773d1b0b1)






## C Program to execute Linux system commands using Linux API system calls exec() family

cat > execcheck2.c
~~~
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
        exit(0);
}
~~~
gcc -o execcheck2.o execcheck2.c

./execcheck2.o






















## OUTPUT

![ex2v](https://github.com/user-attachments/assets/8b2f781a-d65a-4746-836c-513f7f7dcbb8)


![ex2vi](https://github.com/user-attachments/assets/eb378356-8a5d-4334-9350-a9a928d3085a)















# RESULT:
The programs are executed successfully.
