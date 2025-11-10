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

Analysing the wave that was generated for us, we can see serveral signals such as clk, rst, h_sync, and v_sync. The clock is showing periodic pulses, the reset signal is active high, it is high at the start, then set to low for the remainder. The h_sync signal goes low more often then the v_sync signal. This is excepted because v_sync is set to low once the entire frame has been written, while h_sync is set to low at the end for each row. The row counter goes from 0 to 5 before repeating, instead of the full 0-479 confirms that we are using a scaled-down version of our simulation.

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/ColorStripesSimulation.png">

### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/VGASynthesis.png">

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/Schematic.png">

<img src="https://raw.githubusercontent.com/Lance-Cruz/fpga-vga-verilog/main/docs/assets/images/SchematicCloseUp.png">


### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
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
