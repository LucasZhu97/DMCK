DMCK Quick Guideline

------------
Introduction
------------

DMCK is an achronym for Distributed system Model ChecKing
which focus on generating all possibilities of scenarios
of distributed system protocols in order to detect 
distributed concurrency (DC) bugs. If a DC bug is detected,
DMCK is able to provide the target system logs from all nodes,
the order of events that will reproduce the bug, and DMCK
is able to help you debug the patch to fix the DC bug.

More detail related to this tool can be found in
"SAMC: Semantic Aware Model Checking for Fast Discovery Bugs in Cloud Systems" paper
that has been publised in OSDI 2014.

------------------------------
What is included in this tool?
------------------------------

In this DMCK version, we provide two dummy systems
to give simple examples of how DMCK interacts with
the target distributed systems: (1) Simple Concurrent
Messages (SCM); and (2) Sample Leader Election (SampleLE).
You can also find 2 other real systems that we have integrated
with the DMCK to reproduce the DC bug in each system:
(1) Cassandra; and (2) ZooKeeper.

------------------------
How to compile the code?
------------------------
## Reproduce Note
### On Ubuntu 16.04
```
sudo apt update
sudo apt install openjdk-8-jdk-headless
sudo apt-get install ant
sudo apt-get install ivy
````
Let's start with compiling the DMCK and the SCM system.

1. Make sure you have installed the Java-Oracle-8.
2. Copy the target-sys.conf.sample to target-sys.conf 
   in DMCK_dir/scm/ directory
3. Adjust the path file parameters in the target-sys.conf
4. Go to DMCK_dir path and execute `./compile scm` (Don't forget chmox +x compile, and run with sudo)
5. You will find the working_dir location that is specified
   in the target-sys.conf (in default, the working_dir
   can be found in */tmp/scm* directory) is generated there.

--------------------
How to run the DMCK?
--------------------




1. Go to your working_dir directory and execute the
   dmckRunner.sh script.

That's it! You should see the DMCK to run and explore
all possibilities of scenarios. 

Some options in running the dmckRunner.sh is to run it with
"-p" parameter: ./dmckRunner.sh -p
With this command, the DMCK will pause after it has finished
executed the a single path / scenario.

To see the records of all path executions, go to the
working_dir/record/ directory and you can see the path,
result and debug.log for each path.


