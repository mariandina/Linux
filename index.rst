
DOCUMENTATIE LINUX
==================

Comenzi uzuale Linux Debian
---------------------------

.. image:: images/pingu.jpg

* **Ctrl-Alt-F1/F2/F3/F4/F5/F6:** Virtual Terminal
* **sudo** Execute command with Administrator rights. A user can be ``sudo`` if he is mentioned in ``etc/sudoers.d`` file.
* **su (username)**   Changing user.
* **ssh username@remote-server.com** SSH connecting command. Ex: ``ssh <remotesystem> my_command``  To run command via SSH on remote server.
* **shutdown -h / -r**  Command to shut down / restart system. Example: ``sudo shutdown -h 10:00 shutting down for scheduled maintenance.``
* **which / whereis namefile** Where program resides in filesystem.
* **pwd** Displays the present working directory
* **cd ~ or cd** Change to your home directory (short-cut name is ~ (tilde))
* **cd ..** Change to parent directory (..)
* **cd -** Change to previous directory (- (minus))
* **cd /** Changes your current directory to the root (/) directory (or path you supply)
* **ls** List contents of the present working directory. 
* **ls -a** show all including hidden content
* **ls -al** show all including permissions
* **ls -li** show all including inodes
* **tree** Displays a tree view of the filesystem. ``tree -d`` only for directories.
* **ln file1 file2** Suppose that file1 already exists, a hard link, called file2 is created. The inode number is the same for both of these files. Creating a hard link means to create a file (file 2) that should point to the same inode that file1 points to.
* **ln -s file1 file4** Soft link: file4 no longer appears to be a regular file, and it clearly points to file1 and has a different inode number. It means "create a file that should point to the file1". *If file1 is deleted (or moved): my-hard-link still points to the same contents, and is unaffected. My-soft-link now points to nothing.*
* **pushd** Pushes your starting directory onto a list
* **popd** Send you back to those directories, walking in reverse order (the most recent directory will be the first one retrieved with
* **dirs** The list of directories is displayed with the dirs command
* **do_something < input-file** A program called do_something that reads from stdin (input-file) and writes to stdout and stderr.
* **do_something > output-file** Send the output to a file named output-file.
* **com1|com2|com3** Pipeline command. Example: ``locate zip | grep bin`` list all files and directories with both "zip" and "bin" in their name.
* **locate** utilizes the database created by another program, ``updatedb``
* **?** Matches any single character. Example: ``ls ba?.out``
* ***** Matches any string of characters Example: ``ls *.out``
* **[set]** Matches any character in the set of characters, for example [adf] will match any occurrence of "a", "d", or "f"
* **[!set]** Matches any character not in the set of characters
* **find** Lists all files in the current directory and all of its subdirectories
* **find -name** (only list files with a certain pattern in their name)
* **find -iname** (also ignore the case of file names)
* **find -type** (will restrict the results to files of a certain specified type, such as **d** for directory, **l** for symbolic link or **f** for a regular file. Searching for files and directories named "gcc": ``find /usr -name gcc`` . Searching only for directories named "gcc": ``find /usr -type d -name gcc`` . Searching only for regular files named "test1": ``find /usr -type f -name test1`` . Another example is advanced find: ``find -name "*.swp" -exec rm {} ’;’`` find and removes files that ends with .swp .Finding based on time: ``find / -ctime 3`` is when the inode meta-data (i.e., file ownership, permissions, etc) last changed; it is often, but not necessarily when the file was first created. You can also search for accessed/last read (-atime) or modified/last written (-mtime) times. The number is the number of days and can be expressed as either a number (n) that means exactly that value, +n which means greater than that number, or -n which means less than that number. There are similar options for times in minutes (as in -cmin, -amin, and -mmin). Finding based on sizes: ``find / -size 0``. Example to find files greater than 10 MB in size and running a command on those files: ``find / -size +10M -exec command {}
* **sudo find / -name *pula mea"**
* **sudo rm -rf "pula mea"**
* **cat** Used for viewing files that are not very long; it does not provide any scroll-back. **cat** is short for concatenate and is one of the most frequently used Linux command line utilities. It is often used to read and print files as well as for simply viewing file contents. To view a file, use the following command: ``cat <filename>``::

          * cat file1 file2	        Concatenate multiple files and display the output;
          * cat file1 file2 > newfile	Combine multiple files and save the output into a new file.
          * cat file >> existingfile	Append a file to the end of an existing file.
          * cat > file	                Any subsequent lines typed will go into the file until CTRL-D is typed.
          * cat >> file	                Any subsequent lines are appended to the file until CTRL-D is typed.

* **tac** Used to look at a file backwards, starting with the last line. Ex. ``$ tac file $``  or  ``tac file1 file2 > newfile``
* **less** View larger files because it is a paging program; it pauses at each screenful of text, provides scroll-back capabilities, and lets you search and navigate within the file. Use / to search for a pattern in the forward direction and ? for a pattern in the backward direction.
* **tail** Used to print the last 10 lines of a file by default. Change the number of lines by doing -n 15 or just -15 if you wanted to look at the last 15 lines instead of the default.
* **head** The opposite of tail; by default it prints the first 10 lines of a file.
* **touch** Create empty file. ``touch -t 03201600 myfile.txt`` set the date and time stamp of the file.
* **mkdir** Create directory.
* **mv** Rename a file 
* **rm** Remove a file 
* **rm –f** Forcefully remove a file
* **rm –i** Interactively remove a file
* **mv** Rename a directory
* **rmdir** Remove an empty directory
* **rm -rf** Forcefully remove a directory or file recursively
* **mount /dev/sda5 /home** Attach the filesystem contained in the disk partition associated with the ``/dev/sda5`` device node, into the filesystem tree at the ``/home`` mount point. Only root user has permission to run mount. If you want it to be automatically available every time the system starts up, edit the file ``/etc/fstab`` (filesystem table).
* **mount** mount without any arguments will show all presently mounted filesystems.
* **df -Th** disk free (display information about mounted filesystems including usage statistics about currently used and available space).
* **sudo service nfs start** NFS service. Methods used for sharing data across physical systems server-client. On the SERVER, the text file ``/etc/exports`` contains the directories and permissions that a host is willing to share with other systems over NFS. An entry in this file may look like the following: ``/projects *.example.com(rw)``. This entry allows the directory ``/projects`` to be mounted using NFS with read and write (rw) permissions and shared with other hosts in the ``example.com`` domain. After modifying the ``/etc/exports`` file, you can use the ``exportfs -av`` command to notify Linux about the directories you are allowing to be remotely mounted using NFS (restarting NFS with sudo service nfs restart will also work, but is heavier as it halts NFS for a short while before starting it up again). On the CLIENT machine, if it is desired to have the remote filesystem mounted automatically upon system boot, the ``/etc/fstab`` file is modified to accomplish this. For example, an entry in the client's ``/etc/fstab`` file might look like the following:``servername:/projects /mnt/nfs/projects nfs defaults 0 0``. You can also mount the remote filesystem without a reboot or as a one-time mount by directly using the mount command: ``mount servername:/projects /mnt/nfs/projects``. If ``/etc/fstab`` is not modified, this remote mount will not be present the next time the system is restarted.
* **/proc** Contains virtual files (files that exist only in memory) that permit viewing constantly varying kernel data. cpuinfo/interrupts/meminfo/mounts/partitions/version
* **/bin** Contains executable binaries, essential commands used in single-user mode, and essential commands required by all system users.
* **ps** Produces a list of processes along with status information for the system.
* **ls** Produces a listing of the contents of a directory.
* **cp <source> <destination>** Used to copy files.
* **diff <filename1> <filename2>** Compare files and directories. Options: **-c** listing of differences that include 3 lines of context before and after the lines differing in content. **-r** Used to recursively compare subdirectories as well as the current directory **-i** Ignore the case of letters **-w** Ignore differences in spaces and tabs (white space).
* **rsync** Backup a project directory. ``rsync -r project archive-machine:archives/project`` or ``rsync sourcefile destinationfile`` .
* **gzip** The most frequently used Linux compression utility. ``gzip *`` Compresses all files in the current directory; each file is compressed and renamed with a .gz extension. ``gzip -r`` projectX Compresses all files in the projectX directory along with all files in all of the directories under projectX. ``gunzip foo`` De-compresses foo found in the file foo.gz. Under the hood, gunzip command is actually the same as ``gzip –d``.
* **bzip2** Produces files significantly smaller than those produced by gzip. ``bzip2 *`` Compress all of the files in the current directory and replaces each file with a file renamed with a .bz2 extension. ``bunzip2 *.bz2`` Decompress all of the files with an extension of .bz2 in the current directory. Under the hood, bunzip2 is the same as calling ``bzip2 -d``.
* **xz** The most space efficient compression utility used in Linux. ``xz *`` Compress all of the files in the current directory and replace each file with one with a .xz extension. ``xz foo`` Compress the file foo into foo.xz using the default compression level (-6), and remove foo if compression succeeds. ``xz -dk bar.xz`` Decompress bar.xz into  bar and don't remove bar.xz even if decompression is successful. ``xz -dcf a.txt b.txt.xz > abcd.txt`` Decompress a mix of compressed and uncompressed files to standard output, using a single command. ``xz -d *.xz`` Decompress the files compressed using xz.
* **zip** Is often required to examine and decompress archives from other operating systems. ``zip backup *`` Compresses all files in the current directory and places them in the file backup.zip. ``zip -r backup.zip ~`` Archives your login directory (~) and all files and directories under it in the file backup.zip. ``unzip backup.zip`` Extracts all files in the file backup.zip and places them in the current directory.
* **tar** Group files in an archive and then compress the whole archive at once. ``tar xvf mydir.tar`` Extract all the files in mydir.tar into the mydir directory. ``tar zcvf mydir.tar.gz mydir`` Create the archive and compress with gzip. ``tar jcvf mydir.tar.bz2 mydir`` Create the archive and compress with bz2. ``tar Jcvf mydir.tar.xz mydir``	Create the archive and compress with xz. ``tar xvf mydir.tar.gz`` Extract all the files in mydir.tar.gz into the mydir directory. You do not have to tell tar it is in gzip format.
* **dd** Disk to disk copying. Example: ``dd if=/dev/sda of=sda.mbr bs=512 count=1`` (backup MBR) or ``dd if=/dev/sda of=/dev/sdb`` An exact copy of the first disk device is created on the second disk device.
* **who**  List the currently logged-on users. **who -a** Detailed.
* **whoami** Identify the current user.
* **useradd <user>** Add user.
* **id** Informations about current user.
* **groupadd / groupdel <group>** Add/Remove a new group.
* **sudo /usr/sbin/usermod -G <group> <user>** Move user to a new group.
* **echo $SHELL** Show the value of a specific variable.
* **export VARIABLE=value (or VARIABLE=value; export VARIABLE)** Export a new variable value. Edit ``~/.bashrc`` and add the line export ``VARIABLE=value.`` Type ``source ~/.bashrc`` or just ``. ~/.bashrc`` (dot ~/.bashrc); or just start a new shell by typing bash
* **$PATH** Ordered list of directories (the path) which is scanned when a command is given to find the appropriate program or script to run. Each directory in the path is separated by colons (:). A null (empty) directory name (or ./) indicates the current directory at any given time. In the example ``:path1:path2``, there is null directory before the first colon (:). Similarly, for ``path1::path2`` there is null directory between path1 and path2. To prefix a private bin directory to your path::

   $ export PATH=$HOME/bin:$PATH
   $ echo $PATH.
   /home/me/bin:/usr/local/bin:/usr/bin:/bin/usr

* **history** History of commands in BASH. This information is stored in ``~/.bash_history``. ``HISTFILE`` stores the location of the history file. ``HISTFILESIZE`` stores the maximum number of lines in the history file. ``HISTSIZE`` stores the maximum number of lines in the history file for the current session. Ex. ``echo $HISTFILESIZE.``
* **Up/Down arrow key**	Browse through the list of commands previously executed.
* **!!** (Pronounced as bang-bang) Execute the previous command.
* **CTRL-R** Search previously used commands.
* **!**	Start a history substitution
* **!$** Refer to the last argument in a line
* **!n** Refer to the nth command line
* **!string** Refer to the most recent command starting with string
* **CTRL-L** Clears the screen
* **CTRL-D** Exits the current shell
* **CTRL-Z** Puts the current process into suspended background
* **CTRL-C** Kills the current process
* **CTRL-H** Works the same as backspace
* **CTRL-A** Goes to the beginning of the line
* **CTRL-W** Deletes the word before the cursor
* **CTRL-U** Deletes from beginning of line to cursor position
* **CTRL-E** Goes to the end of the line
* **Tab** Auto-completes files, directories, and binaries
* **alias** Define all aliases. Most often these aliases are placed in your ``~/.bashrc`` file. Ex. ``alias vi='vim'``.
* **alias projx='cd /home/staff/RandD/src'** Create an alias, projx, for ``cd /home/staff/RandD/src``
* **chown** Used to change user ownership of a file or directory. ``sudo chown root file1``
* **chgrp** Used to change group ownership. ``sudo chgrp bin file2``
* **chmod** Used to change the permissions on the file which can be done separately for owner, group and the rest of the world (often named as other.)
* **File Permission Modes and chmod** Files have three kinds of permissions::

    read (r), write (w), execute (x). These are generally represented as in rwx.
 
    These permissions affect three groups of owners: user/owner (u), group (g), and others (o).
    As a result, you have the following three groups of three permissions:
    rwx: rwx: rwx
     u:   g:   o

    Ways to use chmod: 
    Give the owner and others execute permission and remove the group write permission:

    $ ls -l test1
    -rw-rw-r-- 1 coop coop 1601 Mar 9 15:04 test1

    $ chmod uo+x,g-w test1
    $ ls -l test1
    -rwxr--r-x 1 coop coop 1601 Mar 9 15:04 test1
    
    A single digit suffices to specify all three permission bits for each entity. This digit is the sum of:

    4   if read permission is desired.
    2   if write permission is desired.
    1   if execute permission is desired.
    7   means read/write/execute,   6 means read/write,   5 means read/execute.

    $ chmod 755 test1
    $ ls -l test1

    -rwxr-xr-x 1 coop coop 1601 Mar 9 15:04 test1
* **Creating files without editor**  
.. note::

   First method is to use echo repeatedly::

    $ echo line one > myfile
    $ echo line two >> myfile
    $ echo line three >> myfile

   The second way is to use cat combined with redirection::

    $ cat << EOF > myfile 
    > line one
    > line two
    > line three
    > EOF
    $
* **Creating a New User in Linux**
.. note::

   - At the command prompt, as root type useradd <username> and press the ENTER key.
   - To set the initial password, type passwd <username>  and press the ENTER key. The New password: prompt is displayed.
   - Enter the password and press the ENTER key.
   - To confirm the password, the prompt Retype new password: is displayed.
   - Enter the password again and press the ENTER key.
   - The message passwd: all authentication tokens updated successfully. is displayed.
* **hostname** See system’s hostname
* **ifconfig** List active network interfaces
* **Network configuration files** For Debian family configuration, the basic network configuration file is ``/etc/network/interfaces``. You can type ``/etc/init.d/networking start`` to start the networking configuration. For Fedora family system configuration, the routing and host information is contained in ``/etc/sysconfig/network``. The network interface configuration script is located at ``/etc/sysconfig/network-scripts/ifcfg-eth0``. To start the networking configuration ``/etc/init.d/network start``.
* **ip addr show / ip route show** Show ip address / Show routing information.
* **ping <hostname>.** Check whether or not a machine attached to the network can receive and send data. Ex.       ``ping -c4 <hostname>/<ipaddr>``
* **route -n** View or change the IP routing table.
.. note::

     A network requires the connection of many nodes. Data moves from source to destination by passing through a series of routers and potentially across multiple networks. 
     Servers maintain routing tables containing the addresses of each node in the network. The IP Routing protocols enable routers to build up a forwarding table that correlates final destinations with the next hop addresses. 
     Route is used to view or change the IP routing table. You may want to change the IP routing table to add, delete or modify specific (static) routes to specific hosts or networks. 
     
     The table explains some commands that can be used to manage IP routing::

         Show current routing table	$ route –n
         Add static route	        $ route add -net address
         Delete static route	        $ route del -net address

* **traceroute <domain>** Print the route taken by the packet to reach the network host.
* **Networking tools** Are very useful for monitoring and debugging network problems, such as network connectivity and network traffic::

        * ethtool	Queries network interfaces and can also set various parameters such as the speed.
        * netstat	Displays all active connections and routing tables.
        * nmap	        Scans open ports on a network. Important for security analysis
        * tcpdump	Dumps network traffic for analysis.
        * iptraf	Monitors network traffic in text mode.
* **Non-graphical browsers**::

        * lynx	       Configurable text-based web browser; the earliest such browser and still in use.
        * links/elinks Based on lynx. It can display tables and frames.
        * w3m	       Newer text-based web browser with many features.
* **wget<url>** Download files.
* **curl** Allows you to save the contents of a web page to a file. Ex. ``curl -o saved.html``
* **ftp client tools** Ex. Filezilla, ftp, sftp, nvftp, yafc. Sftp uses ssh (encrypted).
* **scp <localfile> <user@remotesystem>:/home/user/** To copy a local file to a remote system.
* **echo string** Display a string on standard output (i.e., the terminal) or to place in a new file (using the > operator) or append to an already existing file (using the >> operator) ::
      
           The –e option along with the following switches is used to enable special character sequences:
           \n  represents newline
           \t  represents horizontal tab
           echo is particularly useful for viewing the values of environment variables (built-in shell variables).
           For example, echo $USERNAME will print the name of the user who has logged into the current terminal.
           * echo string > newfile	  The specified string is placed in a new file.
           * echo string >> existingfile  The specified string is appended to the end of an already existing file.
           * echo $variable	          The contents of the specified environment variable are displayed.

* **sed** A powerful text processing tool. Can filter text as well as perform substitutions in data streams, working like a churn-mill::

          * sed -e command <filename> Specify editing commands at the command line, operate on file and put the 
          output on terminal. Allows you to specify multiple editing commands simultaneously at the command line.

          * sed -f scriptfile <filename> Specify a scriptfile containing sed commands, operate on file and put output on term.
          The table explains some basic operations, where pattern is the current string and replace_string is the new string:
          
          * sed s/pattern/replace_string/ file	Substitute first string occurrence in a line
          * sed s/pattern/replace_string/g file	Substitute all string occurrences in a line
          * sed 1,3s/pattern/replace_string/g file Substitute all string occurrences in a range of lines
          * sed -i s/pattern/replace_string/g file Save changes for string substitution in the same file
          
          You must use the -i option with care, because the action is not reversible. 
          It is always safer to use sed without the –i option and then replace the file yourself:
          * sed s/pattern/replace_string/g file1 > file2`
          The above command will replace all occurrences of pattern with replace_string in file1 and move the contents to file2. 
          The contents of file2 can be viewed with cat file2. 
          If you approve you can then overwrite the original file with mv file2 file1.

          * Example: To convert 01/02/… to JAN/FEB/…
          sed -e 's/01/JAN/' -e 's/02/FEB/' -e 's/03/MAR/' -e 's/04/APR/' -e 's/05/MAY/' \ 
          -e 's/06/JUN/' -e 's/07/JUL/' -e 's/08/AUG/' -e 's/09/SEP/' -e 's/10/OCT/' \
          -e 's/11/NOV/' -e 's/12/DEC/'
* **awk** Is used to extract and then print specific contents of a file and is often used to construct reports. It is a powerful utility and interpreted programming language, It is used to manipulate data files, retrieving, and processing text. It works well with fields (containing a single piece of data, essentially a column) and records (a collection of fields, essentially a line in a file)::

          * awk ‘command’ var=value file	    Specify a command directly at the command line
          * awk -f scriptfile var=value file        Specify a file that contains the script to be executed along with f
          * awk '{ print $0 }' /etc/passwd	    Print entire file
          * awk -F: '{ print $1 }' /etc/passwd	    Print first field (column) of every line, separated by a space
          * awk -F: '{ print $1 $6 }' /etc/passwd   Print first and sixth field of every line
* **sort** Is used to rearrange the lines of a text file either in ascending or descending order, according to a sort key. ``sort <filename>`` Sort the lines in the specified file  ``cat file1 file2 | sort`` Append the two files, then sort the lines and display the output on the terminal. ``sort -r <filename>`` Sort the lines in reverse order. When used with the -u option, sort checks for unique values after sorting the records (lines). It is equivalent to running uniq (which we shall discuss) on the output of sort.
* **uniq** is used to remove duplicate lines in a text file and is useful for simplifying text display. uniq requires that the duplicate entries to be removed are consecutive. Therefore one often runs sort first and then pipes the output into uniq; if sort is passed the -u option it can do all this in one step. To remove duplicate entries from some files, use the following command: ``sort file1 file2 | uniq > file3`` or sort -u ``file1 file2 > file3``. To count the number of duplicate entries, use the following command: ``uniq -c filename``.
* **paste** can be used to combine fields (such as name or phone number) from different files as well as combine lines from multiple files. For example, line one from file1 can be combined with line one of file2, line two from file1 can be combined with line two of file2, and so on. To paste contents from two files one can do: ``$ paste file1 file2``. The syntax to use a different delimiter is as follows: ``$ paste -d, file1 file2``. Common delimiters are 'space', 'tab', '|', 'comma', etc.
* **join** To combine two files on a common field, at the command prompt type ``join file1 file2`` and press the Enter key::

          $ cat phonebook             $ cat directory                                       $ join phonebook directory
            555-123-4567 Bob            555-123-4567 Anytown                                  555-123-4567 Bob Anytown
            555-231-3325 Carol          555-231-3325 Mytown         Result of joining:        555-231-3325 Carol Mytown
            555-340-5678 Ted            555-340-5678 Yourtown                                 555-340-5678 Ted Yourtown
            555-289-6193 Alice          555-289-6193 Youngstown                               555-289-6193 Alice Youngstown
* **split** Is used to break up (or split) a file into equal-sized segments for easier viewing and manipulation, and is generally used only on relatively large files. By default split breaks up a file into 1,000-line segments. The original file remains unchanged, and set of new files with the same name plus an added prefix is created. By default, the x prefix is added. To split a file into segments, use the command ``split infile``.To split a file into segments using a different prefix, use the command ``split infile <Prefix>``::

             To demonstrate the use of split, we'll apply it to an american-english dictionary file of over 99,000 lines:
             $ wc -l american-english
             99171 american-english
             where we have used the wc program to report on the number of lines in the file. Then typing:
             $ split american-english dictionary
             will split the american-english file into equal-sized segments named 'dictionary'.
             $ ls -l dictionary*
             -rw-rw-r 1 me me 8552 Mar 23 20:19 dictionaryab
             -rw-rw-r 1 me me 8653 Mar 23 20:19 dictionaryaa
* **Regular expressions** are text strings used for matching a specific pattern, or to search for a specific location, such as the start or end of a line or a word. Regular expressions can contain both normal characters or so-called metacharacters, such as * and $ ::

             * .(dot)	Match any single character
             * a|z	Match a or z
             * $	Match end of string
             * *	Match preceding item 0 or more times

             Using Regular Expressions and Search Patterns
             
             Consider the following sentence: the quick brown fox jumped over the lazy dog
             Some of the patterns that can be applied to this sentence are as follows:
             
             1) a..	matches azy
             2) b.|j.	matches both br and ju
             3) ..$	matches og
             4) l.*	matches lazy dog
             5) l.*y	matches lazy
             6) the.*	matches the whole sentence
* **grep** is extensively used as a primary text searching tool. It scans files for specified patterns and can be used with regular expressions as well as simple strings as shown in the table::

             grep [pattern] <filename>	     Search for a pattern in a file and print all matching lines
             grep -v [pattern] <filename>    Print all lines that do not match the pattern
             grep [0-9] <filename>	     Print the lines that contain the numbers 0 through 9
             grep -C 3 [pattern] <filename>  Print context of lines (3 lines here above and below the pattern) for matching the pattern.

* **tr** Translate specified characters into other characters or to delete them. ``tr [options] set1 [set2]``.The first, designated set1 in the example, lists the characters in the text to be replaced or removed. The second, set2, lists the characters that are to be substituted for the characters listed in the first argument. Sometimes these sets need to be surrounded by apostrophes (or single-quotes (')) in order to have the shell ignore that they mean something special to the shell. It is usually safe (and may be required) to use the single-quotes around each of the sets::
  
             For example, suppose you have a file named city containing several lines of text in mixed case. 
             To translate all lower case characters to upper case, at the command prompt 
             type cat city | tr a-z A-Z and press the Enter key.
             * $ tr abcdefghijklmnopqrstuvwxyz ABCDEFGHIJKLMNOPQRSTUVWXYZ Convert lower case to upper case
             * $ tr '{}' '()' < inputfile > outputfile	                  Translate braces into parenthesis
             * $ echo "This is for testing" | tr [:space:] '\t' 	  Translate white-space to tabs
             * $ echo "This   is   for    testing" | tr -s [:space:]      Squeeze repetition of characters using -s
             * $ echo "the geek stuff" | tr -d 't'	                  Delete specified characters using -d option
             * $ echo "my username is 432234" | tr -cd [:digit:]	  Complement the sets using -c option
             * $ tr -cd [:print:] < file.txt	                          Remove all non-printable character from a file
             * $ tr -s '\n' ' ' < file.txt	                          Join all the lines in a file into a single line
* **tee** takes the output from any command, and while sending it to standard output, it also saves it to a file. In other words, it "tees" the output stream from the command: one stream is displayed on the standard output and the other is saved to a file. For example, to list the contents of a directory on the screen and save the output to a file, at the command prompt type ``ls -l | tee newfile`` and press the Enter key.
* **wc** word count counts the number of lines, words, and characters in a file or list of files::

             To print the number of lines contained in a file, at the command prompt type wc -l filename.

             * –l display the number of lines.
             * -c display the number of bytes.
             * -w display the number of words.
* **cut** manipulating column-based files and is designed to extract specific columns. The default column separator is the tab character. A different delimiter can be given as a command option. For example, to display the third column delimited by a blank space, at the command prompt type ``ls -l | cut -d" " -f3`` and press the Enter key.
* **less** view the contents of such a large file, scrolling up and down page by page without the system having to place the entire file in memory before starting. This is much faster than using a text editor. Viewing the file can be done by typing either of the two following commands: ``$ less <filename>`` or ``$ cat <filename> | less``
* **head** reads the first few lines of each named file (10 by default) and displays it on standard output. For example, If you want to print the first 5 lines from atmtrans.txt, use the following command: ``$ head –n 5 atmtrans.txt`` .
* **tail** Prints the last few lines of each named file and displays it on standard output. By default, it displays the last 10 lines. You can give a different number of lines as an option. tail is especially useful when you are troubleshooting any issue using log files as you probably want to see the most recent lines of output::

             For example, to display the last 15 lines of atmtrans.txt, use the following command:
             $ tail -n 15 atmtrans.txt
             (You can also just say tail -15 atmtrans.txt.) 
             To continually monitor new output in a growing log file:
             $ tail -f atmtrans.txt
             This command will continuously display any new lines of output in atmtrans.txt as soon as they appear. 
             Thus it enables you to monitor any current activity that is being reported and recorded.

* **strings** Is used to extract all printable character strings found in the file or files given as arguments. It is useful in locating human readable content embedded in binary files: for text files one can just use grep. For example, to search for the string my_string in a spreadsheet: ``$ strings book1.xls | grep my_string``
* **z command family** To directly view compressed files::
         
             $ zcat compressed-file.txt.gz	                To view a compressed file
             $ zless <filename>.gz or $ zmore <filename>.gz	To page through a compressed file
             $ zgrep -i less test-file.txt.gz	                To search inside a compressed file
             $ zdiff filename1.txt.gz filename2.txt.gz	        To compare two compressed files

* **bash scripts** ::

             $ cat > exscript.sh
             #!/bin/bash
             echo "HELLO"
             echo "WORLD"

             and press ENTER and CTRL-D to save the file, or just create exscript.sh in your favorite text editor. 
             Then, type chmod +x exscript.sh to make the file executable. 
             (The chmod +x command makes the file executable for all users.) 
             You can then run it by simply typing ./exscript.sh

             !/bin/bash
             # Interactive reading of variables
             echo "ENTER YOUR NAME"
             read sname
             # Display of variable values
             echo $sname


install apt-file to find dependency package that miss *"sudo apt-file find ********"*
pip install wheel
yum provides in centos


touch .gitignore
vim gitignore
add name of file that i want to ignore in git
git add .gitignore
git commit -m s-a efectuat ceva








          







