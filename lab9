#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <signal.h>

pid_t child_pid;

void sigint_handler(int signo) {
    if (child_pid > 0) {
        kill(child_pid, SIGINT);  // Send SIGINT to the child
    }
}

void sigtstp_handler(int signo) {
    if (child_pid > 0) {
        kill(child_pid, SIGTSTP);  // Send SIGTSTP to the child
    }
}

void sigquit_handler(int signo) {
    if (child_pid > 0) {
        kill(child_pid, SIGQUIT);  // Send SIGQUIT to the child
    }
}

int main(int argc, char *argv[]) {
    if (argc < 2) {
        fprintf(stderr, "Usage: %s <command>\n", argv[0]);
        return 1;
    }

    signal(SIGINT, sigint_handler);
    signal(SIGTSTP, sigtstp_handler);

    int status;
    char *cmd = argv[1];

    if ((child_pid = fork()) == 0) {
        // Child process
        execvp(cmd, &argv[1]);
        perror("execvp");
        exit(1);
    } else if (child_pid < 0) {
        perror("fork");
        return 1;
    } else {
        // Parent process
        signal(SIGQUIT, sigquit_handler);
        wait(&status);
    }

    return 0;
}
