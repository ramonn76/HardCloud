---
layout: page
title: HardCloud
permalink: /
---

The computing industry has recently proposed the usage of  FPGAs as a way to improve energy efficiency in modern cloud clusters. Unfortunately, using such FPGA clusters  is a very hard and complex task. In this talk we propose a novel and simple mechanism to offload computation to  the FPGAs available in the  Intel HARP2 architecture, by extending OpenMP directives in such a way that the FPGA becomes just another OpenMP acceleration device that can be used directly from any user program.

## How it work

The version 4.0 of the  OpenMP standard introduces new directives that
enable the transfer of  computation to heterogeneous computing devices
(e.g.  GPUs  or  DSP).  We  use this  programming  model  to  transfer
computation to  an accelerator  that supports  OpenCL 1.2  or greater,
giving  to   the  programmer  the   ability  to  quickly   expand  the
computational power exploring their target devices.

{% highlight C %}

  #pragma omp target device(HARPSIM) map(to: A) map(from: B)
  #pragma omp parallel for use(hrw) module(loopback)
  for (int i = 0; i < NI; i++)
  {
    B[i] = A[i];
  }

{% endhighlight %}


You can look at [Unibench](https://github.com/omp2ocl/Unibench)
repository if you want to see more examples.

## Screencast Demo

Here is a recorded video demonstrating cloud offloading from a simple laptop to a Spark cluster created on Amazon Web Service.

<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" width="560" height="315"
    src="https://www.youtube.com/embed/R5UhzOVrohU" frameborder="0"
    allowfullscreen="">
  </iframe>
</div>

## Documentation, Installation, Configuration

All the information is provided [in the Wiki](https://github.com/omp2ocl/aclang/wiki).
