# ginitd
ginitd is a very badly programmed PID 1 for Unix-like
systems. Ridiculously, it isn't even PID 1 - ginitd does
most of its work as another process (often PID 200-300).

Documentation can be found
[here](https://github.com/smwms1/ginitd/tree/devel/doc).

#### How ginitd improves startup speed.
A summary of ginitd's ways of improving startup speed by
removing the shell, and therefore much process-spawning,
from the startup scripts.

Link: **[1.md](/ginitd/1.md)**