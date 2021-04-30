#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
 
int main(void) {
  for(int i = 1; i < 4; i++) {
    pid_t pid = fork();
 
    if(pid == 0) {
    char name[20];
      printf("Enter your name: "); 
      fgets(name,20,stdin);
      printf("%s",name);
     printf("Child process => PPID=%d, PID=%d\n", getppid(), getpid());

     exit(0);
    }
    else  {
      printf("next name……\n");
      wait(NULL);
      printf("Job is done!.\n");
    }
  }
 
  return EXIT_SUCCESS;
}

