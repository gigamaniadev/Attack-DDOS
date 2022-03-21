Attack DoS tool
===========================================================================================

Attack DoS tool ported to Go language from Python. 
Original Python utility by Barry Shteiman http://www.sectorix.com/2012/05/17/hulk-web-server-dos-tool/
I just ported the code as is quick and dirty. Original functions names are keeped and original logic mostly keeped too.

The main difference from Python version layed in Golang architecture for concurrency: the goroutines. hulk.py runs
a new thread for each connection in the connection pool so it uses hundreds and thousands of threads. 
hulk.go just uses lightweight goroutines that used only tens of threads (commonly golang runtime started one thread for
CPU core + several service threads). This architecture allows golang version better consume resources and got much higher 
connection pool on the same hardware than Python version can.

This tool targeted for stress testing and may really down badly configured server or badly made app. Use it carefully.

Examples:

    $ python2.7 Attack.py http://example.com/

Useful environment vars:

* Limit the connection pool (1024 by default).


===========================================================================================
