Welcome to the world of electronics and Raspberry Pi! Blinking an LED is the "Hello World" of hardware projects, and it is the perfect place to start.

Here is your complete, beginner-friendly, step-by-step guide to safely connecting and programming your LED.

📺 Watch the Full Project Video on YouTube: <https://youtu.be/rtchmPcH5b4>

Useful tool for circuit and [pcb layout](https://design.jlcpcb.com/?from=makerio_layout).

## **Step 1: Gather Your Components**

To build this project, you will need:

1. **Raspberry Pi Pico** (with pins soldered on so it can plug into a breadboard).
2. **1x LED** (Light Emitting Diode, any color).
3. **1x 220-ohm Resistor** (Color bands: Red, Red, Brown, Gold).  
   **Note:** The resistor is crucial. It slows down the electricity so the LED doesn't burn out.
4. **A Breadboard** (used to plug in components without soldering).
5. **2x Jumper Wires** (Male-to-Male).
6. **A Micro-USB Cable  
   Important:** Make sure it is a "Data and Sync" cable, not just a charging cable, otherwise your computer won't see the Pico!

## **Step 2: Understand the Parts Safely**

Before plugging anything in, let's look at the parts:

⚠️ **Safety First:** Always make sure your Raspberry Pi Pico is unplugged from the computer while you are building the circuit.

- **The LED** has a right and wrong way to plug in. It has two legs:
  - **Long Leg (Anode):** This is the Positive (+) side. Electricity goes in here.
  - **Short Leg (Cathode):** This is the Negative (-) side. Electricity goes out here.
- **The Resistor** has no polarity. You can plug it in in either direction.

## **Step 3: Connect the Hardware**

We will use **GPIO Pin 15 (GP15)** to control the LED. If you look at your Pico with the USB port facing up, GP15 is the bottom-right pin (Physical Pin 20).

### **Wiring Instructions:**

1. Push your Raspberry Pi Pico into the breadboard.
2. Connect one end of a jumper wire to the row where **GP15** is located.
3. Connect the other end of that jumper wire to an empty row further down the breadboard.
4. Take your **220-ohm resistor**. Plug one end into the same row as your jumper wire. Plug the other end into a new, empty row.
5. Take your **LED**. Plug the **Long Leg (+)** into the same row as the resistor. Plug the **Short Leg (-)** into a new, empty row.
6. Connect a second jumper wire from the row with the **Short Leg (-)** back to a **GND (Ground)** pin on the Pico. _(Physical Pin 18 is a Ground pin, located right next to GP15)._

**In simple terms:** The electricity travels out of GP15, through the resistor, through the LED (lighting it up), and back into the Pico through the Ground (GND) pin.

## **Step 4: Set Up the Software (Thonny IDE)**

To write code for the Pico, you need a free program called Thonny.

1. Download and install Thonny from [thonny.org](https://thonny.org).
2. Open Thonny.
3. Plug the Micro-USB cable into your computer.
4. Hold down the white **BOOTSEL** button on your Pico, plug the other end of the USB into the Pico, and _then_ let go of the button.
5. In Thonny, look at the bottom right corner. Click where it says "Python" (or similar) and select **MicroPython (Raspberry Pi Pico)**. If it prompts you to install MicroPython, click "Install" and wait for it to finish.

## **Step 5: Write the Code**

Copy the following code and paste it into the large main text area in Thonny:

import machine

```
import time
# Set up GP15 as an output pin so it can send electricity out
led = machine.Pin(15, machine.Pin.OUT)
# Create an endless loop
while True:
    led.on()         # Turn the LED on
    print("LED ON")  # Print a message to the computer screen
    time.sleep(1)    # Wait for 1 second
    led.off()        # Turn the LED off
    print("LED OFF") # Print a message to the computer screen
    time.sleep(1)    # Wait for 1 second
```

### **How the code works:**

- import machine lets the Pico talk to its physical hardware pins.
- import time gives us the ability to add pauses (delays) in the code.
- machine.Pin(15, machine.Pin.OUT) tells the Pico that GP15 is going to be used to push electricity out to a component.
- while True: creates a loop that runs forever.
- time.sleep(1) tells the Pico to do nothing for 1 second before moving to the next line of code.

## **Step 6: Run the Project**

1. In Thonny, click the **Green Play Button** (Run current script) at the top of the screen.
2. Thonny will ask where you want to save the code. Select **Raspberry Pi Pico**.
3. Name the file main.py and click save.  
   **Pro Tip:** Naming it main.py is a special trick. It tells the Pico to run this code automatically whenever it receives power, even if it isn't connected to a computer!

🎉 **Congratulations!** Your LED should now be blinking on for one second, and off for one second. You have successfully built your first hardware project!
