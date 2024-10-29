# tstools Package for R

I've been developing the tstools package for a long time. I've tracked versions of the
package back to at least 2012, but it was initially a collection of tools
I had already been using to teach my econometrics classes, so I'll just leave
it at "a long time".

This is the documentation website for the package. It takes a surprising
amount of time to write R package
documentation, and that's why it's never been fully documented or
uploaded to CRAN. I do have uploading it to CRAN as a long-term goal, so
that mnight actually happen at some point. I hope this website makes it
easier for others to use the package.

I believe this package still has value in spite of the large number of
R packages that are now available. An explicit design goal has been keeping
it as low-overhead as possible. I want others to be able to do introductory and intermediate
analysis of time series data without having to learn a bunch of programming
concepts or having to construct elaborate data structures. For the
most part, if either of those is required, that functionality isn't found in
this package. 

There's nothing wrong with the popular R frameworks of recent years
that require you to invest a bunch of time learning how to use them *so long as
you're a professional data analyst*. My target audience is the undergraduate
or graduate student encountering both R and time series analysis for the
first time. The new concepts those students learn should be time series,
not statistical programming, so I've made every attempt to stick to
functions and limit the number of arguments that have to be passed in.
This will make the tstools package unappealing to a lot of people, 
particularly those with professional programming backgrounds, because it does
not and will never provide general solutions to these problems.

# Design of This Website

I might upgrade the design some day. It's not a priority for now.
Also, I prefer plain websites, which reduces my motivation to make it pretty.
