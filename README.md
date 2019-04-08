# SaunaModel
This package is estimate of how a lumped sum sauna would behave. A lumped sum system modeling means approximating each component of the system with one number. This is a rough and ready approximation: obviously, the stove isn't all one temperature, and the air has has a very complex fluid dynamics problem, which could heat a small sized sauna with the heat given off with all the computers needed to solve in granular detail.

You might ask why would I sink the time into modelling a sauna with differential equations. It sprung from a group chat where we were discussing the impact of adding a water tank to a sauna. I fired off some real preliminary calculations, then said I didn't have the time to write up the differential equations to do it right. The problem stuck with me, and I figured I had enough discussions abouth the thermal dynamics of a sauna to bump out a solution.

## Modelling the Sauna

### Components
Elements of the sauna include
- Fire
- Stove
- Air temperature
- Air humidity
- Walls and furniture of the room
- Floor of the sauna
- Air outside (both temperature and humidity)
- Mass of water on stove
- Temperature of water on stove

There are many other possible variables to consider, such as the effect of adding a water heater.
### Boundary Conditions
One way to make the system simpiler to deal with is to assume a constant value for some components of the system, and to drive some components with functions. In the default scenario:
- Floor of sauna is assumed to be 50 °F
- Outside temperature is assumed to be 50 °F
- Outside relative humidity is 30%
- The fire grows to a maximum temperature of 1200°F and a radius of .3 meters

### Heat transfer equations
Here is a short review of heat transfer. There are only a few equations that drive this process. For all equations below $A$ is area, $L$ is length, $T$ is temperature.
#### Conduction
Conduction is when heat moves through physical contact with objects. In the sauna, the main conductive aspect is the walls conducting temperature to the outside. Effective insulation will greatly reduce this mode of heat transfer.
$$k\frac{(T_{hot}-T_{cold})*A}{L}$$
where $k$ is the conduction coefficient, which is fairly straight forward to measure for many materials. To learn all you probably need to know about thermal conduction consult [Wikipedia.](https://en.wikipedia.org/wiki/Thermal_conduction)

#### Convection
Convection is the mode of heat transfer due to fluid flows. This mode of heat transfer is extremely common in a sauna. The heat transfer from a burning hot steam to your shoulders is one. Heat transfer from hot gas rising off the fire to the stove is another.
$$h(T_{hot}-T_{cold})*A$$
where $h$ is the convective coefficient. Convective coefficients can be approximated through a fairly complex process of determining Reynold's numbers and Nusselt's numbers. I used reference numbers to save time. To learn all you probably need to know about thermal convection consult [Wikipedia.](https://en.wikipedia.org/wiki/Convective_heat_transfer)

### Radiation
Radiation is the mode of heat transfer due to electromagnetic radiation. Heat moving like light, instantaneously, through the atmosphere. If you feel the heat coming off of something hot, it is probably radiation. The burning sensation in your shins from an oversized stove (cough, Benda's, cough) is from radiation.
$$\sigma\epsilon A (T_{hot}^4 - T_{cold}^4)$$
where $\sigma$ is the Stefan–Boltzmann constant (some universal constant), $\epsilon$ is the emissivity (black top has a high emissivity, white shirts have a lower one). I assumed that $\epsilon=1$ for the purposes of this model. [Wikipedia.](https://en.wikipedia.org/wiki/Thermal_radiation)

### Advection (mass transfer)
Heat is also transfered when hot air leaves the room and cold air flows in.
## Humans in the Sauna

## Commentary on development
I
