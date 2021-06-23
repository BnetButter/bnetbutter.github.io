py2cfg
======

py2cfg generates control flow graph from python code. It's not my project, but I
did make substantial improvements. Generating graphs as you type was one of the
features I added.

I created a VSCode extension that requested a CFG to be generated based on the
current file and cursor location. The CFG data was stored as pickled bytes in
a SQL database. Every time the cursor moved, the CFG was pulled and a graph generated.

.. image:: https://i.imgur.com/2JreaSi.gif

Another feature I added was interfacing py2cfg with pudb3, a commandline debugger
for python. I wanted to be able to do live tracing of executed control flow paths.
Whenever the user stepped into a function, a process fork was created. The child process
continued to run, while the parent process was paused on step. While the child process
was running, it reported the lines that were being executed back to the parent process.
The parent process then highlighted all the blocks that were visited by the child.

That's the basic idea at least. Implementing it took me the better half of my
first semester at college. But the end result was this

.. image:: https://py2cfg.readthedocs.io/en/latest/_static/pudb3-py2cfg.gif


Read the `py2cfg`_ documentation for more info.

.. _py2cfg: https://py2cfg.readthedocs.io/en/latest/