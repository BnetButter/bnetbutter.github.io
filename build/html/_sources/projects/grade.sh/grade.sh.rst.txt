grade.sh
========

grade.sh is the auto-grader for CS1500. Each semester the class gets over 200
students. It works using gitlab CI/CD to run the grading script. grade.sh leaves
an artifact which gets extracted and automatically pushed to Canvas. It existed
before I came to Missouri S&T but I made substantial improvements during my time
as a grader. The current iteration looks like this when running Python code

.. image:: https://i.imgur.com/HpIipbR.gif

That's just the script that's run on gitlab CI/CD. We want students to be able
to see everything going on when a bot is in control of their grade.

Visual Studio Code Extension
============================

The first thing I did was try to provide a decent UI for students. I wanted to
integrate grade.sh with Visual Studio Code and provide a web-based interface for
students to use. I went a bit overboard and made it too complicated by trying
to package an entire VSCode extension with every assignment. It worked... but 
there was too much overhead. Nonetheless, students really liked the user interface.

.. image:: https://i.imgur.com/btgfKKZ.gif

Alas, I had to scrap the idea of packaging an extension with every assignment.

grade.sh/Tor
============

During LEAD sessions where we offer tutoring
and assignment help, we found that helping students over zoom was complicated.
We had to pull student assignments from gitlab just to see their source code or
ask them to share their screen. We as graders and tutors couldn't run the tests
ourselves without pulling the repo. And if we wanted to test out their changes,
that's another pull. The solution was Tor. I wrote a bash script that created
a hidden service directory, generated a one time onion link students can share,
and started a python http server that served over the assignment root directory.

.. image:: https://i.imgur.com/FaSVPox.gif

Yes. VSCode live share is an option. But not everyone used VSCode as their IDE.
Some used spyder, other used atom. This is platform independent. Any one with
the onion link and Tor browser can gain access to the assignment.

tmux-pudb3
==========

grade.sh in interactive mode drops user into debug mode. When a test is failed,
a command line debugger is started. The CLI debugger we use is pudb3.
Since it's a command line debugger, we can't separate the control stream from
stdio input stream. However pudb3 can be attached to a remote process. It just
needed to know which terminal the debugee was running in. So I wrote a bash script
which started the debuggee in one tmux panel and the debugger in another. The
debuggee panel displays stdout stream.

.. image:: https://i.imgur.com/L7LebZw.gif

Getting this to work took a surprising amount of hackery. When you request tmux
to start a new panel session, a pseudo terminal is created. The default size 
for a new PTY is [NOT][USABLE]. So right after launching tmux, pty.fork() is
called in a python script. The slave terminal is resized, which also forces a
resize to the master terminal. Then the debuggee is started and pudb3 attached.

