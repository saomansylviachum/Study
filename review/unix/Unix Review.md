# Unix Review

what is operating system

what is the architecture of unix?



| Enlist common shells with their indicators                   | 1    |                                                              | Bourne Shell (sh), C Shell (csh), Bourne Again shell (Bash), Enhanced C shell (tcsh), Z Shell (zsh), Korn Shell (ksh) |
| ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| List a few significant features of UNIX                      | 1    |                                                              | Machine independent, Portability, Multi-user operations, Unix Shells, Hierarchical file system, Pipes and filters, Background processors, Utilities, Development tools |
| What is the general format of UNIX command syntax?           |      |                                                              | Command (-argument) (-argument) (-argument) (filename)       |
| Differentiate between absolute and related path?             |      |                                                              | Absolute path refers to the exact path as defined from the root directory whereas, related path refers to the path related to the current locations. |
| What is the fork() system call?                              | 1    | child process:0 parent process: child pid                    | "The command used to create a new process from an existing process is called fork(). The main process is called the parent process and new process is called child process. The parent gets the child process is returned and the child gets 0. The returned values are used to check which process which code executed. The returned values are used to check which process is executed." |
| Define a process group                                       | 1    | getgrp                                                       | A collection of one or more processes is called a process group. There is a unique process id for each process group. The function getpgrp returns the process group ID for the calling process. |
| What do chmod, chown, chgrp commands do?                     |      |                                                              | "Following are the purposes of the given UNIX commands; chmod changes the permission set of the file. chown changes the ownership of the file. chgrp changes the group of the file." |
| How would you display the last line of a file?               | 1    |                                                              | The last line of a file is displayed using either “tail” or “sed” commands. Example: tail -1 README.txt (displays the last line of the file) |
| What are the pros of executing processes in the background?  |      | ambersand                                                    | The main advantage is to execute processes in the background is to get the possibility to execute some other process without waiting for the previous process to get completed. The symbol “&” at the end of the process tells to the shell to execute given a command in the background. |
| Which command should you use to find the remaining disk space in UNIX server? |      | du: file/dir size                                            | The command df -kl is used to get a detailed description of disk space usage. |
| What is the UNIX command to confirm a remote host is alive or not? | 1    |                                                              | You can use either ping or telnet to confirm a remote host is alive or not. |
| Which command is used to find whether the system is 32 bit or 64 bit? |      |                                                              | arch or uname -a can be used for the required process.       |
| What does the “echo” command do?                             | 1    |                                                              | The echo command outputs the strings it is being passed as arguments. |
| What is meant by u-area?                                     | 不懂 |                                                              | The area contains information specific to the process and is only manipulated by the kernel. It contains the private data unique to the process allocated to u-area. |
| Explain piping                                               |      |                                                              | Piping(\|) is used to combine two or more commands together where the output of the first command serves as the input of the second command, and so on. |
| Can you explain what does the Kernel do?                     | 1    |                                                              | "The Kernel is the heart of the operating system. It does not deal directly with the user but rather act as a separate interactive program for users logged in. It is responsible for the following functions: Interaction with the hardware Memory management File management Task scheduling. Computer resources Allotment of resources to different tasks and users." |
| What can you tell about shell variables?                     |      | set:显示环境变量let:计算式export 新增修改环境变量            | "A variable is like a name. It is defined as a character string to which a value is assigned, where values could be the number, text, filename, etc. The shell maintains the set of internal variables as well as enables deletion, assignment, and the creation of variables. Thus, a shell variable is a special variable that is set by the shell and is required by the shell in order to function correctly. Some of these variables are environment variables whereas others are local variables. So, the shell variables are a combination of identifiers and assigned values that exist within the shell. These variables are local to the shell in which they are defined as well as they work in a particular way. They may have default value or values can be assigned manually by using appropriate assignment command. To define a shell variable, the set command is used. To delete a shell variable, the unset command is used." |
| Define inode                                                 | 1    |                                                              | "When a file is created inside a directory, it accesses the two attributes, namely, file name and inode number. The file name is first mapped with Inode number and stored in the table and then this Inode number serves as a medium to access Inode. Thus, an inode can be defined as an entry created and set aside on a section of the disk for a file system. It serves as a data structure and nearly stores each information that is required to be known about a file. This information usually includes the following details; The File location on the disk The Size of the file The Device Id and Group Id The File mode information The File protection flags The Access privileges for owner, group. The Timestamps for file creation, modifications" |
| Explain Superblock in UNIX                                   |      | **超级块中的数据其实就是文件卷的控制信息部分，也可以说它是卷资源表，**有关文件卷的大部分信息都保存在这里。例如：硬盘分区中每个block的大小、硬盘分区上一共有多少个block group、以及每个block group中有多少个inode。<br/>对于super block的结构和涵义可以通过查看/usr/include/linux/ext3_fs.h文件： | "A SuperBlock is essentially a program that contains a record of specific file systems. Characteristics such as the block size, the empty and the filled blocks and their respective counts, the size and location of the inode tables, the disk block map, and usage information, and the size of the block groups are available in a superblock. There are basically two types of superblocks which are the following; Default superblock: It has its existence always as a fix offset from the beginning of the system’s disk partition. Redundant superblock: It is referenced when the default superblock is affected by a system crash or some errors." |
| Can you tell me something about wildcard interpretation?     |      |                                                              | "Wildcard characters are some special kind of characters that represent one or more other characters. Wildcard interpretation comes into the picture when a command-line contains these characters. In this case, when the pattern matches the input command, these characters are replaced by a sorted list of files. The Asterisk(*) and Question mark(?) are usually used as wildcard characters to set up a list of files while processing." |

## File system

UNIX File System is based on a continuous structure



**/** This is the root directory which should contain only the directories needed at the top level of the file structure. 

**/bin** This is where the executable files are located. They are available to all users. 

**/dev** Stores device files 

**/****etc** Supervisor directory commands, configuration files, disk configuration files, valid user lists, groups, Ethernet, hosts,     where to send critical messages. 

**/home** Contains the home directory for users and other accounts. 

**/tmp** Holds temporary files used between system boots and its contents maybe deleted during a reboot 

**/usr** Used for miscellaneous purposes, or can be used by many users. Includes additional commands, shared files, library files, and others 

**/var** Typically contains variable-length files such as log and print files and any other type of file that may contain a variable amount of data

2. how many types of files in unix

3. In UNIX each file is uniquely identified by its name and by a index node number called** **inode****.**

4. what is hard link and softlin

   A **hard link** associates a name with a file. All files must have at least one hard link giving the original name for each file. 

   Creating an extra hard link has the effect of giving one file multiple names, all of which independently connect to the same data on the disk, none of which depends on any of the others. The inode number is the same because the hard links point to the same file on disc. Hard links are an ideal way to make a dynamic copy that occupies no space of its own.Directories have multiple hard links because each file inside it references the directory.

   A symbolic link, also called a soft link, is a special kind of file that points to another file, much like a shortcut in Windows. Unlike a hard link, a symbolic link does not point to the data in the target file. It simply points to another entry somewhere in the file system. When you delete a target file, symbolic links to that file become unusable, whereas hard links preserve the pointer to the contents of the file. 

5. what is globbing

   •Globbing refers to file and directory pattern expansion

   •The shell will interpret wildcards and expand them with matching files before running the command

   •Useful to perform a command on several files with similar names

   ![image-20200923214332956](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923214332956.png)

   chmod

   chmod u+x

   ![image-20200923214418422](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923214418422.png)rwx

   

## Redirection

what is piping? combined

tee filename

![image-20200923214515089](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923214515089.png)

![image-20200923215029678](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923215029678.png)

## Pattern Matching and Searching

grep [-options] pattern filename

regular expression

![image-20200923215300720](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923215300720.png)

![image-20200923215308406](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200923215308406.png)





cloud

user authentication of using the application, some other features such as connecting smtp sever to send emails, logging in



AIA

```java

public void removeAccount(int accountId) {
		EntityManager em=emf.createEntityManager();
		Account account=em.find(Account.class, accountId);
		if (account==null) {
			return;
		}
		em.getTransaction().begin();
		Query query=em.createQuery("Select e from User e where e.account.account_id=:accountId",User.class);
		query.setParameter("accountId", accountId);
		User user=(User) query.getSingleResult();
		user.setAccount(null);
		em.remove(account);
		em.getTransaction().commit();
		em.close();
	}


public void addUser(User user) {
		EntityManager em=emf.createEntityManager();
		em.getTransaction().begin();
		em.persist(user);
		em.getTransaction().commit();
		em.close();
	}
	public void removeUser(int userId) {
		EntityManager em=emf.createEntityManager();
		User user=em.find(User.class, userId);
		if (user==null) {
			return;
		}
		em.getTransaction().begin();
		em.remove(user);
		em.getTransaction().commit();
		em.close();
	}
	public  void update(User user) {
		EntityManager em=emf.createEntityManager();
		User userToUpdate=em.find(User.class, user.getUser_id());
		em.getTransaction().begin();
		if (user.getAccount()!=null) {
			userToUpdate.setAccount(em.merge(user.getAccount()));
		}
		userToUpdate.setPassword(user.getPassword());
		userToUpdate.setUsername(user.getUsername());
		em.persist(userToUpdate);
		em.getTransaction().commit();
		em.close();
	}
	public User findUserByUserId(int userId) {
		EntityManager em=emf.createEntityManager();
		User user=em.find(User.class, userId);
		return user;
	}
	public List<User> listAll() {
		EntityManager em=emf.createEntityManager();
		Query query=em.createQuery("Select e from User e");
		List<User> users=query.getResultList();
		return users;
	}
	public User findUserByAccountId(int accountId) {
		EntityManager entityManager=emf.createEntityManager();
		entityManager.getTransaction().begin();
		Query query=entityManager.createQuery("Select e from User e where e.account.account_id=:accountId",User.class);
		query.setParameter("accountId", accountId);
		User user=(User) query.getSingleResult();
		entityManager.close();
		return user;
	}
	public User findUserByUserName(String username) {
		EntityManager entityManager=emf.createEntityManager();
		entityManager.getTransaction().begin();
		Query query=entityManager.createQuery("Select e from User e where e.username=:username",User.class);
		query.setParameter("username", username);
		User user=(User) query.getSingleResult();
		entityManager.close();
		return user;
	}
```

