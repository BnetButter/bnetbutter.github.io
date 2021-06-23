HWK System
===========

This was my first first real-world programming project. I wrote an entire
Point-of-Sale system for my restaurant business.

.. image:: _static/cover.jpeg

The system comprised of 3 Raspberry Pi's connected over WLAN. The POS controlled
the cash drawer and card reader. It sent order info to the cook station (below)
and drink station (above).

.. image:: _static/cook-display.jpeg

When an order is being made, the price is displayed to the customer by this LCD display

.. image:: _static/price-display.jpeg

The user sees this screen

.. image:: _static/create-order.png

Once the order is created, a receipt is printed

.. image:: _static/receipt.jpeg

The system was real time. Data was transmitted over websockets. When an order was placed, it was queued up and broadcast to receiver. 
When the order was fulfilled by (pressing Enter on the Key Pad), the orders were dequeued. While in queue however, they may be edited.

.. image:: _static/processing.png

We could also modify the menu in the POS system

.. image:: _static/edit-menu.png

We used a Verifone P400 Terminal provided through Stripe Payment.

.. image:: _static/terminal.jpg

