# Overview

This organization contains code and resources for working with Single-Unit data in the Jacobs lab.

## Tooling, Resources, & Tutorials

This organization contains the following resources & tutorials:
- An [overview and examples](https://github.com/JacobsSU/NWBExamples) of NWB data files
- A [tutorial](https://github.com/JacobsSU/SpikeTutorial) for working with spike data

Other relevant resources:
- This is an external list of [spike resources](https://github.com/openlists/SpikeResources)

Relevant tooling:
- The [NWB](https://www.nwb.org/) file format is used to store data
- The [spikeinterface](https://github.com/SpikeInterface/spikeinterface) tool will be used for managing spike sorting
- The [spiketools](https://github.com/spiketools/spiketools) module is used for common analyses

## Converting Data

Data is initially collected from multiple sites with different amplifiers, file types, etc. 
We therefore want to standardize the data format by converting all data into the NWB format. 
To do so, we have developed a standard workflow, demonstrated in the template below. 

### ConvertTEMPLATE

The [ConvertTEMPLATE](https://github.com/JacobsSU/ConvertTEMPLATE) contains a template repository for conversting data for a particular task.

Each new task should have it's own conversion repository. 
Note that convert repositories should only do data conversion, with minimal pre-processing, but no analysis.

### convnwb

The [convnwb](https://github.com/JacobsSU/convnwb) mini-module contains general, task-agnostic, utilities that can be used to convert data to NWB format. 

This module should be installed for doing data conversion. 
Any general conversion utilities, that can be used across tasks and datasets, should be added to and used from this module. 

## Processing Data

Notes on processing and analyzing data.

### Spike Sorting

The [spike sorting](https://github.com/JacobsSU/SpikeSorting) repository contains information and a template for running spike sorting.

### Analyzing Data

Each analysis project should have it's own analysis repository, ideally following this (or a similar)
[ProjectTemplate](https://github.com/structuredscience/ProjectTemplate).

General analysis code is implemented in the [spiketools](https://github.com/spiketools/spiketools) module. 
Any general analysis utilities, that can be used across tasks and datasets, should be added to and used from this module. 

## Adding a new task

To integrate a new task / project into the general workflow:
- Create a new conversion repository, following the [ConvertTEMPLATE](https://github.com/JacobsSU/ConvertTEMPLATE)
    - Follow instructions in the template for adding all the custom code & information for data conversion
    - Once this repository is ready, data files can be exported to NWB format
- Create a new analysis repository, following the [ProjectTemplate](https://github.com/structuredscience/ProjectTemplate)
    - This repository should load NWB files, and add any custom code needed to analyze the data
    - Analyses and figures for the project should be implented in this repository

## Codemap

A map of code on the [JacobsSU](https://github.com/JacobsSU) organization.

### Conversion Repositories

The following are repositories for converting specific tasks:

- [ConvertTH](https://github.com/JacobsSU/ConvertTH), for the Treasure Hunt task
- [ConvertT3](https://github.com/JacobsSU/ConvertT3), for the T3 task
- [ConvertTrain](https://github.com/JacobsSU/ConvertTrain), for the Train task

### Analysis Repositories

- [AnalyzeTH](https://github.com/JacobsSU/AnalyzeTH), for the Treasure Hunt task
- [AnalyzeT3](https://github.com/TomDonoghue/T3Analyses), for the T3 task
