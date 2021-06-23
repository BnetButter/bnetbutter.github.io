Smart Mirror
============

Using the Leap Motion controller, I created a gesture controlled smart-mirror.
A monitor sat behind a two way mirror which gave the illusion that it was being
projected. This was my first javascript project using the React framework.

.. image:: https://i.imgur.com/CqJTPs6.gif

The difficult part about this project was not the programming. Designing a new
interface for controlling UI elements was difficult. It was critical to forgo emulating
a touch interface. For example, in order to move the NewsContainer, I had to
"grab" the container, then pull it as if I was pulling it off the screen, then move
it to where I want it to be. I can "drop" the container to fix the location.

Creating a menu was also challenging. Button's don't work well when there isn't
anything solid to press. I found that fixing the button position relative to my
palm was the best way to place the button.

Rotation is not a very common feature in UI Web design. You can't really rotate
your mouse. Nor can you rotate your finger on the screen. What I enjoyed most
out of this project is exploring new ways of interacting with devices.
Who wants smudges on their mirrors?
 