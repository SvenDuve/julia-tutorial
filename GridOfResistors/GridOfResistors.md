<HTML>

<body>

<H1>Grid of Resistors</H1>

<h2>Description</h2>

The problem is to compute the voltages and the effective
resistance of a 2<i>n</i>+1 by 2<i>n</i>+2 grid of 1 ohm resistors if
a battery is connected to the two center points. This is a discrete
version of finding the lines of force using iron filings for a magnet.
The picture below describes the two dimensional problem.

<img src="http://beowulf.lcs.mit.edu/18.337-2004/hw1/battery.gif">

The method of solution that we will use here is <i>successive
overrelaxation</i> (SOR) with red-black ordering. This is certainly
not the fastest way to solve the problem, but it does illustrate many
important programming ideas.

It is not so important that you know the details of SOR. Some of the
basic ideas may be found on pages 407-409 of Gil
Strang's <a href="http://www-math.mit.edu/%7Egs/books/itam_toc.html">Introduction
to Applied Mathematics</a>. A somewhat more in-depth discussion may be
found in any serious numerical analysis text such as Stoer and
Bulirsch's <em>Introduction to Numerical Analysis</em>. What is
important is that you see that the nodes are divided in half into red
nodes and black nodes. During the first pass, the red nodes obtain the
voltages as a weighted average of their original voltage, the input
(if any) <i>and the four surrounding black nodes</i>. During the
second pass, the black nodes obtain voltages from the four surrounding
red nodes. The process converges in the limit to the correct answer
for the finite grid.

A C program is provided in `sor2d.c` and a MATLAB version in
`sor2d.m`. Implement the following versions in julia and compare the
timings of the different approaches:

1. A vectorized version.
2. A devectorized version.
3. Create a stencil function and refactor the stencil part of the computation.
4. Use the stencil function and implement using comprehensions.
5. Use a macro for the node updates.

  </BODY>
</HTML>
