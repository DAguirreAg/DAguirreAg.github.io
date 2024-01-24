---
title: 'Simple energy cost study on running a home lab'
date: 2024-01-14T23:58:16+01:00
author: Daniel Aguirre
draft: false
tags: ["Homelab", "Energy cost", "Analysis"]
cover:
  image: images/simple_energy_cost_study_on_running_a_home_lab/european_electricity_prices.png
---

After the increases in Europe's electricity prices, I have decided to run some basic numbers to understand how much my homelab installation costs me, as well as to have some reference numbers to have an informed opinion when purchasing new devices.

For this analysis, I will start by calculating the cost per KWh as well as the yearly cost per W. I will proceed to estimate the rough power consumption of different devices to finally calculate the total cost of running them.  


## Cost per kWh and Yearly cost per W

The cost per kWh is relatively easy to obtain (specially for Europe as a the data is readily available in official sourcers). Below the main countries I am interested in (also adding non European countries to have as reference):

* The Netherlands: 0.475 Eur/kWh
* Spain: 0.1823 Eur/kWh
* Europe: 0.289 Eur/kWh
* USA: 0.1566 Eur/kWh
* Singapore: 0.1991 Eur/kWh

However, instead of working with those directly, I will calculate the **yearly cost per year per Watt**, as this will allow me to easily multiply with each devices power consumption to obtain the total cost of running a device 24/7.

* The Netherlands: 4.161 Eur/W/year
* Spain: 1.596948 Eur/W/year
* Europe: 2.53164 Eur/W/year
* USA: 1.371816 Eur/W/year
* Singapore: 1.744116 Eur/W/year

(These values are calculated by multiplying the electricity cost of each country times 24 hours times 365 days divided by 1000)

## Power consumption per device

The power consumption of each device varies greatly from manufacturer to manufacturer, however, I will take some rough estimates as to give us some idea of the numbers we are speaking about:

* Network switch (home): ~7 W
* Network switch (enterprise): ~20 W
* Raspberry Pi 3/4 (idle): ~7.5 W
* Raspberry Pi 3/4 (high load): ~15 W
* Harddrive: ~6 W
* Mini server: 200 W
* Desktop server: 450 W

## Yearly cost

Finally the cost calculation is quite straightforward. I will multiply each device by each countries yearly Watt cost. This gives us the following result:

{{<figure src="/images/simple_energy_cost_study_on_running_a_home_lab/table_yearly_cost_per_device_on_different_countries.png" title="Yearly cost of running devices on different countries." alt="Yearly cost of running devices on different countries." width="100%">}}

{{<figure src="/images/simple_energy_cost_study_on_running_a_home_lab/graph_yearly_cost_per_device_on_different_countries.png" title="Graph of Yearly cost of running devices on different countries." alt="Graph of Yearly cost of running devices on different countries." width="100%">}}


## Conclusions
 
By looking at the yearly cost numbers, we can deduce quite some interesting points:
* Servers (desktop and mini) are by far the main cost drivers. This makes sense as their power requirements is two orders of magnitude bigger than the other devices. However, this implies that **unless necessary (high loads, need for realibility, ...), we should try to avoid setting servers, as they skyrocket the cost of our setups.**
* Regardless of the little amount of power a device consumes, when the running period is long, the cost starts piling up. This means, that it may be **interesting to purchase devices with low power consumption if we will be making extended use of them.**
* As more devices are added to the setup, the cost of running the setup starts increasing considerably. This makes **cloud solution a good solution to consider**, as most of them provide some discounts when using them and they manage the services fully for you. 


## Sources
* [Electricity prices in Europe](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Electricity_price_statistics)
* [Singapore electricity prices](https://www.spgroup.com.sg/about-us/media-resources/news-and-media-releases/electricity-tariff-revision-for-the-period-from-1-Oct-to-31-Dec-2023)
* [Network switch power consumptions](https://homenetworkgeek.com/how-much-power-does-a-network-switch-use/)
* [How much energy does the raspberry pi consume in a day](https://raspberrypi.stackexchange.com/questions/5033/how-much-energy-does-the-raspberry-pi-consume-in-a-day)



