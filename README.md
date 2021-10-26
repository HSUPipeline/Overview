# Overview

This organization contains code and resources for working with Single-Unit data in the Jacobs lab.

Relevant tooling:
- The [NWB](https://www.nwb.org/) file format is used to store data
- The [spikeinterface](https://github.com/SpikeInterface/spikeinterface) tool will be used for managing spike sorting
- The [spiketools](https://github.com/spiketools/spiketools) module is used for common analyses

## Information & Tutorials

This organization contains the following resources & tutorials:
- An [overview and examples](https://github.com/JacobsSU/NWBExamples) of NWB data files
- A [tutorial](https://github.com/JacobsSU/SpikeTutorial) for working with spike data

Other 
- A list of [spike resources](https://github.com/openlists/SpikeResources)

## Converting Data

Data is initially collected from multiple sites with different amplifiers, file types, etc. We therefore want to standardize the data format by converting all data into the NWB format.

### convnwb

The [convnwb](https://github.com/JacobsSU/convnwb) mini-module contains a 

### ConvertTEMPLATE

The [ConvertTEMPLATE](https://github.com/JacobsSU/ConvertTEMPLATE) contains a template repository for doing conversion for a task.

## Spike Sorting

The [spike sorting](https://github.com/JacobsSU/SpikeSorting) repository contains information and a template for running spike sorting.
