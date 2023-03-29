# ADA_135 C NISIDIS AVA.ADA 2207
Personal repository for course ADA_135 at Ionian University

## Visualization and Sonification of Seismic Activity

This attempt consists of two distinct parts. In **Part I** (Lithosphere), we represent earthquakes as points in space, and in **Part II**, we discuss the possibility of directly sonifying data streams from seismographs.

***
### Part I: Lithosphere

<cite>Earthquakes as point-clouds</cite>

On the first part the goal is to visualize and represent seismic events (earthquakes) in the 3d or 2d space as a pointcloud.


[![Lithosphere Video on youtube](lithosphere_00.png)](https://youtu.be/JKl6PjuqT88)
<small>Youtube Video [Lithosphere](https://youtu.be/JKl6PjuqT88)</small>

##### Earthquake Event Keypoints:

- Location <small>(Longtitude & Lattitude)</small>
- Magnitude <small>(Richter)</small>
- Depth <small>(km)</small>
- DateTime <small>(UTC)</small>

In the current version of this project, each point inherits the properties of the corresponding earthquake event and also possesses the necessary properties and methods to visualize and sonify it.

#### Ways to Interpret and Correlate the data:

- Linearly with a fixed interval, each point is being added or lighten up after the other ignoring the time difference or the actual distance.
- Linearly with a fixed time interval, each point is added or illuminated after the other, ignoring the time difference or the actual distance.
  <small><i>Specifically, if we assume that event A occurs at t0 and event be at t1 then the interval is t0-t1. By this means it is expected to result in an output which has its own internal rhythm.</i></small>
- Non-linear using the centroids of the individual clusters. Events are separated into clusters using the Kmeans algorithm. By self-organizing the points based on their internal criteria it allows us to observe them in parallel threads, simultaneously.


##### Visualization Method

In the current application, the *saturation* of color represents the time of appearance, the hue of color represents the ratio of *magnitude* to *depth* (intensity), and the *magnitude* represents the size (radius) of each point, respectively.

##### Sonification Method

- Time distance is translated to the time interval for the MIDI triggers.
- Depth affects the tone (frequency)
- Magnitude affects the velocity
- and Location (physical distance among the events) is being transcribed to Reverb wetness.  


***
### Part II

<cite>Collect data in real-time (almost real time) from seismographs around the globe.</cite>

In this section, our goal is to sonify data by accessing a continuous stream derived from specific stations around the world. 

The inspiration for this idea comes from an audio experience where the listener stands in the center of a room surrounded by speakers. 

Each stream from the seismograph stations is audibly represented as a continuous sound signal emanating from the speakers placed around the room.


This part is segmented to distinct phases.

##### Phase A. Retrieve Data Sources

This section is generally more complex than Part II as the data is not always publicly available, making it difficult to obtain. However, the good news is that most of the data we need can be accessed through various networks depending on their location and the organization or institution that manages them.

By setting and pushing simple queries with this [builder](http://eida.gein.noa.gr/fdsnws/dataselect/1/builder) we are capable to retrieve useful data from the NOA (National Observatory of Athens) or directly acquiring data through the FDSN[^1]

##### Phase B. Acquire Data

Initially, most devices use the SEED format for exchanging data. 

In particular, there is a subversion of SEED[^10] called MiniSEED, which comes in different flavors, depending on the nature of the data and the capabilities of each Station[^5]

So far the most comon type of MiniSEED seems to be the STEIM2 compression. 

##### Phase C. Rectify and Resample Acquired Data

Upsampling from 100Hz to 48kHz, antialising order:15
no IFRs were applied

Listen to an audible test on [soundcloud](https://soundcloud.com/cnisidis/earthquake-stream)




##### Phase D. Render Data to Multichannel Audio
//TODO

##### Phase E. Represent Data graphically (optional)
//TODO








[^1]: [International Federation of Digital Seismograph Networks](http://www.fdsn.org/)
[^5]: Station: Every potential seismographic device which respects the FDSN convention. A Station has some standard characteristics such as a code, a channel, a network and a location.
[^10]: [miniSEED](https://ds.iris.edu/ds/nodes/dmc/data/formats/miniseed/)
