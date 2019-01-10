# Questions

## HPC good citizenship

1. On the UCI cluster, the resource request "-pe openmp 64" refers to the number of processors requested.  Does that
   request mean that your commands will use multiple processors?
 	**Yes, if they can be parallelized.**

2. In general, how do you know how many processors, how much RAM, how many files would be required/needed/written by the jobs you are running on the cluster? 
	**I will google it for jobs I will be running or just use the command /usr/bin/time-v ls / to find out.**

3. In order to be a "good citizen", you need to have some idea of much RAM your job requires.  In particular, you need
   to know the "peak" (i.e., maximum) RAM required at any point during execution.  Show an example of the shell command that you would use on a Linux machine to measure run time and peak ram usage of an arbitrary command, where the time/peak RAM values are written to a file.
	```
	/usr/bin/time -v ls / &>> Summary.txt
	```

4. What are the units of your answer for number 3?
	** The units for time is seconds. The units for RAM is kbytes.**

5. What are the bash commands for the following operations:

    * Checking that a file exists
	```
	if [ -f questions.md ]
	then
	 echo "the file exists"
	else
	 echo "the file does not exists"
	fi
	```

    * Checking that a file exists and is not empty
	```
	if [ -s README.md ]
	then 
	 echo "The file has some data." 
	else
	 echo "The file is empty."
	fi
	```

6. How would you use the commands from your answer to 5 to write a work flow for HPC that only runs a job if the
   expected output file is **not** present.
	```
	if [ -f question.md ]
	then
	 echo "exists"
	else
	 echo "notpresnt" >> notpresnt.txt
	fi
	```

## Trickier questions

7. Would your answer to number 3 work on Apple's OS X operating system?  If no, do you have any idea why not? 

 	**No. The command only exits on linux system.**
	

8. Most of the HPC nodes have 512Gb (gigabytes) of RAM. Let's say you have a job that will require **no more** than 24Gb
   of RAM.  How would you request resources so that you can run more than one job on a node **and** not cause nodes to
   crash?  Show an example of a skeleton HPC script as part of your answer.  **Knowing how to do this is super important
   and will save you loads of frustration and prevent you from taking out your colleagues' jobs on the cluster,
   preventing you from getting nasty emails from Harry!!!!!!!!!!!**
	```
	#! /bin/bash
	#$ -N run.log
	#$ -q free128
	#$ -l node=nodename
	#$ -l h_rss=24G
	```
