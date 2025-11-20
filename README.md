# System Programming Lab 11 Multiprocessing
This program is an extension of a mandelbrot image generator, which adds the use of mutiprocessing to efficiently generate multiple images at once.
**fork()**, and some mathematics are included to generate **exactly 50 images** using an amount of processes given by the user. The 50 images are incrementally changed,
in this case the images gradually zoom out when view in order. The 50 images are then transformed into 50 frames for a "movie", which can be generated using the cmd
line (see more details below).

## How to Use
First, issue the command '**make**'. This will compile the source code and create the executable.

Second, issue the command '**./mandel -c [number of images]**', replacing the bracketed text with the number of desired processes, such as './mandel -c 20'.

Third, to create the movie file, use 'ffmpeg -imandel%d.jpg mandel.mpg' and your 50 frame movie will be generated in your directory.

## Time Data
I analyzed the times that it took to complete making 50 images by running the executable. Below is a graph depicting the relationship from 1 to 20 processes:


## Conclusions
The graph shows an exponentially decaying function, where the more processes take place at the same time, the faster the program will complete the task. This
makes sense, as distributing the workload is always better than putting it all on one core. Using less processes may save energy and power overall, but good computing
typically depends on speed.
