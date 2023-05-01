Download Link: https://assignmentchef.com/product/solved-cecs326-homework-11
<br>
Chapter 9 (and a little Chapter 8)

You will need to open 5 terminal windows to do this homework. Remotely, this means 5 ssh sessions. I would suggest setting up ssh keys if you haven’t already to avoid typing your password 5 times.

<strong>Program 1:</strong>

A simple exercise in using counting semaphores. You will build “LightWeight” and ”HeavyWeight” programs. There will be a total of 5 resources. The LightWeight program will lock two of them, the HeavyWeight program will lock three of them.

Both programs will do the following (use a for loop) 5 times:

<ul>

 <li>Lock the required number of resources.</li>

 <li>Print a message (either “HeavyWeight Starting” or “LightWeight Starting”) 3) Sleep 4 seconds.</li>

</ul>

4) Print a message (either “HeavyWeight Ending” or “LightWeight Ending”) 5) Unlock the resources 6) Sleep 8 seconds.

Testing: Start 2 copies of the HeavyWeight program, then 3 copies of the LightWeight program. Check your output to make sure you never have 2 HeavyWeights running at the same time, or any other combination that would require more than 5 resources.

<strong>Program 2:</strong>

An exercise using multiple semaphores.

You will build a solution to the readers and writers problem. You will build both a Readers and a Writers program.

The writer program will do the following 5 times:

<ul>

 <li>perform all necessary locks</li>

 <li>print “Writing”</li>

 <li>Sleep 4 seconds</li>

 <li>print “Done writing”</li>

 <li>perform all necessary unlocks 6) Sleep 8 seconds</li>

</ul>

The reader program will do the following times:

<ul>

 <li>perform all necessary locks and associated counting</li>

 <li>print “Reading”</li>

 <li>Sleep 2 seconds</li>

 <li>print “Done reading”</li>

 <li>perform all necessary unlocks and associated counting 6) Sleep 4 seconds</li>

</ul>

Use a counting semaphore (as shown in lecture) to keep track of the number of readers. Use an array of 4 semaphores; three for the semaphores, one to count the number of readers.

Testing: Start 2 copies of the writer program, then 3 copies of the reader program. Check your output to make sure the when a writer is active, no one else is.

The correct P and V code for readers and writers is given on the back of this page.

Nathan Pickrell   8 October 2019 (Week 7 Lecture 2)             Due: 10 October 2019 (Week 8, Lab 1) <strong>CECS 326   Homework 11           Fall 2019</strong>

Writer

P(BlockReaders) P(WriterLock) write V(WriterLock)

V(BlockReaders)

Reader

P(BlockReaders)

P(CounterLock) if (Counter == 0) P(WriterLock) Counter


V(CounterLock) V(BlockReaders) read

P(CounterLock) Counter–

if (Counter == 0) V(WriterLock) V(CounterLock)

<em>Multiple program discussion:</em>

In both cases the solution requires you to run more than one program. This is the first time you have done that. You will discover that, if you build both programs in the same directory, you can’t call both executables a.out (because you can’t have two files in a directory that have the same name. An easy solution is to give the executables different name using a compiler option.

For example: gcc writer.c -o w.out will cause the executable that the compiler outputs to be called w.out. (a.out is a default name when you don’t tell it what to call it)

WARNING: gcc writer.c -o writer.c will DESTROY your source code by dropping the executable on top of it; so be careful. I usually end my executable names in .out so this doesn’t happen.


