# System Programming Lab 12 Multithreading
This program is an extension of a mandelbrot image generator, which adds the use of mutiprocessing to efficiently generate multiple images at once.
**fork()**, and some mathematics are included to generate **exactly 50 images** using an amount of processes given by the user. The 50 images are incrementally changed,
in this case the images gradually zoom out when view in order. The 50 images are then transformed into 50 frames for a "movie", which can be generated using the cmd
line (see more details below).

The Lab12 edition has added multithreading to the implementation which makes use of the mandelbrot's compute_image function to run multiple times at once to increase the speed of the image generation. **pthread_create()** and **pthread_join** are the main functions used to implement this. Like the multiprocessing program, the user may enter the amount of threads the program will use to generate the mandelbrol frames. 

The default amount of child processes and threads is 1 unless the user specifies otherwise.

## How to Use
First, issue the command '**make**'. This will compile the source code and create the executable.

Second, issue the command '**./mandel -c [number of processes] -t [number of threads]** ', replacing the bracketed text with the number of desired processes, such as './mandel -c 20 -t 20'. They can be in either order.

Third, to create the movie file, use 'ffmpeg -imandel%d.jpg mandel.mpg' and your 50 frame movie will be generated in your directory.

## Time Data
I analyzed the times that it took to complete making 50 images by running the executable. Below is a graph depicting the relationship from 1 to 20 processes:


I also analyzed the times with different combinations of child processes and threads:



## Conclusions
The "Time vs. Processes" graph shows an exponentially decaying function, where the more processes take place at the same time, the faster the program will complete the task. This makes sense, as distributing the workload is always better than putting it all on one core. Using less processes may save energy and power overall, but good computing
typically depends on speed.

The Table below the graph show a sweet spot of efficiency at 20 threads and 10 processes. It proved to have the fastest time of all the combinations. The number of threads had a substantially higher impact on speed than the number of child processes, since the operation of computing images was workload-heavy, so easing it with multithreading truly made a difference. Also, very high amounts of threads and processes (ex. 20 and 20) did not have the fastest completion time, probably due to hardware limits, bottlenecking, etc.
