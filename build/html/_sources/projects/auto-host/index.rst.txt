Auto-Host
=========

While working as a host/buss boy at Denny's, I found it difficult to clean
tables and seat the front. If there were customers at the front, I had to drop
what I was doing and seat the customers. By the time I got back I often forgot
which tables I bussed and needed wiping. There was a lot of extra walking around.
So I wrote Auto-Host, a simple web app that kept track of which tables were clean,
in-use, need bussing, or need wiping.

.. image:: https://i.imgur.com/vok5mBq.gif

I like to think of it as simple reference counter that keeps track of customers
as they walk in and walk out. I seat a customer at a Green table and tap it so 
it goes yellow. When that customer is done eating they pay up front at the cash
register and we scan their check. Their table number is also on that check. I 
can tap their table and it'll go from Yellow to Red.

If somebody else checks out a customer, they can also tap the table. Since I have
it running on a browser on my phone, I can also see when a table needs bussing.
It's very useful if I'm in the back dropping dishes off and I know if I need to
come back out with a buss tray or something.
