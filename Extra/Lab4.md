# Lab 4: Cache Simulator

**Objective:**  Demonstrate the behavior of different cache systems; prove understanding of why each type of cache behaves the way that it does.

## Introduction

For this lab you will be using the ParaCache simulator to peform a series of experiments. You will record your results and submit a writeup that includes screenshots.

Please use the word processor of your choice to produce your writeup. Export or print to .PDF and submit the .PDF document on LearningSuite.

## Steps

1. Go to ParaCache Simulator (https://www3.ntu.edu.sg/home/smitha/ParaCache/Paracache/start.html)
2. Click on Direct Mapped Cache
3. Make sure the **Write Policy** is on `Write Back` and `Write On Allocate`.  Also make sure the **Cache Size** is set to `16`, the **Memory Size** is set to `2048`, and the Offset Bits is set to `2`.  All of these settings should be the default.  Click **submit** to create your cache and memory.
4. The "Instruction" box offers a list of either load or store operations with hexadecimal addresses. To the left is the next operation (**Load** or **Store**) and to the right is the address. In the box below you can create a list of the next addresses. Once you have at least one operation you can click "Submit" and, in the "Information" box click the **Next** button to step through the memory cache retrieval. Experiment with the UI a little to get a feel for how it all works. You can click **Gen Random** to generate a random set of addresses.
5. Click **Reset** and **Submit** to clear the results of your experiment.
6. Now, enter a list of 10 addresses, separated by commas for an actual test. Remember, the first address goes in the box to the right and the remainder in the box below, separated by commas. Addresses are in hexadecimal though they don't have a "0x" prefix. A random set of addresses is much less likely to generate cache hits. So use a pattern that is likely to yield more interesting results.
7. Step through the simulation by clicking **Submit** in the "instruction" section and clicking through **Next** in the information section. Be sure to read each screen in the information section thoroughly to the point where there are no surprises by the time you finish the sequence. You should be able to predict the behavior of each instruction.
    * Some of the boxes may be hard to read due to dark background colors. If you select the text with your mouse they will be more readable.
8. Include in your writeup the sequence you used, screenshots of your cache, and a 2-3 sentence explanation of how this type of cache works.
9. Repeat steps 3-6 for both `Fully Associative Cache` and *either* `2-` or `4-Way Set Associative Cache` (your choice).  Make sure you keep the **Replacement Settings** as `FIFO` on these types of cache.
10. Write a short 2-3 sentence comparison of how these 3 types of caches differ from each other.  This is to check that you understand the difference between each type.  Make sure to specify if you’re talking about 2- or 4-Way Set Associative.
11. Click **Reset** on the cache information, then set the **Cache Size** to `64`.  Click **Submit**.  Manually generate a sequence of 16 unique addresses which, when looped (enter the sequence twice), will cause all misses in a direct mapped cache but will have all hits the second time through a fully associative cache, so a 16-16 ratio (i.e., 16 hits and 16 misses).
12. Record the address sequence.
13. Explain how you came up with the sequence that demonstrates this behavior.
14. With a cache size of 64, manually generate a sequence of 17 unique addresses which, when looped (enter the sequence twice), will cause all misses in a fully associative cache but will have a 15-19 ratio (i.e., 15 hits and 19 misses) in a direct mapped cache.
15. Record the address sequence.
16. Record the number of misses in the direct mapped cache during the second loop.
Explain how you came up with the sequence that demonstrates this behavior. What caused direct mapped cache to work better in this case?
 
## Writeup

Please include the following in your writeup:

* Include a header (name, course number, assignment number/title).
* The sequence used for your experiments on Direct Mapped Cache, Fully Associative Cache, and either 2- or 4-Way Set Associative Cache.
* Screenshots of the cache as you parsed through the above three types.
* A 2-3 sentence explanation for each type of cache explaining how it works.
* An additional 2-3 sentence explanation explaining the difference between all 3 types of cache.
* Your sequence for step 9, with screenshots and an explanation of how you came up with the sequence.
* Your sequence for step 10, with screenshots and an explanation of how you came up with the sequence.
* Finally, an explanation of why direct mapped cache performed better than fully associative cache in step 10.

Remember to export your writeup as a .PDF and submit in LearningSuite.