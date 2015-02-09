---
layout: post

title: First Prototype
subtitle: "Design and Results"
cover_image: blog-cover.jpg

excerpt: "Build details and results for our first prototype design."

author:
  name: Nathan Jarus
  gplus: +LinuxMercedes
  bio: Tinkerer
  image: nate.png
---

This initial prototype was designed to be relatively simple to make with tools I had in my basement and materials I could get from the local hardware store. 
I've made three of these, now, and the process changes a little each time as I get better at anticipating what needs to happen. 

We made it from a 2' length of 1" dowel rod with a pocket routed in one end to hold a pair of 1"x1/2"x1/4" aluminum electrodes.
Dowel rod was cheap, and we know that things under about 1" are pretty easy to pound into the ground, especially if they are pointed and persuaded with a properly sized fence-post hammer. 
Since we'll be passing a current between probes buried in the ground, we have to worry about electrolysis ocurring between the probes. 
In addition, we want to avoid using materials that will form a galvanic cell when buried in earth. 
As such, we've chosen aluminum, instead of copper or galvanized steel, for our sensor probes.
Ultimately, we will probably go with stainless steel, but it's not locally available where I live. 

![First prototype](/images/posts/2015/02/08/1-complete.jpg)

Each sensor probe has a hole drilled in it, allowing us to crimp ring terminals onto a wire and attach them to the sensor. 
The crimps serve a second purpose of spacing the probes out so they don't short out inside the post.
![Connection detail](/images/posts/2015/02/08/1-detail.jpg)

We can then wire it up in a simple voltage divider circuit to give us a nice analog input for an arduino: 
![Circuit](/images/posts/2015/02/08/circuit.jpg)
![Arduino](/images/posts/2015/02/08/arduino.jpg)
Note that we're actually powering it across two digital I/O pins, which allows us to 'float' the sensor when we're not reading it. 
This reduces the amount of electricity we're dumping into the ground, and therefore lessens electrolysis corrosion and increases battery life.
As it turns out, it also keeps multiple sensors in the same bucket from interfering with each other by providing alternate paths to ground. 
(Note: by bucket, I mean a literal bucket of water, which is fantastic for basic sensor testing).

A few lessons we learned from this prototype: 
1. Routing round stock in a straight line is tricky
2. Assembling the sensor probes is difficult
3. Ring terminals introduce needless complexity; these probes probably won't ever be disconnected
4. Since water can get inside the sensor, sensor readings tend to significantly lag physical changes

To fix the crookedness of the router cuts, I made a little jig that gives a flat surface to hold against the router table fence. 
![Jig](/images/posts/2015/02/08/jig-1.jpg)
![Jig against fence](/images/posts/2015/02/08/jig-2.jpg)

It cuts pretty straight, but you also have to not be a moron and feed the router so that it pushes the post into the fence instead of pulling it away...
![Jig cut](/images/posts/2015/02/08/jig-cut.jpg)

Finally, I skipped the ring terminals and instead put a small piece of plastic cut from a clamshell package between the probes to isolate them. 
I also assembled everything with a heavy dose of silicone caulk, which waterproofs the inside of the sensor and gives us a much speedier reaction time. 
One side effect of this is that our ideal voltage divider resistance has changed, so that 330 ohm resistor will probably get much smaller. 
![Silicone](/images/posts/2015/02/08/2-silicone.jpg)

For more fun technical notes on things including what 'ideal voltage divider resistance' means, check out the [arduino sketch](https://github.com/streed/farm/blob/11820bb0a3ebbf2a57b61098e9bfcadb6f4f15cd/Prototypes/1/sketch/sketch.ino) we've been using to test this stuff. 

From here, we'll be doing some in-soil testing (once the ground stops being frozen) and working to improve the sensor design and the microcontroller code. 
