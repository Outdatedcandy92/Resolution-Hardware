
# Preface

## What is this?

This is a beginner friendly introduction to electronics and hardware.

You do not need:

- Any prior experience
- Any components
- Any tools
- Any physics background

We are going to build intuition first.

This guide is designed to go wide, not deep. You’ll touch a lot of topics. You won’t master any single one yet, and that’s intentional. The goal is exposure and understanding, not specialization.

We’ll start entirely in simulation using [**Falstad Circuit Simulator**](https://www.falstad.com/circuit/circuitjs.html), so you can experiment without buying anything. 

Once you’re comfortable, we’ll move toward real hardware and PCB design. By the time your physical components arrive, you’ll already understand what you’re doing.

## What this is not

This is not:

- A deep electrical engineering course
- A complete guide to circuit design

We will use some formulas in this that require some knowledge of algebra (really basic) but we're not going to be going into any calculus.

The goal is to not let ideas get to abstract here.

This is also not a purely theoretical guide. Everything we talk about will be something you can simulate immediately and later build physically.

## What is Electronics

![](https://cdn.hackclub.com/019cb669-abe4-7e6a-b851-6ca4270e5eac/Pasted%20image%2020260302215443.png)

Electronics is the art of controlling electricity to do useful things.

That’s it.

When you use your phone, connect to WiFi, play music through speakers, or turn on a microwave, electronics is what makes it happen.

At its core, electronics is about guiding tiny flows of electric charge through carefully arranged components so that we can:

- Send information
- Process data
- Amplify signals
- Control machines
- Light things up
- Make decisions using logic

Over the last century, electronics went from large glowing vacuum tubes to microscopic transistors packed by the millions inside tiny chips. Today, devices that fit in your pocket contain more computing power than room sized machines from the past.

*The first transistor*

![](https://cdn.hackclub.com/019cb669-ae17-7287-a407-6e87183d8453/Pasted%20image%2020260302233912.png)

*A modern through hole transistor*

![](https://user-cdn.hackclub-assets.com/019cb6c9-2a34-73de-84b3-effe60b16914/Pasted%20image%2020260303215834.png)

It all comes down to a few core ideas:

- Voltage
- Current
- Power
- Components connected in circuits

If you understand those, you understand the foundation of everything from a blinking LED to a computer processor.

There is one tricky part: you cannot see electricity directly. You cannot touch it safely, smell it, or hear it. That means we have to think a little abstractly at first. We use models, diagrams, and measurements to understand what is happening.

The good news is that the rules are consistent. Once something makes sense, it keeps making sense. The same principles apply whether you are building a tiny sensor circuit or designing a full PCB.

In this guide, we will focus on building intuition. You will learn what the important quantities mean, how components behave, and how circuits fit together.

We are going to build it, simulate it, and *eventually* hold it in your hands.

## What You'll Learn

This guide takes you from zero hardware knowledge to designing your own boards.

Here’s the journey:

- Learn the core ideas: voltage, current, power, and how circuits work
- Understand analog components like resistors, capacitors, diodes, LEDs, and transistors
- Simulate real circuits using **Falstad Circuit Simulator**
- Design and lay out your own PCB
- Build an analog radio from your own design
- Move into digital electronics and integrated circuits
- Design and build your own development board

By the end, you’ll have designed real hardware.


---

Now that that’s out of the way, let’s actually start.

Before we jump into simulations, you need a quick rundown of what everything is and how it works. The beginning will be a little more text heavy, but it’s important. Once the foundations are clear, everything we build later will make a lot more sense.


# How Electricity Works

Electricity is all about moving energy through a circuit.

Think of a circuit like a closed loop of pipe filled with water:

- The water is like electric charge.
- The pump pushing the water is like a battery.
- The pipes are like wires.

If the pump pushes, water flows. In a circuit, the battery *“pushes”* the charge, and that movement is called **current**.

The push that drives the flow is called **voltage**.  
Voltage is the electrical pressure that makes charge want to move. A stronger push means more potential for flow.

But a push alone doesn’t do anything, you need a complete loop. If the pipe is broken, no water flows. Likewise, in a circuit, current only flows if there’s a complete path.

So in simple terms:

- **Voltage** = the push
- **Current** = the flow

When we measure them, there is a key detail

- **Voltage** is always measured across two points. It tells you the difference in push between those points, like the pressure difference between two spots in a pipe

- **Current** is measured at a single point in the circuit. It tells you how much flow is passing through that spot, like counting how much water goes through a section of pipe

Electronics is all about controlling both  
You decide how strong the push is, how much flows, and what the flow passes through

# Simulating Circuits

## Meet Falstad

You’ve learned the basics of what electricity is and how it flows. Now it’s time to get your hands *(virtually)* dirty. Before we touch any real wires, we’re going to use a tool called **Falstad Circuit Simulator**. It’s like having a digital workbench where you can safely experiment, connect parts, and see electricity come to life right inside your browser.

![](https://cdn.hackclub.com/019cb669-b718-742c-9164-7df10fe5186e/20260303-0446-53.7206403.gif)

Think of Falstad as a **sandbox for learning electronics**. You can drag and drop components like resistors, wires, and LEDs, then watch little dots race around the screen representing current flow. It’s visual, interactive, and much more exciting than staring at static diagrams.

### Why We’re Using Falstad

Let’s be honest, you probably don’t have a pile of electronic components sitting on your desk right now. You might not have a breadboard, resistors, or even a multimeter. That’s totally fine. Falstad gives us a way to explore circuits without needing any of that.

Falstad lets us **simulate real circuits** and **see what’s happening inside them**, like how voltage and current change over time. You can even open fancy little graphs that show how things behave as you adjust values.

And compared to drawing static schematics on paper, this is way more fun and interactive. You can actually **watch** the circuit come alive and see how energy moves through it in real time.

### Getting Started

To get started first head on over to [falstad.com/circuit/circuitjs.html](https://falstad.com/circuit/circuitjs.html)

By default, there's a circuit on the canvas. Get rid of it by either selecting and deleting the parts, or go to **File → New Blank Circuit** for a clean slate.

![](https://cdn.hackclub.com/019cb669-c46a-7f73-940d-cdea6e4d60b4/20260303-0453-03.4229243.gif)

Now the black space is your **canvas**, drag to pan, scroll to zoom, click to place stuff.

**Top bar:** Commonly used components (voltage sources, resistors, LEDs).  
**Right sidebar:** Run/pause simulation, speed control, reset button.

![](https://cdn.hackclub.com/019cb669-ce44-7274-94df-a08fe43a7042/Pasted%20image%2020260302235114.png)

## **First Component: Voltage Source (The Push)**

Let's drop in our first voltage source. Remember the water analogy? Voltage is like water pressure pushing through a pipe. The voltage source provides that push.

Select the **DC voltage source** symbol from the top bar (looks like a battery: long line + short line), then left-click and drag to place it on the canvas.

![](https://cdn.hackclub.com/019cb669-d125-7800-988e-b947a7904cea/20260303-0454-02.1827950.gif)

This symbol represents a **battery/DC voltage source**.

- **Long line** = positive (+) side (high pressure)
- **Short line** = ground or 0V (reference point, zero pressure)

We'll connect stuff between these two points to create pressure differences that make current flow.

#### Resistors

Next we need to give that voltage somewhere to flow. Enter the **resistor**, which is like a skinny section of pipe in our water analogy. It controls how easily current can flow through the circuit.


Find the resistor symbol on the top bar (looks like a zigzag line), click it, then drag to place it near your voltage source. Now grab the **wire tool** (usually looks like a straight line) from the top bar and connect one end of the voltage source to one end of the resistor. Then connect the other ends together to make a complete loop.

![](https://cdn.hackclub.com/019cb669-d5e6-7faa-96d1-561571c2471d/20260303-0455-05.7699513.gif)

Hit **Run** on the right sidebar. Boom! You should see little green dots racing around your loop. Those dots represent **current flow**. The voltage source is pushing, the resistor is restricting, and you can actually _watch_ the energy move.

You can also right click the resistor and click on view in new scope to basically have a Voltage and current over time graph to visualize the values over time as you change stuff up.

![](https://cdn.hackclub.com/019cb669-da3e-7cb6-87ee-bc5ba6b8917b/Pasted%20image%2020260302235548.png)

Try clicking directly on the resistor. A little menu pops up where you can drag the value lower or higher. Make it smaller and watch the green dots speed up. Make it bigger and they slow down. That is resistors in action, controlling current flow in real time.

![](https://cdn.hackclub.com/019cb669-e526-7ed8-8162-745195d702d6/20260303-0456-21.8603440.gif)

#### LEDs

Now let's make something glow. An **LED** (Light Emitting Diode) is like a tiny light bulb that only lights up when current flows through it the **right direction**.

To place an LED, right click anywhere on the canvas, go under **Outputs and Labels**, then click **Add LED** to place one. You'll notice it looks like a circle normally, but when you hover over it, it shows a triangle with a line at one end. That line marks the **negative side** (cathode) of the LED. LEDs only work when connected one specific way: **positive voltage → LED → ground**.

While we're at it, let's add a **switch** to control if the LED is on or off. Right click → **Passive Componenets** → **Add Switch**.

![](https://cdn.hackclub.com/019cb669-fb04-7f9a-ad81-b580e978c2e7/20260303-0459-18.5679297.gif)

Wire it up like this: voltage source → switch → LED (line side to ground) → back to voltage source. Hit **Run**. Flip the switch closed and the LED should glow red! If not, the green dots stop at the LED. That's the diode teaching you about direction. Flip the LED around and try again.


##### Checking Voltage and Current (Scopes!)

Right click the LED → **Show in New Scope** (remove old graphs first by right clicking them → **Remove Scope**). Hover over the graph: you'll see **~5V across the LED** (matches our battery) but **56A of current** and **283W of power**.

![](https://cdn.hackclub.com/019cb66a-035f-7b64-84a0-efc9f837281b/20260303-0500-50.0372465.gif)

![](https://cdn.hackclub.com/019cb66a-0bb6-761a-a950-7f93a327d172/Pasted%20image%2020260303000252.png)

That's _way_ too much! A desktop computer idles at 60-150W. Without resistance, current rushes through like water through an open pipe. In real life, the LED would burn out instantly.

##### Adding a Resistor (The LED's Best Friend)

That's why we add a **series resistor** before or after the LED. Right click → **Add Resistor**, place it between the switch and LED.

![](https://cdn.hackclub.com/019cb66a-1476-7b31-ac61-798432102fd9/20260303-0504-04.1961304.gif)

Run it again. Now current drops to **~3mA** (milliamps), which is perfect. The LED glows safely, just like in real circuits. The resistor chokes down the current so your LED lives a long happy life.


#### Capacitors: Storing Electrical Pressure

A **capacitor** is like a tiny bucket that stores electrical pressure (voltage). Connect it to a voltage source and it slowly "fills up." Disconnect it and it slowly "empties" into whatever's connected.

Right click → **Passive Components** → **Add Capacitor**. Place it in parallel with your LED (both ends connected to the same two points)

**Try this:** Voltage source → switch → resistor → LED → ground, _plus_ capacitor across the LED. Close the switch. Now notice how when you close and then open the switch the LED gradually dims instead of just 

![](https://cdn.hackclub.com/019cb66a-21e2-79f0-9ce8-0d6524f7939c/Pasted%20image%2020260303000523.png)

If you look at the graph down below which shows voltage and current across the LED you'll be able to visualize how the capacitors stored energy is used and how current is gradually dropped down to zero instead of instantly. 

Right click **capacitor** → **Show in New Scope**. Close switch → voltage **spikes instantly to 5V**, current shows a sharp pulse then zero. Open switch → voltage **ramps down slowly** as capacitor discharges.

![](https://cdn.hackclub.com/019cb66a-24d6-73bc-98b0-457aec42a02a/20260303-0506-43.6923366.gif)

Now experiment by changing the values of the **resistor** and **capacitor**. Click on each one and drag their sliders around. You'll notice something interesting: with **higher value resistors and capacitors**, the LED stays lit up much longer after you open the switch.

This happens because you've created an [**RC circuit**](https://en.wikipedia.org/wiki/RC_circuit) (Resistor + Capacitor circuit). Here's the magic:

#### How RC Circuits Control Time

Think of the **resistor** as a narrow garden hose and the **capacitor** as your bucket.

- **Big resistor + big capacitor** = super narrow hose + giant bucket. Takes forever for bucket to drain.
- **Small resistor + small capacitor** = wide hose + tiny bucket. Drains almost instantly.

The resistor controls **how fast** the capacitor can empty (current flow rate). The capacitor controls **how much** voltage it can store (bucket size).


**Try this:**

- Set resistor to 10kΩ (pretty big) + capacitor to 10µF (decent size) → LED glows for seconds
- Crank resistor to 100kΩ + capacitor to 100µF → LED stays lit for 10+ seconds!

This exact trick makes timing circuits, blinking lights, and even camera flashes work. Bigger RC values = longer delays.

## Make Something Cool!?

	FYI, please make sure to track your time using Lapse: lapse.hackclub.com

This guide showed you the ropes: voltage sources, resistors, capacitors, LEDs, switches, diodes. **Now comes the real electronics learning: doing + researching.**

Hardware isn't learned from reading. It's learned by:

- Breaking circuits (then fixing them)
- Googling your problems
- Finding solutions, tweaking them, making them yours

**Your Challenge:** Create something **creative + unique** using **ONLY** the components from this guide:

- Voltage sources (Only DC)
- Resistors
- Capacitors
- LEDs (+ series resistors)
- Switches, diodes, wires

**Goal:** A **self-running light effect** that uses **RC timing** to do something visually cool. Aim for something complex enough that it takes a few hours to get right with research.

**Some Examples to spark ideas**

- Chaser effect: brightness "moves" between 2 LEDs
- 3 LEDs light up one-by-one (1s delays), then fade together


Your project workflow should ideally look something like this:

- **Brainstorm** cool ideas or google "cool RC LED circuits" for inspiration
- **Break it down:** How can I recreate that using just RC timing?
- **Research values:** Search RC time constant calculator, estimate R/C needed
- **Build + test** in Falstad
- **Debug:** Scope voltages/currents, google "weird scope behavior [details]" or ask forums
- **Iterate:** Adjust values, add diodes, rewire until perfect
- **Polish:** Clean layout, labels, export to share


## Submitting

Coming Soon!
