# CS-350 Portfolio Submission

## Summarize the project and what problem it was solving.
In the final project of our CS-350 course, we were to create a program that runs on the Texas Instruments CC3220S Simple Link MCU.  This program shows an example of a thermostat and takes user input from the input buttons on the left and right of the MCU
and adjusts the target temperature accordingly. Pressing the GPIO button 0 decreases the target temperature by one degreee celsius. Pressing GPIO button 1 increases the target temperature by one degree celsius.
The program uses a task scheduler and several tasks to read the input of the GPIO buttons, read the temperature of the TMP006 sensor, and report to a cloud service (or UART output) in given intervals. If the target temperature is below the actual temperature read by TMP006, the thermostat turns on the heat, indicated by GPIO led 0 output HIGH. Once the actual temperature is equal or greater than the target temperature, the GPIO led 0 output is LOW, indicating heating is off. This same task outputs data for the target temp, actual temp, heating state, and elapsed system time to the cloud service (UART output).

## What did you do particularly well?
I believe that something I did particularly well was creating a simplified method of reading the GPIO buttons and changing the target temperature. When the buttons trigger GPIO interrupt, I change the magnitude of temperature change to one, and the direction to either negative (left GPIO button) or positive (right GPIO button).

## Where could you imporve?
One area that I can absolutely improve is in the area of planning. I could have planned my program more thoroughly before developing code. In my code for the final project, I left artifacts of a state machine I was
going to implement for the project. I ultimately decided that a state machine wasn't necessary, as the tasks could handle the what would be a state, simply by being executed. There was no need to implement
active and idle states for a state machine when by nature each task implemented was idle when not executing.

## What tools and/or resources are you adding to your support network?
Within my support network, I am adding a more thorough knowledge in terms of research when it comes to problem solving. Some of our modules within this course quite literally left us to research information on our own to solve a problem and implement a solution. We've also experience additional debugging concepts that apply to debugging physical hardware.

## What skill from this project will be particularly transferable to other projects and/or course work?
I think the skill that I have gotten the most out of is the ability to plan and implement task schedulers. This really really will help with some future personal projects that I have on my mind. A few years ago I implemented a basic Christmas Lightshow with a Raspberry Pi. Now I have many RP2040 wireless MCUs that I can use as well, to create wireless hubs for different sections of the light show. Being able to implement a task scheduler and state machines will help tremendously with this idea.

## How did you make this project maintainable, readable, and adaptable?
This was acheived by implementing separate functions for specific functionality within the project. Each task was defined as its own function. The task scheduler also was implemented within the timer's ISR. Making this makes it easy to determine the where the different areas of logic are for each part of the program, as well as eliminating a need to filter through one large function to make a change. Providing separate functions for tasks also helps make the code a little more self-documenting.