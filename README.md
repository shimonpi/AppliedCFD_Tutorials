# Applied CFD Tutorials
Welcome to the Applied Computational Fluid Dynamics (CFD) Tutorials repository. This repository contains a series of hands-on tutorials designed to help undergraduate students learn and apply CFD principles using **OpenFOAM**, a leading open-source CFD software, and **ParaView**, a powerful visualization tool.

## Repository Contents
0. [Tutorial 0: Setting up WSL and OpenFOAM](Tutorial_0/README.md)
   
   Learn how to install the Windows Subsystem for Linux (`wsl`) and **OpenFOAM** on your Windows machine. This tutorial includes step-by-step instructions to ensure a smooth installation process, especially for beginners.

1. Tutorial 1: Basic Case Setup - Lid-Driven Cavity (LDC) 
   - [Tutorial 1.1 – Introduction to CFD concepts and OpenFOAM](Tutorial_1/README.md)
   - [Tutorial 1.2 - Setting up the LDC problem](Tutorial_1/Tutorial_1_2/README.md)
   - [Tutorial 1.3 - Running the LDC simulation](Tutorial_1/Tutorial_1_3/README.md)
   
   Dive into setting up your first CFD simulation case. This tutorial covers the initial steps of preparing the lid-driven cavity benchmark case and running it in **OpenFOAM**, and visualizing the results using **ParaView**.

2. Tutorial 2: Laminar Flow Over a Flat Plate
   - [Tutorial 2.1 – Introduction to boundary layer and Blasius solution](Tutorial_2/README.md)
   - [Tutorial 2.2 – OpenFOAM setup](Tutorial_2/Tutorial_2_2/README.md)
   - [Tutorial 2.3 – Running the simulation and post-processing](Tutorial_2/Tutorial_2_3/README.md)

   Explore the process of setting up and simulating laminar flow over a flat plate. This tutorial includes the theoretical background of boundary layer development, configuring the simulation in **OpenFOAM**, and analyzing the results using **ParaView**.

3. Tutorial 3: Turbulent Flow Over a Flat Plate
   - [Tutorial 3.1 – Introduction to turbulence and the Law of the Wall](Tutorial_3/README.md)
   - [Tutorial 3.2 – OpenFOAM setup](Tutorial_3/Tutorial_3_2/README.md)
   - [Tutorial 3.3 – Running the simulation and post-processing](Tutorial_3/Tutorial_3_3/README.md)

   Delve into the complexities of simulating turbulent flow over a flat plate. This tutorial covers the fundamental concepts of turbulence and the law of the wall, guides you through setting up a turbulent flow simulation in **OpenFOAM**, and instructs you on how to analyze the results using **ParaView**.

4. [Tutorial 4: Flow Over a Backward-Facing Step](Tutorial_4/README.md)

   This tutorial explores the flow over a backward-facing step (BFS), highlighting flow separation and reattachment phenomena. You will set up, run, and analyze a BFS simulation using **OpenFOAM**, and compare the results with experimental data.

5. [Tutorial 5: Flow Over a Cylinder (Vortex Shedding)](Tutorial_5/README.md)

   This tutorial introduces the simulation of flow over a circular cylinder, focusing on vortex shedding phenomena. You will learn how to set up and run this case in **OpenFOAM** and visualize the formation of the Von Kármán vortex street.

6. Tutorial 6: Flow Over NACA0012 Airfoil
   - [Tutorial 6.1 – NASA-Provided Mesh Analysis for NACA0012 Airfoil Flow](Tutorial_6/README.md)
   - [Tutorial 6.2 - Custom Mesh Generation for NACA0012 Airfoil Using SnappyHexMesh](Tutorial_6_2/README.md)

   Explore the aerodynamic characteristics of the NACA0012 airfoil using two approaches. The first sub-tutorial utilizes NASA's provided geometry and mesh to set up and simulate flow over the airfoil. The second sub-tutorial introduces `snappyHexMesh`, a tool within **OpenFOAM** for generating custom meshes. You will compare both approaches, validating your findings against NASA's experimental data.

## Getting Started
To get started, begin with [Tutorial 0: Setting up WSL and OpenFOAM](Tutorial_0/README.md). Follow the instructions carefully to prepare your system for running **OpenFOAM** simulations. Once set up, proceed to the subsequent tutorials to deepen your understanding and skills in CFD.

## Contributing
We welcome contributions to enhance these tutorials. If you find any issues or have suggestions for improvement, please open an issue or submit a pull request.