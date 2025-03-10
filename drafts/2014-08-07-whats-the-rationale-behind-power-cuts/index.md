# What's the rationale behind power cuts?


I found to my horror earlier this week that, everyday, there are 4 hours of
power cuts in Hyderabad. These are generally scheduled and occur in 2 batches
of 2 hours each. This particular week seems to have had awry timings and
durations via unscheduled power cuts.

Anyway, why power cuts[^1], and why unscheduled? The old rationale seems to be to
ration power to match supply. I'm not entirely convinced by this:

* A lot of usage is necessary and will happen at another time of the day if the
  power is cut. Examples include doing the daily laundry in the washing machine
  and ironing (pressing) clothes.

* An increasing number of homes are starting to have inverters and UPSes to
  manage these power outages. These devices tend to generally have an
  advertised combined storage and dispatch efficiency of around 80%. While these
  devices tend to power fewer appliances, their decreased efficiencies somewhat
  counter balance the effective power savings.

* The weather here is rather pleasant at this time of the year, removing the
  need for 24x7 air conditioners (and to an extent, geysers).

In fact, it is a rather easy experiment (with controls) to design and conduct
for the authorities that be at the electricity board. For a given locality, it
is fairly easy to measure the net power usage for

1. A week with unscheduled power cuts for *n* hours in the area.
1. A week with scheduled power cuts for *n* hours in the area.
1. A week with no power cuts at all.

Chances are somebody somewhere has this data already. I would be very
interested to see how much these figures differ by. If they do not differ by
much, maybe we need to think about a max-min fairness based power rationing
method[^2]. It would also be interesting to see how the power saved percentages
vary with *n*, the number of hours of power cut. I also suspect the
relationship would be sub-linear till the point of average inverter capacity.

There are also actual solutions out of this problem (other than people buying
inverters). Here are two immediate ones I can think of:

* Most houses here have a 3-phase connection. Blacking out two out of three
phases randomly will prevent people from continuously using high wattage devices
while allowing people to have some necessary access to power.

* The government investing in a low power fuse at each endpoint's meter will
allow the electricity board to implement a "low power mode" for each house.

Of course, either of the above systems can be gamed with some rewiring, but
that's sort of what's happening with inverters[^3] anyway.

Alright, it's 2014 outside and we are still talking about 15% power outages in
a metropolitan city in India. Maybe we should pretend the problem does not
exist. Anybody has a carpet I can sweep this under?


[^1]: I'm somewhat aware of the politics between the electricity board, office spaces, and the existence of certain sums of money that will prevent power being rationed for certain parties. I'm choosing to ignore the will-cut-power-to-bully argument and focus on the possibility of any scientific reasons.

[^2]: There must be a joke in here somewhere involving sine waves, Fourier transforms, a max voltage of 220V and a min voltage of 0V?

[^3]: Interestingly, the Kerala government [attempted](http://timesofindia.indiatimes.com/city/thiruvananthapuram/Consumers-should-explore-solar-option-for-inverters/articleshow/16975488.cms) to keep the usage of inverters in check. I have anecdotally heard that this is still an ongoing conversation / process.

