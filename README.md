# EXPT.NO-8-IMPLEMENTATION-OF-GO-BACK-N-PROTOCOL-SLIDING-WINDOW
# AIM
To write and execute a program for Go-Back-N protocol.
# EQUIPMENTS REQUIRED
  1. Personal Computer
  2. Turbo C Compiler
# PROCEDURE
1.	Connect two computers in Wired/Wireless LAN.
2.	Make sure that two computers are in one network and could able to ping each other.
3.	In the codeblocker open new c file and type the program.
4.	In the menu choose->Project->Properties->Project Build options->Linker settings->Add netproto and pthread.
5.	Execute the program in both server and client.
6.	Enter the IP address of the remote machine, port address of both local & remote machine and error rate.
7.	Choose the file and verify the go back protocol operation.

# PROGRAM
```
#include <stdio.h>
#define WINDOW_SIZE 4   // Assume 7 frames of data are to be sent using GO-BACK-N ARQ
void main()
{
    int i, window_start = 1, ack, n;
    char frame[20][10];   // Increased size to handle up to 20 frames safely
    printf("SLIDING WINDOW PROTOCOL\n");
    printf("Enter the number of frames: ");
    scanf("%d", &n);
    for (i = 1; i <= n; i++)
    {
        printf("Content for frame %d: ", i);
        scanf("%s", frame[i]);
    }
    while (window_start <= n)
    {
        printf("\nSending frames: ");
        for (i = window_start; i < window_start + WINDOW_SIZE && i <= n; i++)
        {
            printf("Frame %d ", i);
        }
        printf("\nEnter the frame number which no ACK (or 0 for all ACK): ");
        scanf("%d", &ack);
        if (ack == 0)
        {
            printf("\nAll frames acknowledged. Moving window forward.\n");
            window_start += WINDOW_SIZE;
        }
        else
        {
            printf("\nNo acknowledgement for frame %d.\n", ack);
            printf("Resending frames starting from frame %d:\n", ack);
            window_start = ack;
        }
    }
    printf("\nAll frames sent successfully.\n");
}
```
# OUTPUT

<img width="1475" height="750" alt="image" src="https://github.com/user-attachments/assets/eb819456-afaf-481f-8836-dd1470a70a0c" />

# RESULT
Thus the Go-Back-N protocol-Sliding Window was implemented and the output is verified successfully.
