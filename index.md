---
layout: page
title: HardCloud
permalink: /
---

The computing industry has recently proposed the useof  FPGAs as a way to improve performance and energy efficiency in modern cloud clusters. Unfortunately, using such FPGA clusters  is a very hard and complex task. In this context,we present HardCloud a novel and simple mechanism to offload computation to  the FPGAs available in the  Intel HARP2 platform, by extending OpenMP directives in such a way that the FPGA becomes just another OpenMP acceleration device that can be used directly from any user program. HardCloud is a subproject of [AClang](https://omp2ocl.github.io/aclang).

## How it works

The version 4.0 of the  OpenMP standard introduces new directives that
enable the transfer of  computation to heterogeneous computing devices
(e.g.  GPUs  or  DSP).  We  use this  programming  model  to  transfer
computation to the HARP2 platform or to an emulator (for debug purpose).

The following example shows the syntax that was adopted. The *device(HARPSIM)*
clause indicates that the execution will be performed by the emulator.
Optionally to HARPSIM, there is the HARP keyword that instructs the
HardCloud to generate code for the real HARP instead of for the emulator.
The *map(:to)* clause indicates the data that will be sent to the accelerator,
while the *map(:from)* indicates the data that will be get from the accelerator as a result. 
The clause *use(hrw)* especifies wich optimization is going to be used. Finally, the clause *module(loopback)* indicates the bitstream to configure the FPGA.


{% highlight C %}

  #pragma omp target device(HARPSIM) map(to: A) map(from: B)
  #pragma omp parallel for use(hrw) module(loopback)
  // Code that represents the loopback bitstream
  for (int i = 0; i < NI; i++)
  {
    B[i] = A[i];
  }

{% endhighlight %}


## Screencast Demo

Here is a recorded video demonstrating how to use the HardCloud.

<div class="embed-responsive embed-responsive-16by9">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/hds4YRkGIDY?rel=0" frameborder="0" allowfullscreen></iframe>
</div>

## Documentation, Installation, Configuration

All the information is provided [in the Wiki](https://github.com/omp2ocl/aclang/wiki).
