# 2020-Sensor-Miniproject
# Jarek Bartel & Nicholas Bart

The Fall 2020 Senior Design practice project involves using simulated sensors to test the overall temperature, occupancy, and CO2 level in a specified room at a specific time. 

# Task 0: setup Python Websockets

The greeting string issued by the server to the client is “ECE Senior Capstone IoT simulator”.

A sample of the simulation running in the terminal after websockets were set up:
[![Simulation](https://github.com/jarekab/images/blob/master/Screen%20Shot%202020-09-11%20at%2014.25.55.png)

# Task 1: Data Flow

Task 1 required that we edit one of the given documents in order to save the simulation data to a text file.

Snippet of python code added to client.py in order to save JSON data to a text file in real time.
[![client](https://github.com/jarekab/images/blob/master/Screen%20Shot%202020-09-16%20at%2019.26.55.png)

# Task 2: Analysis

For task 2 we had to run the server/client and collect data for 20 minutes. This data would then be saved into a .txt file.
We were tasked with finding the mean, variance, and probability distribution of the temperature, occupancy, and time interval.

The following screenshots are pictures of my code that I used to determine the required information:

[![part21](https://github.com/jarekab/images/blob/master/part2-1.png)
[![part22](https://github.com/jarekab/images/blob/master/part2-2.png)
[![part23](https://github.com/jarekab/images/blob/master/part2-3.png)
[![part24](https://github.com/jarekab/images/blob/master/part2-4.png)

It is worth noting that the time interval probability distribution looks similar to that of a binomial distribution.

# Part 3: Analysis

Part 3 required that we write our own code entirely that implements an algorithm to detect anomalies in the temperature sensor data.

The following screenshots depict the written code as well as the results of that code.

[![part31](https://github.com/jarekab/images/blob/master/Screen%20Shot%202020-09-15%20at%2021.21.42.png)
[![part32](https://github.com/jarekab/images/blob/master/Screen%20Shot%202020-09-15%20at%2021.21.50.png)

When ran, the code written for part 3 prints out every line where a temperature anomaly was detected.
To determine what was considered an anomaly, I googled the average temperature for each room type.
For pretty much every room type, OSHA recommended that the temperature stay between 20 and 25 degrees Celsius. So anything above or below is an anomaly.

Additionally, the algorithm is programmed to print the number of anomalies above 25 degrees as well as below 20. Along with this the percentage of "bad" data points is also printed.

A persistent change in temperature does not always indicate a failed sensor. For instance, the AC unit itself could be the problem. The bounds I presented for each room type is very reliable, between 20-25 degrees celsius.

# Part 4 conclusions

This simulation almost directly reflects potential real world data. All the info seems to be reasonable approximations of what the actual data might look like. The temperature mostly stays in a comfortable range.

The simulation, despite being a good reflection of the real world however, still has many flaws. Because the data is randomized, It doesn’t always match up with the data that came before it. The data jumps around and fails to remain consistent, despite the samples supposedly being taken only a few seconds apart. 


Initially, installing the python websockets library was difficult and confusing. However, after figuring out how to do so it became more clear what was going on. We cannot compare it to installing on other programming languages because we have never done so before. Despite this, programming in python was generally more straight forward and forgiving than programming in something such as C.

The better option greatly depends on whether or not the sensors have a way to store the data they collect in between server polls. If they do, then having the server poll the sensors would be the better option, because the constant uploading of the other option would lead to greater workloads for the server. If they don’t, then having the sensors reach out would be the better option. The other option in that scenario could lead to a loss of whatever data was gathered in between server polls.






