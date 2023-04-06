# Lab 5: Cache Simulator

**Objective:**  Develop a sense of how virtual memory and translation caching work.

## Introduction

Please read all instructions before beginning the lab. In particular, review the **Writeup and Submission** section so you know what to submit upon completion of the lab.

For the first part of this lab you will use the ParaCache simulator (same as Lab 4) to simulate virtual memory address translation. You will record your results and submit a writeup that includes screenshots.

For the second part of this lab you will use the memory mountain test and graph the results to discover the characteristics of your computer's memory system. The test comes from the *Computer Systems, A Programmer's Perspective* textbook section 6.6.1.

## Part 1: Virtual Memory

1. Proceed to the same website as in lab 4 - [https://www3.ntu.edu.sg/home/smitha/ParaCache/Paracache/start.html](https://www3.ntu.edu.sg/home/smitha/ParaCache/Paracache/start.html); click on `Virtual Memory`.
2. Set the Physical Page Size to 64, Offset Bits to 2, Virtual Memory Size to 512, and TLB Entries to 10. **These are not necessarily the defaults.** Click `Submit`.
3. Generate a series of 10 random instructions (actually addresses), and step through the information log.  Take a screenshot of the final result to include in your writeup.
4. From step 3, describe the process this simulation is stepping you through – from loading an address to loading the data from secondary memory.  Make sure to include each step of the process, including the TLB and Page Table.
5. Reset the memory using the same instructions as in step 2.
Generate a series of 31 instructions that will miss 11 times, hit in the TLB 10 times, and miss in the TLB but hit in the page table 10 times.  Take a screenshot of the final result.
    a. Hint – take advantage of the fact that the least significant 2 bits are used for the offset, and the most significant 7 bits are used for the index.
    b. Second hint – use the same strategy you used when creating a series of 17 instructions that always missed in a fully associative cache.
6. In your writeup, include the sequence you used and explain why it works the way it does.
7. Describe how the Transaction Lookaside Buffer (TLB) improves the performance of a computer (2-3 sentences).

## Part 2: Memory Mountain

This part requires a Windows or Linux computer. If you have a Mac, do the tests on one of the lab computers and then complete the graphing and writeup on whatever computer you prefer.

1. In your textbook, the memory mountain test is shown in section 6.6.1 (page 641). This test shows the different levels of cache, and virtual memory
2. First, get information on the type of caches your system has.
    a. On **Linux**, install **cpuid** with the command `sudo apt install cpuid`.
    b. Run **cpuid** and save the output to a text file. E.g. `cpuid > cpuid.txt`
    c. Review the information under the "deterministic cache parameters" heading. Include in your writeup these specifications: "cache type", "cache level", "fully associative cache", "system coherency line size" (what we call block size), "ways of associativity", and "number of sets"
4. Run the MemoryMountain executable.
    a. For Linux, download the executable [from here](LinuxMemoryMountain.zip).
    b. Or, if you prefer, build from [the source files](MemoryMountainSource.zip).
4. Run the MemoryMountain from a Linux command line and pipe the results into a .csv file using the ">" command. e.g., `./MemoryMountain > data.csv`
    * Be patient. On a fast processor it takes about a minute. It could take longer on a slower machine
5. The result is a table of numbers. Open the .csv file you created using Microsoft Excel, OpenOffice Calc, or another package capable of making 3D charts. You can also use [Google Sheets](https://docs.google.com/spreadsheets) but it's only capable of 2D charts.
6. Create a 3D graph of the data (or 2D if necessary). Include that graph in your writeup. Here are instructions for how to do it in Excel.
    a. Open the .csv file in excel.
    b. Select the cell in the upper-left of the table. (Typically, it is already selected).
    c. Select **Insert** > **Recommended Charts**
    d. Select **All Charts** > **Surface** > **3-D Surface**
    e. The chart should appear. In the **Chart Design** tab experiment with **Switch Row/Column**. Depending on your data, the different views will reveal different information.
    f. Once you are satisfied with the chart, save it as an image by righ-clicking in an area within the box but outside the chart and selecting **Save as Picture**.
7. Mention 2-5 things you observe in your computer's memory mountaion. Reading section 6.6.1 from the textbook will help with this part, especially Figure 6.41.

Here is the example from the textbook authors with regions labeled: [MemoryMountain-CSAPP](MemoryMountain-CSAPP.png).
And here is an example with data from my computer: [MemoryMountain-REDD](MemoryMountain-REDD.png).

## Writeup and Submission

Write up your results using your authoring tool of choice (word processor, MarkDown, HTML etc.), export the result to .pdf format and submit the .pdf on LearningSuite.

Please follow this outline:

    * Your Name and Date
    * Title
    * Virtual Memory
        * Screenshot of 10 random instructions/addresses. (Virtual Memory Step 3)
        Description of the process illustrated by the simulator. (Virtual Memory step 4)
        * Sequence of 32 instructions/addresses that produced the expected pattern. (Virtual Memory Step 5)
        * Why the sequence worked. (Virtual Memory Step 6)
        * How the TLB improves performance. (Virtual Memory Step 7)
    * Memory Mountain
        * Your memory mountain 3-D graph.
        * 2-5 observations regarding your memory mountain.

Submit the result in .pdf format on LearningSuite.


