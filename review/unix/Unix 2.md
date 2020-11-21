# Unix 2

## Job Control

•A process is an instance of a running command or program.

•[CTRL] z pauses, or stops, the foreground process.

•[CTRL] c kills, or terminates, the foreground process



### Background process

•A background process does not interrupt your session.

•& on the right side of the command allows the process to run in the background

•nohup prevents a background process from aborting when you exit the shell.

![image-20200924215434064](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924215434064.png)

•ps –f full list of all your processes

•jobs – lists all background and stopped processes 

- bg %jobID
- fg %jobID



## System