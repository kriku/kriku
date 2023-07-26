## Bluetooth keyboard

https://github.com/kriku/kpukboard-pcb

https://github.com/kriku/kpukboard-zmk

There is a lot of ways to create the keyboard. 

But first - lets see which steps is required to build a custom keyboard.

### Key press

Probably the simplest interface to interact with - the switch.
The main idea behind it - is detect the key press, detect transition between unpressed and pressed state.

The keypress have to change state of logic level.

More on logic level:
- https://en.wikipedia.org/wiki/Logic_level
- https://learn.sparkfun.com/tutorials/logic-levels/all

We have to decide which logic level for pin is ACTIVE, the other level will be INACTIVE.
Sometimes it calls ON and OFF state.

#### Direct pins

First solution in our list is direct pin connection.

<img src="/kriku/kriku/raw/main/projects/keyboard/images/direct-pin.png" height="100px">

Buttons create contact between input pin of MCU and GND. 

In that case we say that pin is in active state when low.

Or we can connect it to VCC if we decide that pin active state is when it's high.

Even with direct pins there is some problems.

First one is "floating pins".

Solution is pretty straightforward - use
[pull-up resistors](https://learn.sparkfun.com/tutorials/pull-up-resistors/all) (or pull-down)
on each switch.

<img src="/kriku/kriku/raw/main/projects/keyboard/images/direct-pin-pull-up.png" height="100px">

Second one is "contact bounce".

There are [differect solutions](https://forumautomation.com/t/what-is-contact-bouncing/5976) to this problem.

With MCU and amount of keyboard firmwares available open source - looks like software solution is simpler.

The problem with this schematic - we need unique pin and pull-up/down resistor for each button.

<img src="/kriku/kriku/raw/main/projects/keyboard/images/direct-pins.png" height="100px">

#### Simple matrix

Widely spread solution among keyboard enthusiasts.

It's kind of easy to come up with.

<img src="/kriku/kriku/raw/main/projects/keyboard/images/matrix.png" height="100px">

#### Not that simple matrices

https://kbd.news/The-Japanese-duplex-matrix-1391.html

https://kbd.news/Improved-square-matrix-1415.html
