---
title: Lab 5: Memory
---

**Objective:**  Develop a sense of how virtual memory and translation caching work.

## Introduction

Please read all instructions before beginning the lab. In particular, review the [Writeup and Submission](#writeup-and-submission) section so you know what to submit upon completion of the lab.

For the first part of this lab you will use the ParaCache simulator (same as Lab 4) to simulate virtual memory address translation. You will record your results and submit a writeup that includes screenshots.

For the second part of this lab you will use the memory mountain test and graph the results to discover the characteristics of your computer's memory system. The test comes from the *Computer Systems, A Programmer's Perspective* textbook section 6.6.1.

## Part 1: Virtual Memory

1. Proceed to the same website as in lab 4 - [https://www3.ntu.edu.sg/home/smitha/ParaCache/Paracache/start.html](https://www3.ntu.edu.sg/home/smitha/ParaCache/Paracache/start.html){:target="_blank"}; click on `Virtual Memory`.
2. Set the Physical Page Size to 64, Offset Bits to 2, Virtual Memory Size to 512, and TLB Entries to 10. **These are not necessarily the defaults.** Click `Submit`.
3. Generate a series of 10 random instructions (actually addresses), and step through the information log.  Take a screenshot of the final result to include in your writeup.
4. From step 3, describe the process this simulation is stepping you through – from loading an address to loading the data from secondary memory.  Make sure to include each step of the process, including the TLB and Page Table.
5. Reset the memory using the same instructions as in step 2.
Generate a series of 31 instructions that will miss 11 times, hit in the TLB 10 times, and miss in the TLB but hit in the page table 10 times.  Take a screenshot of the final result.
    * Hint – take advantage of the fact that the least significant 2 bits are used for the offset, and the most significant 7 bits are used for the index.
    * Second hint – use the same strategy you used when creating a series of 17 instructions that always missed in a fully associative cache.
6. In your writeup, include the sequence you used and explain why it works the way it does.
7. Describe how the Transaction Lookaside Buffer (TLB) improves the performance of a computer (2-3 sentences).

## Part 2: Memory Mountain

This part requires Linux or the Windows Subsystem for Linux. Use whatever system you used for the Binary Bomb and Buffer Overflow Labs.

1. In your textbook, the memory mountain test is described in section 6.6.1 (page 639). This test shows the different levels of cache, and virtual memory
2. First, get information on the type of caches your system has.
    * On **Linux**, install **cpuid** with the command `sudo apt install cpuid`.
    * Run **cpuid** and save the output to a text file. E.g. `cpuid > cpuid.txt`
    * Review the information under the "deterministic cache parameters" heading if present. Include in your writeup these specifications: "cache type", "cache level", "fully associative cache", "system coherency line size" (what we call block size), "ways of associativity", and "number of sets"<br/>Some systems will not have a "deterministic cache parameters" section or the section may be blank. Regardless, please report any cache information that's report for your processor or write, "No cache information given" if you cannot find anything useful.
3. Run the MemoryMountain executable.
    * For Linux, download the executable [from here](LinuxMemoryMountain.tar).
    * Or, if you prefer, build from [the source files](MemoryMountainSource.zip).
    * Note 1: Extract the executable from the .tar with the Linux command<br/>`tar -xf LinuxMemoryMountain.tar`
    * Note 2: Once the executable is extracted, you may have to set it as executable with the command<br/>`chmod +x MemoryMountain` 
4. Run the MemoryMountain from a Linux command line and pipe the results into a .csv file using the ">" command.<br/>e.g., `./MemoryMountain > data.csv`
    * Be patient. On a fast processor it takes about a minute. It could take longer on a slower machine
5. The result is a table of numbers. Open the .csv file you created using Microsoft Excel, OpenOffice Calc, or another package capable of making 3D charts. You can also use [Google Sheets](https://docs.google.com/spreadsheets){:target="_blank"} but it's only capable of 2D charts.
6. Create a 3D graph of the data (or 2D if necessary). Include that graph in your writeup. Here are instructions for how to do it in Excel.
    * Open the .csv file in excel.
    * Select the cell in the upper-left of the table. (Typically, it is already selected).
    * Select **Insert** > **Recommended Charts**
    * Select **All Charts** > **Surface** > **3-D Surface**
    * The chart should appear. In the **Chart Design** tab experiment with **Switch Row/Column**. Depending on your data, the different views will reveal different information.
    * Once you are satisfied with the chart, save it as an image by right-clicking in just inside the chart border but outside the graphic, legend, or title, and then selecting **Save as Picture**.
7. Mention 2-5 things you observe in your computer's memory mountain. Reading section 6.6.1 from the textbook will help with this part, especially Figure 6.41.

Here is the example from the textbook authors with regions labeled: [MemoryMountain-CSAPP](MemoryMountain-CSAPP.png){:target="_blank"}.
And here is an example with data from my computer: [MemoryMountain-Redd](MemoryMountain-Redd.png){:target="_blank"}.

Your memory mountain may be quite different from the examples. It may be influenced by the architecture if you're running on a virtual machine, on an emulator or in the cloud. Some people get more of a "memory plain" than a memory mountain. Regardless, just report on what you find. You may find it interesting to compare your results with your classmates. 

**WSL2 Hints**

If you're running Linux under WSL2 (Windows Subsystem for Windows 2), you are likely to generate your data in Linux but generate your graphs in Windows. So, you need move files between your Windows and Linux subsystems. The Linux file system may be accessed from the Windows File explorer at `\\wsl$\`. In that file system you'll find your home directory at `\\wsl$\Ubuntu\home\username` or similar. Likewise, you can access your Windows file system from LSW2 at the following path: `/mnt/`. So, for example, your Windows home directory would be at `/mnt/c/users/username`.

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
    * Cache information from `cpuid`.
    * Your memory mountain 3-D graph.
    * 2-5 observations regarding your memory mountain.

Submit the result in .pdf format on LearningSuite.
