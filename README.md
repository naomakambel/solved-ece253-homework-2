Download Link: https://assignmentchef.com/product/solved-ece253-homework-2
<br>
<ol>

 <li>Microblaze Processor: Read the slide set “MicroBlaze Overview” and “MicroBlaze Notes” from Gauchospace.

  <ul>

   <li>Describe how branch delay slot instructions can improve the code throughput.</li>

   <li>If interrupt latency is of key importance to a design, why might support for hardware divide instructions be an issue?</li>

   <li>Consider a Microblaze processor with initial stack pointer at address 0x0b0 on program start. For a series of depth-first recursive function calls on small functions with 1-2 parameters each, estimate how many calls can you support before serious trouble is likely. What trouble?</li>

   <li>Consider a function call whose parameter is a small 6×6 array of long ints which is declared in the parent as simply “long int”. Where, physically (i.e. on the stack, in the heap, in initialized memory) is the storage for the array allocated? Where is it stored if declared as “static”?</li>

   <li>A bug in an otherwise carefully checked embedded system is diagnosed as the stack growing too large during some rare execution traces. To fix this problem, the data segment of the program is moved from the shared BRAM to the much larger DRAM device on the Nexys Board. The larger space fixed the stack overflow, but the new version exhibits a variety of odd bugs including missing some interrupts. Why might this be happening?</li>

  </ul></li>

 <li>Consider the following code fragment:</li>

</ol>

static int var; void bar(void){ var=0;

while (var!=255);

}

Most compilers will notice that no other code can possibly change the value stored in var, and will assume that it will remain equal to 0 at all times. The compiler will therefore replace the function body with an infinite loop similar to this:

void bar optimized(void){ var=0; while (<strong>True</strong>);

}

However, var might represent a location that can be changed by other elements of the computer system at any time, such as a hardware register of a device connected to the CPU. The above code would never detect such a change. Rewrite to show how to prevent this from happening.

<ol start="3">

 <li>The attached code <strong>two interrupt model.c </strong>contains a model for a system that can be interrupted by 2 interrupts:</li>

</ol>

<table width="419">

 <tbody>

  <tr>

   <td width="94">Interrupt</td>

   <td width="171">Run-time(clock cycles)</td>

   <td width="92">Probability</td>

   <td width="61">Priority</td>

  </tr>

  <tr>

   <td width="94">Interrupt0</td>

   <td width="171">3</td>

   <td width="92">0.1</td>

   <td width="61">1</td>

  </tr>

  <tr>

   <td width="94">Interrupt1</td>

   <td width="171">5</td>

   <td width="92">0.03</td>

   <td width="61">2</td>

  </tr>

 </tbody>

</table>

1

Rules for servicing the interrupts are as follows:

<ul>

 <li>The interrupt with the higher priority value will be serviced first, if the two interrupts arrive at the same time.</li>

 <li>The system has a mechanism to mark <strong>one </strong>interrupt of each kind as “pending”, if it cannot be serviced immediately after its occurrence. This happens if any interrupt is being serviced when the current interrupt is fired.</li>

 <li>If any interrupt is “pending” and a new request for the same interrupt occurs, the request is “missed” and is not serviced at all. The program keeps track of the number of missed interrupts for each kind.</li>

 <li>If more than one interrupt is pending, the interrupt with the higher priority will be serviced first.</li>

 <li>Determine the mean and worst case service time for each interrupt. Plot a CDF for the measured service times and indicate the confidence intervals.</li>

 <li>Increase the probability of Interrupt0 to 0.2, roughly doubling the number of interrupt requests of that type. Measure the number of missed interrupts and the worst case latency of both interrupt requests. Explain your findings.</li>

</ul>