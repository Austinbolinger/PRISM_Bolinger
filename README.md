PRISM_Bolinger
==============

#ALU and Datapath
###Design
Originally I looked at the code and saw that I needed to make a case for each OpSel. I then looked at my PRISM Instruction Set Table. I identified three of the 8 operations as operations I would need to make files for like the fuller adder we created in lab 2. I created the code for the process for the AND, NOT, ROR, OR, and IN operations. I then made vhdl files for fuller adder or ADD and LDA and NEG. But that is when I ran into problems. I did not understand how to implement entities in my cases. 

I decided to get some help from C3C Pluger. He looked at my code an suggested not using components by using signed and unsigned type casting. After that, I realized from his help that I could change all my coding to type casting because I would have run into errors anyways when I checked the syntax. So, I changed all the code to include type casting which ended up making the code much easier to write and read.

My ALU would look like this after implementation:
![ALU drawing](https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/ALU_Drawing.JPG?raw=true "ALU Drawing")

This is the ALU code.
https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/ALU_shell.vhd

For the datapath, I looked at this picture.
![prism schematic](https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/prismschematic.JPG?raw=true "PRISM Schematic")

This picture allowed me to closely look at each registor. I broke down the code given for the PC Registor. I saw that the process depended on all inputs. The reset was asynchronous. The rising edge of the clock starts the if else statements after that to determine the output value. After I understood the given code. I copied the code and pasted the process for each of the processes below (one for each of the other registors). I then went in and changed all the inputs that the process recognized for each registor. Again, I used the prism schematic to look at each registor closely. I then changed the output variable used to match that specific registor. I changed the load variable and the inputs as well in the same manner as the output variable. I then noticed that the only a few used 8 bits. I changed the others to 4 bits.

Next I needed to do the last few lines of code. Which was just logical sense of assigning values to the outputs based on looking at the picture above some more.

This is the Datapath code.
https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/Datapath_shell.vhd

###Reverse Engineering
The results from the test bench worked. I looked at each case individually, usually 2 or 3 tests for each OpSel. By using the schematic given and the Table mentioned earlier, I was able to confirm that each OpSel was performing the correct operation with the correct input and returning the correct output.

The test bench results look like this.
![test bench](https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/testbenchOutput.JPG?raw=true "Test Bench")

This is the ALU test bench code. https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/ALU_testbench.vhd

This is the Datapath test bench code. https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/Datapath_testbench.vhd

The test bench results for the datapath are super extensive. I only checked a few of the results with the same type of logic I used to code the datapath. I would randomly click somewhere on the results and analysis the outcome.

I did compare my work to the lab4 handout that had the results for what our data should look like. For the first 50 nseconds, at least, mine matches the lab4 test bench wave graph.

Here is the results I looked at to see if my results were the same as the given results. I then used this to see what happens at 50-100ns and 225ns. 
![results](https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/datapathwithlab4.JPG?raw=true "Results")

From 50 to 100ns the results show that it: At 54ns the clock goes up, the 4 from data is asked to be anded with the b from accumulator but the accumulator load is zero until the next clock cycle at 65ns. There the load is 1 the accumulator is still b and the op sel asks the mux to rotate right the accumulator. The result is now d as displayed by the next accumulator value. The for the reset of the time between 50 and 100 ns, the clock cycles twice more but the accumulator load is still at zero. So the accumulator just reads what it was before. 

At 225 ns, The JmpSel turns to 1 giving the PC signal the MarHi and MarLo nibbles on the next clock cycle. Other wise the signal of MarHi and MarLo gets carried to the addSel mux. When the addSel turns to 1, the signal gives the Address bus the MarHi MarLo. Otherwise the PC signal gives the address bus its 8 bit signal.

The test results for the datapath looked like this.
![test bench](https://github.com/Austinbolinger/PRISM_Bolinger/blob/master/datapathtestbench.JPG?raw=true "Test Bench")

####Data Checked
Lesson 29 Dr. Neebel checked my ALU.
Lesson 30 Dr. Neebel saw my working datapath testbench output.

#####Documentation
C3C Pluger explained the importance of using unsigned and signed type casting.
