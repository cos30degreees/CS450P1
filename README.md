                     +---------------------------+
                     |          CS 450           |
                     | PROJECT 1: MULTITHREADING |
                     +---------------------------+

---- GROUP ----

>> Fill in the names and email addresses of your group members.

Sean Baker <baker2sc@stu.cs.jmu.edu>


---- PRELIMINARIES ----

>> If you have any preliminary comments on your submission, notes for the
>> TAs, or extra credit, please give them here.

>> Please cite any offline or online sources you consulted while
>> preparing your submission, other than the project documentation, course
>> text, lecture notes, and course staff.


                             ========
                             PTHREADS
                             ========

---- DATA STRUCTURES ----

>> A1: Copy here the declaration of the struct that you created to pass
>> parameters to the new threads that get created. Explain why you selected
>> these parameters.





---- ALGORITHMS ----

>> A2: Copy here the declaration of the function that runs inside the new
>> thread. Explain in pseudocode and comments how you get to the parameters
>> passed to the function.













>> A3: The parent thread needs to calculate the total number of iterationsen
>> computed in the Mandelbrot calculation. In the multithreaded version, each
>> child thread must return this value to the parent somehow. How do you
>> accomplish this?














---- TEST CASES ----

>> A4: Add three additional test cases to the tests/ directory and add them to
>> the tests/Make.args file as required. In your test cases, examine different
>> coordinates to use as parameters. Can you find any parameters that produce
>> interesting images?


---- PERFORMANCE ----

>> NOTE: This part will make more sense if you run these tests on either stu or
>> one of the machines in the lab. If you try to run these on a virtual machine,
>> you will not see any speedup. You should clone your repository in the lab or
>> from your $HOME directory on stu and run these tests there.


>> A5: Execute the program with the parameters for the 4 original test cases
>> (basic.ck, mandel2.ck, mandel3.ck, and mandel4.ck), both with Pthreads and
>> without. With Pthreads, use 10 threads total. Use the "time" utility (i.e.,
>> put the work "time" at the beginning of the command line) to measure how
>> long they take. Copy and paste your results here. For each of the test
>> cases, compute the speedup.


>> A6: Re-run the Pthreads test cases from (A5) with different numbers of
>> threads (e.g., 2, 50, 500). What do you notice about the performance of
>> these different parameters?


---- LIMITATIONS ----

>> A7: On your virtual machine, try running your Pthread version with -n 1440.
>> Does anything unusual happen? If you run this on stu, do you get the same
>> results? Explain what is happening. (Hint: Consider the implications of a
>> 32-bit vs. 64-bit address space. It might also be helpful to look at what
>> you can learn from doing ulimit -a on the command line.)

The virtual machine. since the virtual machine is running 64-bit instructions cannot be emulated. This  sysl tem to crash when the x86 processor tried to run those x64 instructions. 

>> A8: On the command-line, do ulimit -u 200, then run one of the test cases
>> again with -n 288. What happens and why? (Hint: Again, look at ulimit -a
>> to see what you can lean.)



                             ======
                             OpenMP
                             ======

---- ALGORITHMS ----

>> B1: Copy here your OpenMP translation of the unithreaded code. Explain how
>> you assigned rows to the individual threads and how you specified the numberul
>> of threads to use.
#pragma omp parallel
{	
#pragma omp for reduction(+:total_iters) private(j, i, x, y, iters, b, g ,r)

openMP acts as a wrapper for Pthreads. At runtime the compiler will  will calculate the code in the for loop to determine the number of worker thre ads, unless this is specified by OMP_SET_NUM_threads. #pragma omp for maps the iterations of the loop to the threads as needed. by default all the variables are shared except for the for loop variables in the parrallel section of the loop.

>> NOTE: As before, the performance test makes more sense if you have multicore
>> or multiprocessor systems, not a virtual machine.


>> B2: Repeat (A5) comparing your OpenMP implementation with the original
>> unithreaded implementation. Do you notice any significant differences
>> between the Pthread performance and the OpenMP performance? Why or why not?


>> B3: Repeat (A6) with OpenMP. How do these results compare with what you saw
>> for Pthreads?


