# File-Permissions-in-Linux
We will be using Linux commands to configure authorization. This means we will give/remove users for access to resources. 
Check file and directory details

researcher2@6d133065cf68:~$ pwd
/home/researcher2

Describe the permissions string

esearcher2@6d133065cf68:~$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 21:25 .
drwxr-xr-x 1 root        root          4096 Nov 10 20:46 ..
-rw------- 1 researcher2 research_team   17 Nov 10 21:27 .bash_history
-rw-r--r-- 1 researcher2 research_team  220 May  7  2026 .bash_logout
-rw-r--r-- 1 researcher2 research_team 3574 Nov 10 20:46 .bashrc
-rw-r--r-- 1 researcher2 research_team 3574 Nov 10 20:46 .profile
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 projects
researcher2@6d133065cf68:~$ ls -a
.   .bash_history  .bashrc   projects
..  .bash_logout   .profile
esearcher2@6d133065cf68:~$ cd /home/researcher2/projects
researcher2@6d133065cf68:~/projects$ la -la
-bash: la: command not found
researcher2@6d133065cf68:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 21:25 ..
-rw--w---- 1 researcher2 research_team   46 Nov 10 20:46 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Nov 10 20:46 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 10 20:46 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_t.txt

Change file permissions
researcher2@6d133065cf68:~/projects$ ls -l
total 20
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Nov 10 20:46 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 10 20:46 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_t.txt
researcher2@6d133065cf68:~/projects$ chmod o-w project_k.txt
researcher2@6d133065cf68:~/projects$ ls -l
total 20
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 drafts
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Nov 10 20:46 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_t.txt
researcher2@6d133065cf68:~/projects$ chmod g-r-w project_m.txt
researcher2@6d133065cf68:~/projects$ ls -l
total 20
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 drafts
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_k.txt
-rw------- 1 researcher2 research_team   46 Nov 10 20:46 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_t.txt

Change file permissions on a hidden file

researcher2@6d133065cf68:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 21:25 ..
-rw--w---- 1 researcher2 research_team   46 Nov 10 20:46 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 drafts
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_k.txt
-rw------- 1 researcher2 research_team   46 Nov 10 20:46 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_t.txt
researcher2@6d133065cf68:~/projects$ chmod u+r-w,g+r-w .project_x.txt
researcher2@6d133065cf68:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 21:25 ..
-r--r----- 1 researcher2 research_team   46 Nov 10 20:46 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 drafts
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_k.txt
-rw------- 1 researcher2 research_team   46 Nov 10 20:46 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Nov 10 20:46 project_t.txt

Change directory permissions

researcher2@6d133065cf68:~/projects/drafts$ cd /home/researcher2/projects/drafts 
researcher2@6d133065cf68:~/projects/drafts$ ls -la
total 8
drwx--x--- 2 researcher2 research_team 4096 Nov 10 20:46 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 ..
researcher2@6d133065cf68:~/projects/drafts$ chmod g-x /home/researcher2/projects/drafts
researcher2@6d133065cf68:~/projects/drafts$ ls -la
total 8
drwx------ 2 researcher2 research_team 4096 Nov 10 20:46 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 ..
researcher2@6d133065cf68:~/projects/drafts$ ls -l
total 0
researcher2@6d133065cf68:~/projects/drafts$ ls -a
.  ..
researcher2@6d133065cf68:~/projects/drafts$ ls -la
total 8
drwx------ 2 researcher2 research_team 4096 Nov 10 20:46 .
drwxr-xr-x 3 researcher2 research_team 4096 Nov 10 20:46 ..

Summary
We were successfully able to use basic Linux Bash shell commands to examine files and directory files, change permissions on files, and change permissions on directories.
