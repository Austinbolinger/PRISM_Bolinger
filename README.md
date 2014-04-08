PRISM_Bolinger
==============

#ALU
###Analysis
Originally I looked at the code and saw that I needed to make a case for each OpSel. I then looked at my PRISM Instruction Set Table. I identified three of the 8 operations as operations I would need to make files for like the fuller adder we created in lab 2. I created the code for the process for the AND, NOT, ROR, OR, and IN operations. I then made vhdl files for fuller adder or ADD and LDA and NEG. But that is when I ran into problems. I did not understand how to implement entities in my cases. 

I decided to get some help from C3C Pluger. He looked at my code an suggested not using components by using signed and unsigned type casting. After that, I realized from his help that I could change all my coding to type casting because I would have run into errors anyways when I checked the syntax. So, I changed all the code to include type casting which ended up making the code much easier to write and read.

This is the ALU code.
https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/ALU_shell.vhd

###Results
The results from the test bench worked. I looked at each case individually, usually 2 or 3 tests for each OpSel. By using the schematic given and the Table mentioned earlier, I was able to confirm that each OpSel was performing the correct operation with the correct input and returning the correct output.

The test bench results look like this.
![test bench](https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/testbenchOutput.JPG?raw=true "Test Bench")

This is the ALU test bench code. https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/ALU_testbench.vhd

#####Documentation
C3C Pluger explained the importance of using unsigned and signed type casting.
