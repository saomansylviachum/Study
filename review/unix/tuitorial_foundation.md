1. cat>filename cat>>filename
2. man command
3. more filename : full screen q exit space
4. grep 

| Option | Description                                    |
| ------ | ---------------------------------------------- |
| -i     | Case  insensitive search                       |
| -c     | Prints  a count of lines that match            |
| -n     | Prints  the line numbers                       |
| -l     | Prints  the filenames in which the lines match |

5. cut -c1-4 column

   cut -d" " -f1

   this command is used for selecting a number of columns from a file (or the output from another command). You can specify column numbers or choose delimiters (column separators) and choose column numbers based on the delimiters.

6. ![image-20200924220837246](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924220837246.png)

![image-20200924220901458](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924220901458.png)

7. echo: display message and variable

8. sort accounts

   uniq

9. diff cmp

10. ![image-20200924221127662](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200924221127662.png)

11. Variable

12. alias



13.  bg %JOBID - puts a job in the background

 

fg %JOBID - puts a job in the foreground

14. Mathematical:

    $[ expression ] and $(( expression )) 

| Symbol | Meaning                                                      |
| ------ | ------------------------------------------------------------ |
| +      | Addition                                                     |
| -      | Subtraction                                                  |
| *      | Multiplication                                               |
| /      | Division(Integer division)                                   |
| %      | Modulus(calculates the remainder when dividing the  numbers) |
| **     | Exponentiation(Power of)  Raise the first number to the power of the second number |





 

| Command/topic                                                | definition                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **DAY 1**                                                    |                                                              |
| **touch**                                                    | Create a new file                                            |
| **ls**                                                       | Directory listing                                            |
| **rm –r**                                                    | Remove directories                                           |
| **mkdir**                                                    | Create a directory                                           |
| **rmdir**                                                    | Remove a directory (empty)                                   |
| **man**                                                      | Online manual                                                |
| **cp**                                                       | Copy a file                                                  |
| **cd**                                                       | Change directory                                             |
| **pwd**                                                      | display the current directory                                |
| **cat**                                                      | Display a file                                               |
| **mv**                                                       | Move a file                                                  |
| **chmod**                                                    | Changes permissions      Remember the rules for chmod:     **u:**   **g:   o:**  rwx rwx rwx  r=4,   r=2,  x=1     chmod 700: rwx for user only   rwx --- ---  chmod 070: rwx for group only  --- rwx ---  chmod 007: rwx for other only  --- --- rwx |
| **wc –l**  **wc -w**   **wc -c**                             | Word count  -l: lines  -w: words  -c: characters             |
| **more**                                                     | Displays a file                                              |
| **less**                                                     | Displays a file                                              |
| **head -n**                                                  | Display the first n lines of a file                          |
| **tail -n**                                                  | Display the first n lines of a file                          |
| **clear**                                                    | Clears the screen                                            |
| **grep**                                                     | Looks for text in a file                                     |
| **find**                                                     | Look for a particular file which is …….                      |
| Wildcards  *,?, []                                           | Used to enable a command to be performed on  many files at the same time |
| Redirection/piping  >, >>, 2>  \|, tee                       |                                                              |
| Regular Expressions  ^, $, ., [], *, *                       | Used to define patterns, used by the grep  command           |
| **DAY 2**                                                    |                                                              |
| **ps, ps –e**                                                | List the processes                                           |
| **jobs**                                                     | List the jobs                                                |
| **sleep**                                                    | Sleep for a number of seconds                                |
| **bg %JOBID**                                                | Run a job in the background                                  |
| **fg %JOBID**                                                | Run a job in the foreground                                  |
| **kill PROCESSID**                                           | Kill a process                                               |
| **who**   **which**   **finger**   **users**  **sort**   **uniq**   **basename**   **dirname**  **id**   **du**   **hostname**   **tput**  **uname**   **echo**   **comm**   **cmp**  **tr**   **cut**   **find** | During the second morning, there is an  exercise where students will choose a command from this list and use the UNIX  man command to find out as much about the command as possible.      Then they will present their findings to the  other students in the class. |

# 12. Other useful commands

 

| Other commands/tips                        |                                                              |
| ------------------------------------------ | ------------------------------------------------------------ |
| history                                    | If  you use the history command it will list the commands you have used in your  UNIX session previously. If you wish to use a previously used command from  your UNIX session you can use the up arrow to locate previous commands.  Simply use the up and down arrows until you find the command you need. |
| echo                                       | Prints to the screen                                         |
| {1..100} expansion                         | Expands a range   (in this example 1 to 100)                 |
| for   while   case                         | Loop  Loop  Case statement                                   |
| read                                       | Read from the keyboard                                       |
| alias                                      | An  alias can be used to create alternative, shortened names for commands. If you  use a command (or a series of commands on one line) frequently then you can  use an alias to represent this command(s). This can be used to save you time.  For example:     alias  ll='ls -al'  alias  myalias='grep 'abc' filename \| cut -c1-4' |
| vi common shortcuts:     ESC   :wq  :q   i | Command mode  Save and quit  Quit  Insert mode               |



 