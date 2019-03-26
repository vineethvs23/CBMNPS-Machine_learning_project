# Condition Based Maintainance of Naval Propulsion Systems

- As I will be required to find a coefficient value, this will be a regression problem.

# What is Condition based maintainance?
This will be a long read,skip to the last paragraph of this section if you're feeling lazy.   :) 

In the shipbuilding industry, one of the main objectives of shipwrights companies is to improve the technological quality of their products. For example, they design more efficient hull shapes and propeller geometries,study innovative propulsion systems, and reduce the overall production costs. Recently, many of these companies are evaluating different DA solutions for improving the quality of their products, for monitoring the equipment, and for maintenance purposes as integrative activities to their core business. In fact, ships are already equipped with a network of sensors that collect data for security, diagnostic and monitoring purposes, which DA can directly exploit
by taking advantage of these technologies. Data Analysis, for example, offers the possibility to extract, from the raw sensor data, useful information about the efficiency of the ship, to reduce the fuel consumption, and to improve maintenance activities. 

Among the different problems, maintenance is probably the most critical one since it could require drydocking, and the cost of retrieving a stricken vessel offshore is non-trivial. Correct maintenance ensures that a ship works as it was designed, with the desired level performances, without impacting the service.

Maintenance policies can be divided into two main categories:
- Corrective (CM)
- Preventive (PM).

In the past, the most common approach to this problem relied on the Corrective measure where maintenance is performed only after a breakdown of a component. However, replacing a malfunctioning component after it has failed during service, results in exceptional costs and inevitable lower incomes. In Preventive Measure, instead, a component is replaced when it reaches the end of its life cycle, which can be computed adopting many estimations. One of the historical way to perform this operation is to determine a conservative average of the component life cycle adopting the experience gained with all the components belonging to a specific class. Similarly to Corrective measure, this particular type of Preventive Measure can bring unnecessary costs too, if the replaced component could have been used more than originally forecast. Moreover,this technique does not guarantee to limit the number of faults in a fleet, since a breakdown could still happen before the replacement takes place. In this case, there is a trade-off between the number of breakdowns and the lifetime
estimation of the components, which is not easy to reach since the actual ship usage can be very different from ship to ship. 

Nevertheless, Condition Based Maintenance (CBM) can be considered as a specification of Preventive Measure, which aims at reducing both the costs of Corrective measure and non-predictive Preventive Measure by relying on the exact decay state of each component and then by efficiently planning its maintenance. Since, in most cases,the decay state of each component cannot be tracked with a sensor, CBM requires a model able to predict it based on other sensors available. Considering the estimated state of decay, it is possible to schedule each component’s replacement before failures occur, maximizing its life cycle, according to the time required for each maintenance and to the geographical location of the ship. As a result, the additional costs of Corrective measure and Preventive Measure can be replaced with the lower ones of equipping the propulsion system with sensors and by collecting, storing, and analyzing these data for the purpose of creating effective predictive DDMs .


# How the data has been extracted:

A naval vessel, characterized by a combined diesel-electric and gas propulsion plant,has been exploited to collect such data and show the effectiveness of the proposed approaches. Because of confidentiality constraints with the Navy,the authors used a real-data validated simulator and the dataset has been published for free use through the UCI repository.

The experiments have been carried out by means of a numerical simulator of a naval vessel (Frigate) characterized by a Gas Turbine (GT) propulsion plant. The different blocks forming the complete simulator (Propeller, Hull, GT, Gear Box and Controller) have been developed and fine tuned over the year on several similar real propulsion plants. In view of these observations the available data are in agreement with a possible real vessel. 
In this release of the simulator it is also possible to take into account the performance decay over time of the GT components such as GT compressor and turbines. 

The propulsion system behaviour has been described with this parameters: 

- Ship speed (linear function of the lever position lp). 
- Compressor degradation coefficient kMc. 
- Turbine degradation coefficient kMt. 


# Features of each recorded observation:

- A 16-feature vector containing the GT measures at steady state of the physical asset:

  -  Lever position (lp) [ ]
  -  Ship speed (v) [knots]
  -  Gas Turbine (GT) shaft torque (GTT) [kN m]
  -  GT rate of revolutions (GTn) [rpm]
  -  Gas Generator rate of revolutions (GGn) [rpm]
  -  Starboard Propeller Torque (Ts) [kN]
  -  Port Propeller Torque (Tp) [kN]
  -  Hight Pressure (HP) Turbine exit temperature (T48) [C]
  -  GT Compressor inlet air temperature (T1) [C]
  -  GT Compressor outlet air temperature (T2) [C]
  -  HP Turbine exit pressure (P48) [bar]
  -  GT Compressor inlet air pressure (P1) [bar]
  -  GT Compressor outlet air pressure (P2) [bar]
  -  GT exhaust gas pressure (Pexh) [bar]
  -  Turbine Injecton Control (TIC) [%]
  -  Fuel flow (mf) [kg/s]

# There are two targets:

- GT Compressor decay state coefficient (Target-1)
- GT Turbine decay state coefficient (Target-2)

## Note on data:
- Features are not normalized
- Each feature vector is a row on the text file

# Installation:

This project requires python 3.6 or anyother higher versions of python, along with these libraries :

- NumPy
- Pandas
- matplotlib
- scikit-learn
- seaborn

You also need a web-application to run this python notebook called "Jupyter Notebook". It is highly recommended that you install the Anaconda distribution of Python, which already has the above packages and more included.

# About the Repository

- There are 10 jupyter notebooks in the repository and 1 data file.

- You will be required to use the included dataset file data.txt containing all the data.

- The notebook titled understanding-data.ipynb is a cumulation of graphs which give us a better insight as to what the data looks like and helped me select different features. 

- The notebooks titled Benchmark target-1.ipynb and Benchmark target-2.ipynb give us an idea of what MSE to expect. We use sklearn (Multivariate Linear regression) to set a benchmark.

- The notebooks titled 5-layer-neural-network-target-1.ipynb , 5-layer-neural-network-target-2.ipynb and 5-layer-neural-network.ipynb were initial attempts based off of the paper (mentioned below), the 5 layers did not yeild a MSE anywhere close to the benchmarks but it gave me an insight of using lesser layers and nodes in my neural network.

- The notebooks titled 3-layer-Relu-neural-network-target-1.ipynb, 3-layer-Relu-neural-network-target-2.ipynb ,3-layer-Sigmoid-neural-network-target-1.ipynb and 3-layer-Sigmoid-neural-network-target-2.ipynb are attempts in creating new networks based on insights from previous 5-layer networks. These yeilded a better MSE and I used ReLu and Sigmoid as activation funtions to check if the MSE varied.  

# Running the Code

In a terminal or command window, navigate to the top-level project directory and run the command below:

	jupyter notebook 5-layer-neural-network-target-1.ipynb

You can change the name of the notebook to whichever notebook you want to open.

This will open the Jupyter Notebook software and project file in your browser.