# Underground system

## Context

We want to model an underground system, composed of several elements: stations, lines, tracks, track sections, and trains. 

* An underground network is composed of lines, which are sequences of stations connected by tracks. In a line, each track is connected to the next and previous tracks of the sequence, except for the first and last, which are connected to the origin and destination stations of the line (which may be the same), respectively. 
* Stations represent points in the network where trains regularly stop so that passengers can get on or off. 
* Several trains can be in the same station at the same time. 
* Each track connects two consecutive stations and has two sections, one for each directions of travel. 
* A station may belong to more than one line, and therefore be connected to more than two tracks.
* Trains are the objects that move through the network. At any given time, each train must be located either at a station or on a section of a track. 
* For safety, at any given time, there must be at most one train on each section of track. 
* Each train services one line only, and therefore can only move through the tracks of that line.
* A train can be moving, if it is on a section of track, or stopped at a station.
* Trains go from the initial station of the line to the final station, in one direction, and then return, in the opposite direction, unless the line is circular, i.e., the initial and final stations are the same. In this case, trains always follow the same direction. 
* All lines have trains moving in both directions.
* All the main elements of a railway system have a unique name (a string of characters). 

## Questions

You are asked to develop in UML, using the USE tool:

(a) A class diagram with the elements described above and the relationships between them.
b) Specify all the constraints and conditions expressed in the text on the elements of the model. 
c) 

1. Develop a UML class diagram with the structure of such a system, with all the elements mentioned above, the relationships between them, and all required integrity constraints.

2. Specify in OCL the following query operations:

    * Line::numTrains(): Integer, which returns the number of trains currently operating a line. 
    * Train::position(): String, which returns the name of the track section where a moving train is located. If the train is stopped at a station, it returns the name of the station. 
    * Line:numTracks():Integer, which returns the number of tracks that make up the line.

3. Model the behavior of the system by specifying the operations required to represent trains moving through the network,  including their pre- and post-conditions. Train movements should respect the integrity constraints of the system, in particular the fact that at most one train can be in a track section in a given moment in time (otherwise it has to wait in the station), or how they traverse the line they belong. 

4. Create an object model with at least 2 lines, each with 5 stations. At least two stations should belong to the two lines. Consider 5 trains moving through the network, and simulate the system asuming that every train should remain in a station for at least 1 time step, and traversing a track section takes two time steps (one to the middle, one to the next station).
