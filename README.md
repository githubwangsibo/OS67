OS67
===============================
OS67 is a unix-like toy kernel, which comes with some user routines.

###BUILD REQUIREMENTS
Platform: Linux
* make
* nasm
* gcc
* binutils(ld, objcopy)
* mkfs
* bochs
     
###HOW TO COMPILE  
    git clone https://github.com/LastAvenger/OS67.git
    cd OS67
    make init   # only for first time
    make fs     # build root file system and user routines, root privilege required
    make        # build kernel
    make run    # run with bochs

###SYSCALLS LIST
    int _fork();
    int _exit();
    int _wait();
    int _pipe(int *fd);
    int _read(int fd, char *addr, uint32_t n);
    int _kill(int pid);
    int _exec(char *path, char **argv);
    int _fstat(int fd, struct stat *stat);
    int _chdir(char *path);
    int _dup(int fd);
    int _getpid();
    int _sleep(uint32_t sec);
    int _uptime();
    int _open(char *path, uint32_t mode);
    int _write(int fd, char *addr, uint32_t n);
    int _mknod(char *path, uint32_t di);
    int _unlink(char *path);
    int _link(char *old, char *new);
    int _mkdir(char *path);
    int _close(int fd);

###USER ROUTINES LIST
* sh: a simple shell, support IO redirect and pipe
* ls: list files
* cat: read from stdin and send it to stdout
* mkdir: make up diectroy
* rm: remove file
* ...

####WITRE YOUSELF A USER ROUTINES
* add a new file in `usr/`: `touch usr/newroutines.c`
* add a new value to `UPROGS` varible in `Makefile` as follow:

     - UPROGS =  bin/cinit bin/sh bin/cat bin/ls bin/mkdir bin/rm
     + UPROGS =  bin/cinit bin/sh bin/cat bin/ls bin/mkdir bin/rm bin/newroutines

* in newroutines.c you can use these header files:
    * usys.h: system call interfaces
    * uio.h: basic input output function
    * string.h: basic string operate function
* `make fs && make run` then you can run your user routines


###BUG REPORT
See [Issues · LastAvenger/OS67](https://github.com/LastAvenger/OS67/issues)

Please paste the kernel log in the issue.

Uncomment macro `__LOG_ON` as follow to enable logging of specific file:

     - // #define __LOG_ON 1
     + #define __LOG_ON 1

###LICENSE
[GNU General Public License Version 3](https://github.com/LastAvenger/OS67/blob/master/LICENSE)

###REFERENCES
* [MIT 6.828 xv6](http://pdos.csail.mit.edu/6.828/2011/xv6.html)
* [xv6 中文文档](https://github.com/ranxian/xv6-chinese)
* [Bran's Kernel Developments Toturial](http://www.osdever.net/bkerndev/Docs/gettingstarted.htm)
* [Bran's Kernel Developments Toturial - 译言网](http://article.yeeyan.org/view/197439/161890)
* [wiki.osdev.org](http://wiki.osdev.org/Main_Page)
* [hurlex-doc](https://github.com/hurley25/hurlex-doc)
* [fleurix](https://github.com/Fleurer/fleurix)
* [Minix File System - Dr.John C.S.Lui](https://koala.cs.pub.ro/redmine/attachments/download/105/minix.pdf)
* [《Linux 内核完全注释》](http://book.douban.com/subject/1231236/)
* [《30天自制操作系统》](http://book.douban.com/subject/11530329/)
* [《Orange's 一个操作系统的实现》](http://book.douban.com/subject/3735649/)

###THANKS TO
* [fleuria](http://fleurer-lee.com/)
* [郭家华](http://www.zhihu.com/people/guo-jiahua)
* [farseerfc](https://farseerfc.me/)
* [fixme](https://fbq.github.io/)
* nami

###Just for fun. 
