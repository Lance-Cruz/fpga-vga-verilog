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
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
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
