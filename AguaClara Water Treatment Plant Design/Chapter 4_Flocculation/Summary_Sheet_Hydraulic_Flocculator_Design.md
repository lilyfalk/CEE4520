# Hydraulic Flocculator Design Summary Sheet
Welcome to the **fourth** summary sheet of CEE 4540! These documents will be guides and references for you throughout the semester. Since Professor Monroe's class time is limited, so too is the amount of material he can fit on the slides while ensuring that they remain understandable. Thus, these summary sheets will supplement the powerpoints by going into further detail on the course concepts introduced in the slides.

Equations, universal constants, and other helpful goodies can be found in the [aide_design repository on GitHub](https://github.com/AguaClara/aide_design/tree/master/aide_design "aide_design"). Most equations and constants you find in these summary sheets will already have been coded into aide_design, and will be shown here in the following format:  

Variable: `pc.gravity`  
Function: `pc.area_circle(DiamCircle)`.

The letters before the `.`, in this case `pc`, indicate the file within aide_design where the variable or function can be found. In the examples above, `pc.gravity` and `pc.area_circle(DiamCircle)` show that the variable `gravity` and function `area_circle(DiamCicle)` are located inside the [physchem.py](https://github.com/AguaClara/aide_design/blob/master/aide_design/physchem.py) (`pc`) file. You are strongly recommended to look up any aide_design equations you plan to use within in their aide_design file before using them, even if they are given here in this summary sheet. This is because each equation has comments in its original file describing what the specific conditions are to using it.

For the most part, [hyperlinks in these documents will contain supplementary information](http://likethis.com/ "This link does not go anywhere"). The information contained in the linked external sites is there in case you don't feel completely comfortable with a concept, but is not necessary to learn thoroughly and will not be tested.


<br>
<br>


---


<br>
<br>

## Table of Contents
Please use this table to control/command find the sections you are looking for.
#### **Section 4: Hydraulic Flocculators, the AguaClara Approach**    
**4.1)** Introduction to Hydraulic Flocculation   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Collision Potential, $\bar G \theta$, and Energy Dissipation Rate, $\varepsilon$  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Generating Head Loss with Baffles    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Flocculator Efficiency  
**4.2)**  AguaClara Design of Hydraulic, Vertical Flow Flocculators  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Input Parameters    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Designing Physical Dimensions  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;Designing Hydraulic Parameters

<br>
<br>


---


<br>
<br>

## Section 4: Hydraulic Flocculators, the AguaClara Approach
### Important Terms
1.  Collision potential  
2. Energy dissipation rate
3. Baffle
4. Baffle module

### Important Equations   
1.

## 4.1) Introduction to Hydraulic Flocculation
The reason that flocculation is widely used in water treatment is because of sedimentation. Sedimentation is the process that actually removes particles like clay, dirt, organic matter, and bacteria from water. As you learned in the previous chapter on Rapid Mix _**(DOUBLE CHECK THAT THIS IS IN RAPID MIX ONCE RAPID MIX IS WRITTEN)**_, sedimentation is the process of particles 'falling' out of water due to density stratification, and its governing equation is:

$$V_t = \frac{d^2 g}{18 \nu} \frac{\rho_p - \rho_w}{\rho_w}$$  

Such that:  
$V_t$ = terminal velocity of a particle, its downwards speed if it were in quiescent (still) water  
$d$ = particle diameter  
$\rho$ = density. $p$ stands for particle, $w$ stands for water

To increase $V_t$ and make sedimentation more efficient, floccuation aims to increase the diameter $d$ of the particles. This is done by applying a coagulant to the dirty water and helping the coagulant to stick evenly to all particles during Rapid Mix _**(DOUBLE CHECK THAT THIS IS IN RAPID MIX ONCE RAPID MIX IS WRITTEN)**_. Being covered in coagulant allows the particles to collide, merge, and grow bigger during flocculation.

So our goal in designing a flocculator is to facilitate particle collisions. How can we do this?

### Collision Potential, $\bar G \theta$, and Energy Dissipation Rate, $\varepsilon$
**Collision potential $(G \theta)$** is a term with a very straightforward name. It represents the magnitude of potential particle collisions in a fluid. It is a _dimensionless_ parameter which is often used as a performance metric for flocculators; big $G \theta$ values indicate lots of collisions (good) while small values indicate fewer collisions (not so good). AguaClara flocculators usually aim for a collision potential of 37,000. _**WHY DO WE SHOOT FOR 37,000?**_ The value for collision potential is obtained by multiplying $G$, a parameter for fluid shear with units of $\frac{1}{[T]}$, and $\theta$, the residence time of water in the flocculator, with units of $[T]$. $\theta$ is intuitive to measure, calculate, and understand. $G$ is a bit more difficult. First, an intuitive explanation. See the image below, which shows the velocity profile of flowing water.

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/G_velocity_profile.jpg?raw=true" width=500>


$G$ measures the magnitude of shear by using the velocity gradient of a fluid in space, $\frac{\Delta V}{\Delta h}$. This is essentially the same as the $\frac{\delta u}{\delta y}$ term in fluid mechanics, which is found in the ubiquitous [fluid-shear problem](http://polymerdatabase.com/polymer%20physics/images/Visc.png "sourced from http://polymerdatabase.com/polymer%20physics/Viscosity.html").

$\bar G$ represents the average $\frac{\Delta V}{\Delta h}$ for the entire water volume under consideration, and is the parameter we will be using from now on. Unfortunately, it is unrealistic to measure $\frac{\Delta V}{\Delta h}$ for every parcel of the water in our flocculator and take an average. We need to approximate $\bar G$ using measureable parameters.

The parameter that serves as the basis for obtaining $\bar G$ is $\varepsilon$, which represents the **energy dissipation** rate of a fluid _normalized by its mass_. The units of $\varepsilon$ are Watts per kilogram:

$$\varepsilon = \left[ \frac{W}{Kg} \right]
= \left[ \frac{J}{s \cdot Kg} \right]
= \left[ \frac{N \cdot m}{s \cdot Kg} \right]
= \left[ \frac{kg \cdot m \cdot m}{s^2 \cdot s \cdot Kg} \right]
= \left[ \frac{m^2}{s^3} \right]
= \left[ \frac{[L]^2}{[T]^3} \right]$$

There are at least two ways to think about $\varepsilon$. One is through $G$. Imagine that a fluid has _no viscosity_; there is no internal friction caused by fluid flow. No matter how high $G$ becomes, no energy is dissipated. Now image a honey, which has a very high viscosity. Making honey flow fast requires a lot of energy over a short period of time, which means a high energy dissipation rate. This explanation allows us to understand the equation for $\varepsilon$ in terms of $G$ and $\nu$:

$$\varepsilon = \nu G^2$$

Which means we can solve for $G$:

$$G = \sqrt{\frac{\varepsilon}{\nu}}$$

Energy dissipation rate is, fortunately, easier to determine than collision potential. This is due to the second way to think about $\varepsilon$, which is using head loss. In any reactor, a flocculator in this case, the total energy dissipated is simply the head loss, $h_L$. The amount of time required to dissipate that energy is the residence time of the water in the reactor, $\theta$. Accounting for the fact that 'head' energy is due to gravity $g$, we have all the parameters needed to determine another equation for energy dissipation rate:

$$ \bar \varepsilon = \frac{g h_L}{\theta}$$

Note that the equation above is for $\bar \varepsilon$, not $\varepsilon$. Since the head loss term we are using, $h_L$, occurs over the entire reactor, it can only be used to find an average energy dissipation rate for the entire reactor. Combining the equations above, $G = \sqrt{\frac{\varepsilon}{\nu}}$ and $\bar \varepsilon = \frac{g h_L}{\theta}$, we can get an equation for $\bar G$ in terms of easily measureable parameters:

$$\bar G = \sqrt{\frac{g h_L}{\nu \theta}}$$

We can use this to obtain a final equation for collision potential of a reactor:

$$\bar G \theta = \sqrt{\frac{g h_L \theta}{\nu}}$$

**Note:** When we say $G \theta$ we are almost always referring to $\bar G \theta$.


### Generating Head Loss with Baffles
#### **What are Baffles?**
Now that we know how to measure collision potential with head loss, we need a way to actually generate head loss. While both major or minor losses can be the design basis, it generally makes more sense to use major losses for low-flow flocculation and minor losses for higher flows, as flocculation with minor losses tends to be more space-efficient. Since this book focuses on town and village-scale water treatment (5 L/S to 120 L/S), we will use minor losses as our design basis.

To generate minor losses, we need to create flow expansions. AguaClara does this with **baffles**, which are obstructions in the channel of a flocculator to force the flow to switch directions by 180°. Baffles in AguaClara plants are plastic sheets, and all of the baffles in one flocculator channel are connected to form a **baffle module.** Images below show an AguaClara flocculator and the beginnings of a module.

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/AC_flocculator.JPG?raw=true" width=900>

<br/>  
<br/>  
<br/>

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/Baffle_module.JPG?raw=true" width=600>

<br/>
<br/>

AguaClara flocculators, like the one pictured above, are called **vertical hydraulic flocculators**, because the baffles force the flow up and down. If the baffles were instead arranged to force the flow side-to-side, the flocculator would be a **horizontal hydraulic flocculator**. AguaClara uses vertical flocculators because they are more efficient when considering plant area. They are deeper than horizontal flocculators, which allows them to have a smaller [plan-view area](https://simple.wikipedia.org/wiki/Plan_view) and thus to be cheaper.  

#### **Finding the Minor Loss of a Baffle**  
Before beginning this section, it is important to make sure that the physical parameters of the flocculator are well defined. This is done in the following image:

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/Flocculator_physical_parameters.jpg?raw=true" width=900>

<br/>
<br/>

Since baffles are the source of head loss via minor losses, we need to find the minor loss coefficient of one baffle. To do this, we apply fluid mechanics intuition and check it against a computational fluid dynamics (CFD) simulation. Flow around a 90° bend has a vena contracta value of around $\Pi_{vc} = 0.62$ (_**NEED A CITATION ON THIS!!**_). Flow around a 180° bend therefore has a value of $\Pi_{vc, \, baffle} = \Pi_{vc}^2 = 0.384$. This number is roughly confirmed with CFD, as shown in the image below. ***Ahhhhhhhhhhhhhh I need to make sure this is legit***

<center><img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/CFD_vc_baffle.jpg?raw=true" width=60></center>

We can therefore state with reasonable accuracy that, when most contracted, the flow around a baffle goes through 38.4% of the area it does when expanded, or $A_{contracted} = \Pi_{vc, \, baffle} A_{expanded}$. Through the [third form of the minor loss equation](https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%201_Fluids%20Review/Summary_Sheet_Fluid_Review.md#minor-losses), $h_e = K_e^{'} \frac{V_{out}^2}{2g}$ and its equation for the minor loss coefficient, $K_e^{'} = \left( \frac{A_{out}}{A_{in}} -1 \right)^2$, we can determine a $K_e^{'}$ for flow around a single baffle:

$$K_{e, \, baffle}^{'} = \left( \frac{A_{expanded}}{A_{contracted}} -1 \right)^2$$

$$K_{e, \, baffle}^{'} = \left( \frac{\rlap{\Big/} A_{expanded}}{\Pi_{vc, \, baffle} \rlap{\Big/} A_{expanded}} -1 \right)^2$$

$$K_{e, \, baffle}^{'} = \left( \frac{1}{0.384} -1 \right)^2$$

$$K_{e, \, baffle}^{'} = 2.56$$

If we use this $K_{e, \, baffle}^{'}$, we must make sure that the assumptions behind it are true. This means that we must make sure that the flow fully expands before it reaches the next baffle and begins to contract again.
ahhhhhhhhhhh

### Flocculator Efficiency

_**<span style="color:red">I need some of Monroe's insights to write this section with legitimacy. This section should include, amongst other things, why $\frac{H}{S}$ is important, $\Pi_{\bar \varepsilon}^{\varepsilon_{Max}}$ and it should contain CFD images of flocculators with different $\frac{H}{S}$ ratios. I could write some stuff here, and have it be true, but it would take a lot of leaps of faith. Time is better spent elsewhere until I have a solid understanding </span>**_

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/CFD_baffle_image.jpg?raw=true" width=500>

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/CFD_full_channel.jpg?raw=true" width=700>

#### **Obstacles**
Knowing that efficient flocculators require an $\frac{H}{S}$ ratio that lies between 3 and 6, we need to understand how that impacts the flocculator design. Keeping $\frac{H}{S}$ between two specific values limits the options for baffle spacing and quantity, due to the flocculator having certain size constraints before beginning the design of the baffles. These limitations also place an upper limit on the amount of head loss that a baffled flocculator can generate, since the number of baffles is limited and baffles are what cause head loss. This is unfortunate, it means that baffled flocculators under certain size specifications can't be designed to generate certain values of $\bar \varepsilon$ and $\bar G$ _while remaining efficient_.

To get around this problem, AguaClara included 'obstacles,' or half-pipes to contract the flow, after the flow expands around one baffle and before it reaches the next baffle. The purpose of these obstacles is to provide extra head loss in between baffles. They generate head loss via minor losses, _and one obstacle is designed to have the same $K_e{'}$ as one baffle_. The inclusion of obstacles introduces a new ratio, $\frac{H_e}{S}$, where $H_e$ represents the distance traveled by the water between flow expansions, where a flow expansion can be caused by either a baffle or an obstacle. In a flocculator where there are just baffles and no obstacles, then  $\frac{H_e}{S} = \frac{H}{S}$, since the height of water in the flocculator is equal to the distance between expansions, $H_e = H$. But when obstacles are added, then $H_e = \frac{H}{1 + n_{obstacles}}$, where $n_{obstacles}$ is the amount of obstacles between two baffles.

These obstacles serve as 'pseudo-baffles'. They allow for $\frac{H}{S}$ to exceed 6, while maintaining maximum flocculator efficiency since, $\frac{H_e}{S}$ can still be between 3 and 6. The following images show these obstacles and how they affect the flow in a flocculator.

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/Floc_module_with_obstacles.jpg?raw=true" width=800>

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/Floc_flow_with_obstacles.jpg?raw=true" width=900>

## 4.2) AguaClara Design of Hydraulic, Vertical Flow Flocculators  
AguaClara's approach to flocculator design is the same as it is for any other unit process. First, critical design criteria, called inputs, are established. These criteria represent the priorities that the rest of the design will be based around. Once these parameters are established, then the other parameters of the design, which are dependent on the inputs, are calculated.
Take the CDC as an example of this design process; its design inputs are $h_{L_{Max}}$, $\sum K_e$, $\Pi_{Error}$, and the discrete dosing tube diameters $D$ that are available at hardware stores or pipe suppliers. Its dependent variables include the number and length of the dosing tubes and the flow through the CDC system.

The flocculator is more complex to design than the CDC, as it has more details and parameters, and the equations for those details and parameters are very interdependent. Therefore, there are many ways to design an AguaClara flocculator, and many different sets of critical design criteria to begin with. Enumerated below is the current AguaClara approach.

1. Input parameters
    - Specify:
      - $h_{L_{floc}}$, head loss  
      - $\bar G \theta$, collision potential   
      - $Q$, plant flow rate     
      - $H$, height of water _at the end of the flocculator_    
      - $L_{Max, \, sed}$, max length of a flocculator channel based on sedimentation tank length  
      - $W_{Min, \, human}$ minimum width based on the width of the average human hip (someone's got to go down there...)
    - Find:  
      - $\bar G$, average velocity gradient  
      - $\theta$, hydraulic retention time   
      - $\rlap{-}V_{floc}$, flocculator volume
2. Physical dimensions
    - Find:
      - $L_{channel}$, actual channel length
      - $n_{channels}$, amount of channels
      - $W_{channel}$, actual channel width
3. Hydraulic parameters
    - Find:
      - $H_{e_{Max}}$, maximum distance between baffle/obstacle expansions
      - $n_{obstacles}$, amount of obstacles per baffle spacing
      - $S$, baffle spacing
      -

### Input Parameters    
#### **Specify**
We start by making sure that our flocculator will be able to flocculate effectively by defining $h_{L_{floc}}$ and $\bar G \theta$. Fixing these two parameters initially allows us to easily find all other parameters which determine flocculator performance. Here are the current standards in AguaClara flocculators:
- $h_{L_{floc}} = 40 \, {\rm cm}$
- $\bar G \theta = 37,000$

The plant flow rate $Q$ is defined by the needs of the community that the plant is being desiged for. Additionally, the height of water _at the end_ of the flocculator, $H$, and the _maximum_ length of the flocculator based on the length of the sedimentation tank length, $L_{Max, \, sed}$, are also defined initially. Ordinarilly in AguaClara plants, the flocculator occupies the same length dimension as the sedimentation tanks, which is why this length constraint exists. See the image below for a representation of how the flocculator and sedimentation tanks are placed in a plant.

- $H = 2 \, {\rm m}$
- $L_{Max, \, sed} = 6 \, {\rm m}$

<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/Physical_design_criteria.jpg?raw=true" width=600>

#### **Find**
We can rearrange the equation for $\bar G$ from the section on collision potential, $\bar G = \sqrt{\frac{g h_L}{\nu \theta}}$, to solve for $\bar G$ in terms of $\bar G \theta$:

$$\bar G = \frac{g h_{L_{floc}}}{\nu (\bar G \theta)}$$

Now that we have $\bar G$, we can very easily find $\theta$:

$$\theta = \frac{\bar G \theta}{\bar G}$$

Finally, we take retention time $\theta$ over plant flow rate $Q$ to get the required volume of the flocculator:

$$\rlap{-} V_{floc} = \frac{\theta}{Q}$$

Now that we have the basic parameters defined, we can start to design the details of the flocculator, starting from the physical dimensions.

### Physical Dimensions
Deriving the equations required to find the physical dimensions now and the hydraulic parameters (baffle/obstacle design) in the next section requires many steps. To simplify this design explanation, [the equation derivations will all be in the derivation sheet](https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Derivation_flocculator_design_equations.md). All complex equations which seemingly came out of nowhere will be derived in the derivation sheet.

#### **Length**
Flocculator length, $L_{channel}$ must meet two constraints: it must be less than or equal to the length of the sedimentation tanks it will be next to, $L_{Max, \, sed}$. Next, the flocculator must be long enough to make sure the target volume of the flocculator is met, $L_{Max, \, \rlap{-} V}$. **The constraint that wins out is the one that results in the _smaller_ length value**.

$$L_{Max, \, sed} = 6 \, {\rm m}$$
$$L_{Max, \, \rlap{-}V} = \frac{\rlap{-} V}{n_{Min, \, channels} W_{Min, \, human} H}$$
Such that:  
$n_{Min, \, channels} = 2$

The reason why $W_{Min, \, human}$ is used is because it represents the absolute minimum of flocculator channel width. If the width ends up being larger, the length will decrease. $n_{Min, \, channels} = 2$  to make sure that the flow ends up on the correct side of the sedimentation tank, as the image below shows.

The equation for _actual_ flocculator length is therefore:

$$\color{purple}{
  L_{channel} = {\rm min}(L_{Max, \, sed}, \, L_{Max, \, \rlap{-} V})
  }$$


<img src="https://github.com/AguaClara/CEE4540_Master/blob/master/AguaClara%20Water%20Treatment%20Plant%20Design/Chapter%204_Flocculation/Images/Floc_channels.jpg?raw=true" width=600>

#### **Width and Number of Channels**
The width of a single flocculator channel must meet the following conditions:
- $\bar G$ must be maintained at the value we found in the inputs section
- $3 < \frac{H_e}{S} < 6$
- a human must be able to fit into a flocculator channel

The first two conditions are wrapped up into the following equation:

$$W_{Min, \, \Pi_{HS}} = \frac{\Pi_{HS}Q}{H_e}\left( \frac{K_e}{2 H_e \nu \bar G^2} \right)^\frac{1}{3}$$

This equation represents the absolute smallest width of a flocculator channel if we consider the lowest value of $\Pi_{HS}$ and the highest possible value of $H_e$:  
$H_e = H$, this implies that there are no obstacles between baffles  
$\Pi_{HS} = 3$

Recall the other width constraint, $W_{Min, \, human}$, based on our desire to have a human be able to fit into the channels. The governing constraint is the _larger_ value of $W_{Min}$:

$$W_{Min} = {\rm max}(W_{Min, \, \Pi_{HS}}, \, W_{Min, \, human})$$

We can find the number of channels, $n_{channels}$ and their actual width in one last step, by finding the _total flocculator width_ if there were no channels and dividing that by the minimum flocculator width, $W_{Min}$, based on the two equations above. The equation for total flocculator width is based on our target volume: $W_{total} = \frac{\rlap{-} V}{H L_{channel}}$. Finally:

$$\color{purple}{
  n_{channels} = \frac{W_{total}}{W_{Min}}
  }$$  
Such that:  
$n_{channels}$ is an even number and is not 0. Usually, $n_{channels}$ is either 2 or 4.

Now that we know $n_{channels}$, we can find the actual width of a channel, $W_{channel}$.

$$\color{purple}{
  W_{channel} = \frac{W_{total}}{n_{channels}}
  }$$

### Hydraulic Parameters
Now that the physical dimensions of the flocculator have been defined, the baffle module needs to be designed. The governing parameter for the module is the distance between expansions, $H_e$. Recall that $H_e = H$ where there are no obstacles in between baffles.

#### **Height Between Expansions $H_e$ and Number of Obstacles per Baffle Space $n_{obstacles}$**
We have a range of possible $H_e$ values based on our window of $3 < \frac{H_e}{S} < 6$. However, we are limited by the fact that there can only be an integer number of obtacles. To make sure this is not a problem, we first find $H_{e_{Max}}$, which occurs at $\frac{H_e}{S} = 6$. The equation for $H_e$ is obtained by rearranging one of the equations for minimum channel width found above, $W_{Min, \, \Pi_{HS}} = \frac{\Pi_{HS}Q}{H_e}\left( \frac{K_e}{2 H_e \nu \bar G^2} \right)^\frac{1}{3}$, and instead using $W_{channel}$ and the maximum value of $\Pi_{HS}$, which is $\Pi_{{HS}_{Max}} = 6$. The result is:

$$H_{e_{Max}} = \left[ \frac{K_e}{2 \nu \bar G^2} \left( \frac{Q \Pi_{{HS}_{Max}}}{W} \right)^3 \right]^\frac{1}{4}$$

Oftentimes, _**<span style="color:red"> Finish once Monroe tells me why we use $H_{e_{Max}}$ and round down instead of using $H_{e_{Min}}$ and rounding up... or figure it out myself! </span> Is it because getting $\frac{H_e}{S}$ closer to 5 or 6 is closer to full expansion and we don't know the physics yet  for $\frac{H_e}{S} = 3$?**_**

Now we round down to make sure that we have an integer number of flow expansions per baffle spacing:

$$n_{expansions} = {\rm ceil}\left( \frac{H}{H_{e_{Max}}} \right)$$

From here, we can easily get to the number of obstacles per baffle spacing:

$$\color{purple}{
  H_e = \frac{H}{n_{expansions}}
  }$$

Finally, we can get to the number of obstacles per baffle space. The $- 1$ in the equation is because the baffles themselves provide one flow expansion per baffle space.

$$\color{purple}{
  n_{obstacles} = \frac{H}{H_e} - 1
  }$$

#### **Baffle Spacing $S$**
Finally, we can find the space between baffles, $S$. The equation for $S$ is taken from an intermediate step in deriving the equation for $W_{Min, \, \Pi_{HS}}$, $W = \frac{Q}{S}\left( \frac{K_e}{2 H_e \nu \bar G^2} \right)^\frac{1}{3}$ Rearranging for $S$, we get:

$$\color{purple}{
S = \left( \frac{K_e}{2 H_e G^2 \nu } \right)^\frac{1}{3} \frac{Q}{W}
}$$