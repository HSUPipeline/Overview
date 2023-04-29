# HSU Pipeline

HSUPipeline is a pipeline for processing and analyzing single-unit neural data from human subjects.

## Table of Contents

- [Overview](#overview)
- [Templates](#templates)
- [Resources](#resources)
- [Tools](#tools)
- [Contributing](#contributing)

## Overview

HSUPipeline including templates, code, and resources for
working with single-unit data collected from human subjects.

Human single unit data is typically collected with across multiple sites,
which may include different amplifiers, file types, etc.
It then requires specific procedures for spike-sorting and analyses, that
are oriented to the specifics of human data.

To address these needs, this pipeline implements and uses standardized tools and data
formats, organized into a standard workflow that can be used for human spike data.

## Templates

This pipeline is organized into multiple components, including:
- SORT: basic pre-processing of the neural data, including spike sorting
    - This is available in the [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE)
- CONVERT: converting the data to a standard data format, including neural and behavioural data
    - This is available in the [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
- ANALYZE: analyzing the data, including analyzing single-unit activity and relating it to behaviour
    - This is available in the [AnalyzeTEMPLATE](https://github.com/HSUPipeline/AnalyzeTEMPLATE)

## Resources

Other resources that may be useful include:
- This [tutorial](https://github.com/HSUPipeline/SpikeTutorial) introduces working with spike data

### Spike Resources

As part of the
[OpenLists](https://openlists.github.io/) project,
there is a maintained list of
[spike resources](https://github.com/openlists/SpikeResources).

This list details tools and resources related to working with single-unit data.

### Spike Interface

For running spike-sorting, we recommend the
[spikeinterface](https://github.com/SpikeInterface/spikeinterface)
tool for managing and running spike sorting.

SpikeInterface is a tool for creating flexible and robust
spike-sorting pipelines, including supporting access to a large
number of existing spike sorters.

### Neurodata Without Borders

The data standard used in this pipeline is the
[NWB](https://www.nwb.org/) file format.
NWB is a general-purpose data standard for neurophysiological data.

See the
[NWBexamples](https://github.com/HSUPipeline/NWBExamples)
repository for some examples NWB files.

## Tools

This pipeline also has associated software tools that are available to be used with the pipeline.

Note that these tools are organized as independent Python modules and thus can be used
with or without using the broader pipeline.

### convnwb

The [convnwb](https://github.com/HSUPipeline/convnwb)
mini-module contains general, task-agnostic, utilities that can be used to convert data to NWB format.

This module should be installed for doing data conversion, and is used by the ConvertTEMPLATE.
Any general conversion utilities, that can be used across tasks and datasets, should be added to and used from this module.

### Spiketools

The [spiketools](https://github.com/spiketools/spiketools)
module is an open-source collection of analysis tools for working with single-unit activity,
specifically designed for analyzing human data.

Spiketools implements general analysis code, which can be used for analyzing data across tasks and contexts.

## Contributing

'HSUPipeline' welcomes contributions and suggestions from the community!

If you would suggest an edit to a part of the project, please open an issue on Github, on the relevant repository,
and/or directly open a pull request with the suggested update.

Note that to interact with the HSUPipeline organization you must follow the
[Code of Conduct](https://github.com/HSUPipeline/Overview/blob/main/CODE_OF_CONDUCT.md).
