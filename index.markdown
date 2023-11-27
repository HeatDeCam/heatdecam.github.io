---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

title: HeatDeCam Detecting Hidden Spy Cameras via Thermal Emissions
layout: default
---

# HeatDeCam: Detecting Hidden Spy Cameras via Thermal Emissions

Unlawful video surveillance of unsuspecting individuals using spy cameras has become an increasing concern. To mitigate these
threats, there are both commercial products and research prototypes designed to detect hidden spy cameras in household and office environments. However, existing work often relies heavily on user expertise and only applies to wireless cameras. To bridge this gap, we propose HeatDeCam, a thermal-imagery-based spy camera detector, capable of detecting hidden spy cameras with or without built-in wireless connectivity. To reduce the reliance on user expertise, HeatDeCam leverages a compact neural network deployed on a smartphone to recognize unique heat dissipation patterns of spy cameras. To evaluate the proposed system, we have collected and open-sourced a dataset of a total of 22,506 thermal and visual images. These images consist of 11 spy cameras collected from 6 rooms across different environmental conditions. Using this dataset, we found HeatDeCam can achieve over 95% accuracy in detecting hidden cameras. We have also conducted a usability evaluation involving a total of 416 participants using both an online survey and an in-person usability test to validate HeatDeCam.

## Team
HeatDeCam was developed by the following team of academic researchers:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[Zhiyuan Yu](https://zh1yu4nyu.github.io/)** at Washington University in St. Louis  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[Zhuohang Li](http://web.eecs.utk.edu/~zli96/)** at University of Tennessee, Knoxville  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[Yuanhaur Chang](https://changoliver.github.io/)** at Washington University in St. Louis  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[Skylar Fong](https://www.linkedin.com/in/skylarfong/)** at Washington University in St. Louis  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[Jian Liu](https://web.eecs.utk.edu/~jliu/)** at University of Tennessee, Knoxville  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**[Ning Zhang](https://engineering.wustl.edu/faculty/Ning-Zhang.html)** at Washington University in St. Louis  

<p style='text-align: center'> Contact us at <a href="mailto:yu.zhiyuan@wustl.edu">yu.zhiyuan@wustl.edu</a></p>

<center><img src="logos/WUSTL.png" alt="WashU_logo" width="200"/><img src="logos/UTK.jpg" alt="UTK_logo" width="170"/></center>

## Features

**Motivation of This Work**

This work is motivated by the gap between existing detection methods and our observations on the heat dissipation patterns of spy cameras.

There have been both commercial products and research prototypes that leverage radiofrequency (RF) signals and optical reflections to detect spy cameras. While achieving impressive detection performance, they could be limited in detecting non-wirelessly connected cameras and usability. To fill the gap, we leverage thermal imagery as the detection vector. An example of heat dissipation patterns is shown in the figures below. 

<center><img src="figs/Angle1.png" alt="Angle1" width="200"/><img src="figs/Angle2.png" alt="Angle2" width="200"/></center>

We observe that the spy camera disguised as a charger plug (at the top in black) exhibits additional uneven heat distribution, as compared to the regular charger plug (at the bottom in white). This is because spy cameras have to add unique hardware components (e.g., SD cards, image sensors) without changing the original form factor. It will unavoidably affect the internal layout that was originally optimized for heat dissipation. 

**Key Approach**

However, it is almost impossible for we to require users to manually distinguish heat patterns with their raw eyes. We develop a data-driven approach with designed neural network model to recognize and locate the spy cameras.

We collect the first thermal image dataset of spy cameras. It consists of over 22,056 images collected from six rooms across three scenarios, Airbnb, hotel, and office. A total of eleven heterogeneous spy cameras with varying properties in appearances, functionalities, brands, and costs.

<center><img src="figs/Spycams.jpg" alt="Spycams" width="230"/>&nbsp;&nbsp;<img src="figs/Rooms.png" alt="Rooms" width="260"/></center>

The overall workflow of our detection algorithm is depicted in the figure.

<center><img src="figs/Workflow.png" alt="Workflow" width="830"/></center>

The key design elements include:

- Thermal-visual registration to align spatial features
- Adaptive soft mask to mitigate environmental influences while preserving context
- Neural-network-based feature extraction and recognition 
- CAM-based visualization of hidden locations of spy cameras

The structural design of the neural network incorporates ResNet-based feature extration and attention module that enables effective learning of heat pattern features.

<center><img src="figs/NeuralNetwork.png" alt="NeuralNetwork" width="600"/></center>

**Experiments in the Real World**

We developed an Android app as a prototype of our approach. Besides the evaluation of our collected dataset, we also invited people to use our prototype to find hidden spy cameras deployed in a simulated room. Our method is shown to be superior to commercial products in both detection rate and false positive. To test the robustness in high-temperature environments, we also conduct experiments in a room with a temperature over 104°F.

<center><img src="figs/Detectors.jpg" alt="Detectors" width="230"/>&nbsp;&nbsp;<img src="figs/InPersonRoom.jpg" alt="Room" width="230"/>&nbsp;&nbsp;<img src="figs/AdvEnv.png" alt="AdvEnv" width="172"/></center>

For more details of our work, please see our [paper](https://dl.acm.org/doi/10.1145/3548606.3560669) and [code](https://github.com/WUSTL-CSPL/HeatDeCam). Also please contact us if you have any questions!
