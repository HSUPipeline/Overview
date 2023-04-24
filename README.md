# HSU Pipeline

HSUPipeline is a pipeline for processing and analyzing single-unit neural data from human subjects.

## Table of Contents

- [Overview](#overview)
- [Sorting Data](#sorting-data)
- [Converting Data](#converting-data)
- [Analyzing Data](#analyzing-data)
- [Using the Pipeline](#using-the-pipeline)

## Overview

HSUPipeline including templates, code, and resources for
working with single-unit data collected from human subjects.

Human single unit data is typically collected with across multiple sites,
which may include different amplifiers, file types, etc.
It then requires specific procedures for spike-sorting and analyses, that
are oriented to the specifics of human data.

To address these needs, this pipeline implements and uses standardized tools and data
formats, organized into a standard workflow that can be used for human spike data.

This pipeline is organized into multiple components, including:
- SORT: basic pre-processing of the neural data, including spike sorting
- CONVERT: converting the data to a standard data format, including neural and behavioural data
- ANALYZE: analzying the data, including analyzing single-unit activity and relating it to behaviour

Other resources that may be useful include:
- This [tutorial](https://github.com/HSUPipeline/SpikeTutorial) introduces working with spike data
- This list of [spike resources](https://github.com/openlists/SpikeResources)

## Sorting Data

Neuro-physioloigcal recordings from human subjects that allow for single-unit analyses
need to be spike sorted before putative single-neuron activity can be analyzed.

Notably, the specifics of the eletrodes in human patients which are typically recorded
with microwires such as in Behnke-Fried electrodes, has some specific requirements that
differ from what is typically done in other contexts, such as in work in animal models.

To address this, this pipeline implements a recommended approach for spike sorting
human single-unit data.

### Spike Interface

For running spike-sorting, we recommend the
[spikeinterface](https://github.com/SpikeInterface/spikeinterface)
tool for managing and running spike sorting.

SpikeInterface is a tool for creating flexible and robust
spike-sorting pipelines, including supporting access to a large
number of existing spike sorters.

### SortTEMPLATE

The [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE)
contains a template repository for spike sorting data.

## Converting Data

To facilitate common tool usage and having shareable data,
this pipeline uses a standard data standard and includes
tools for converting data to this standard.

### Neurodata Without Borders

The data standard used in this pipeline is the
[NWB](https://www.nwb.org/) file format.
NWB is a general-purpose data standard for neurophysiological data.

See the
[NWBexamples](https://github.com/HSUPipeline/NWBExamples)
repository for some examples NWB files.

### ConvertTEMPLATE

The [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
contains a template repository for conversting data for a particular task
into the NWB standard.

Note that convert repositories should only do data conversion, with minimal pre-processing,
but do not include data analyses.

### convnwb

The [convnwb](https://github.com/HSUPipeline/convnwb)
mini-module contains general, task-agnostic, utilities that can be used to convert data to NWB format.

This module should be installed for doing data conversion, and is used by the ConvertTEMPLATE.
Any general conversion utilities, that can be used across tasks and datasets, should be added to and used from this module.

## Analyzing Data

The final step for a human single-unit project is to analyze the data.
This details of this process are necessarily more custom for each projects,
however where possible analyses should follow are shared basica toolkit and organization.

### Spiketools

The [spiketools](https://github.com/spiketools/spiketools)
module is an open-source collected of analysis tools for working with single-unit activity,
specifically designed for analyzing human data.

Spiketools implements genearal analysis code, which can be used for analyzing data across tasks and contexts.

### AnalyzeTEMPLATE

The [AnalyzeTEMPLATE](https://github.com/HSUPipeline/AnalyzeTEMPLATE)
repository implements a template layout for an organized analysis repository.

## Using the Pipeline

To integrate a new task / project into the general workflow:
- Create a new sorting repository, following the [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE)
    - Follow instructions in the template to process the data through a spike sorter, and extract outputs
- Create a new conversion repository, following the [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
    - Follow instructions in the template for adding custom code & information, and running data conversion
- Create a new analysis repository, following the [AnalyzeTEMPLATE](https://github.com/HSUPipeline/AnalyzeTEMPLATE)
    - This repository should load NWB files, and add any custom code needed to analyze the data

## Contributing

'HSUPipeline' welcomes contributions and suggestions from the community!

If you would suggest an edit to a part of the project, please open an issue on Github, on the relevant repository,
and/or directly open a pull request with the suggested update.

Note that to interact with the HSUPipeline organization you must follow the
[Code of Conduct](https://github.com/HSUPipeline/Overview/blob/main/CODE_OF_CONDUCT.md).
