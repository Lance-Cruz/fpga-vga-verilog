---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

Welcome to my System of Chip (SoC) Field Programable Gate Array (FPGA) project. Here is where I blogged the timeline of my project to the lead up of my final work.

## **Template VGA Design**
### **Project Set-Up**
In setting up this project, we had two source code that were given to us to work with, one being a Colour Cycle and another a Stripes. The one I used below was the VGAStripes source code, which had the following structure. In the design sources had a VGATop.v file and within it had a VGASync.v, VGAColourStripes.v, after the creation of the project we went to the IP catalog to find a clock wizard which allows us to run the project at 25MHz. In the constraints folder had a Basys3_Master.xdc file, this holds the rules for the design (i.e what pins are being used for the FGPA). In the Simulation folder contained a Testbench.v and the VGATop.v like the one in the design sources.

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/VGAProjectSummary.png">

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/VGAProjectSources.png">

### **Template Code**
For this project we were given two templates to start with. First being the VGAColorCycle.v file which uses a state machine logic to go through a series of colours. It uses twelve bits with four bits each being used to represent red, green, and blue (rgb), and set the rgb values to generate the colour. The code would use a counter to show a colour for a period of time and then switch to the next colour once the timer reached the maximum value. This would lead into a loop of colours displayed on a monitor.

The second template we were given was the VGAColorStripes.v file. This used a series of if statements to check if the program was between a specific range of columns, then sets that range for a specific colour. This led to a series of columns with different colours depending on the range of pixels. (i.e black would be between 0 to 80 pixels, blue would be between 80 to 160 pixel). Unlike the previous example we were given, this display one single still image.

### **Simulation**
Once our project was set up, a simulation was run. The signals shown in the simulation were not actual full-scale, but a scaled-down versions to reduce the time needed to simulate it.

Analysing the wave that was generated for us, we can see serveral signals such as clk, rst, h_sync, and v_sync. The clock is showing periodic pulses, the reset signal is active high, it is high at the start, then set to low for the remainder. The h_sync signal goes low more often then the v_sync signal. This is excepted because v_sync is set to low once the entire frame has been written, while h_sync is set to low at the end for each row. The row counter goes from 0 to 5 before repeating, instead of the full 0-479 confirms that we are using a scaled-down version of our simulation. The column signal appears more often then the rows, because for each row value, the columns count through their entire range of 0-640 before the row value is incremented.

The colour signals are toggle between 0 and f, a combinations of these across the channels produce different colours. For example, when all three colours signals are f, the colour would be white and if all three colours signals are 0, then the colour would we black. Taking our screenshot at 74ns, only the red signal is f, meaning the colour red will be displayed. 

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/ColorStripesSimulation.png">

### **Synthesis**
The synthesis processes takes our code and converts it into a netlist, and then the implementaion processes produces a logical block schematic that shows how the components are arranged and routed.

Below you can see synthesised design for the ColorStripes and the schematic which contains the logical blocks needed to implement the ColorStripes, including the clock, VGA sync, and the colour generation.

The VGA sync (u_vga_sync) block produces the horizontal sync and vertical sync signals, the colour generation block (i_color_stripes) outputs the values for red, green, and blue, which is used to determine the visible color of the stripes on the display. For the outputs, buffers are used to represent each bit of the RGB, as well both hsync and vsync. The clock and reset inputs also pass through buffers. All blocks receive the same clock input for synchronization.

#### Colour Stripes Synthesis and Implentation

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/VGASynthesis.png">

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/Schematic.png">

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/SchematicCloseUp.png">


### **Demonstration**
Below is the output of our ColorStripes.v, showing a series a colours in stripes based on the pixel range. 

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/ColourStripesDemo.png">

## **My VGA Design Edit**
After seeing the output of the colour stripes, which were divided into eight sections with each colour taking up 80 pixels, I got the idea to create a pixel art emoji. My goal was to use the ColorStripes.v template as a base and modify it to form the pixel art image.

For my design, I chose to create a 15x15 grid, where each block in the grid would represent a 10x10 pixel area. This resulted in a final image size of 150x150 pixels on my screen. Initially, I started by adjusting the template to form a box outline and check how it would fit on the 640x480 display we were working with.



### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
