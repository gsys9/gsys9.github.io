# ginitd
ginitd is a very badly programmed PID 1 for Unix-like
systems. Ridiculously, it isn't even PID 1 - ginitd does
most of its work as another process (often PID 200-300).

Documentation can be found
[here](https://github.com/smwms1/ginitd/tree/devel/doc).

ginitd uses both multithreading and multiprocessing to
provide a possibly faster startup mechanism. One advantage
is that it does not spawn endless processes by using shell
scripts - it instead only uses extra python processes to
launch programs, providing a performance improvement over
SysV-style and BSD-style init scripts, which may spawn 
many processes as they use shell-scripts. For example, the
following shell-line spawns no less than 3 separate
processes to check if a kernel module (i915, the Intel
graphics driver) is depended upon by the 'video' kernel
module:

```lsmod | grep "video" | grep "i915"```

Not only does that come with complex output that may not
be easy for the recieving commands to manipulate, it also
does *more* than is necessary. Only the /proc/modules content
up to '\nvideo' must be parsed, but in the shell script, all
of the content is read, only for most of it to be discarded.
It is a very inefficient approach.

More later...