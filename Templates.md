# Templates

This section provides an overview and guide to using the HSNPipeline, including introducing the templates.

## Table of Contents

- [Overview](#overview)
- [SortTEMPLATE](#sort-template)
- [ConvertTEMPLATE](#convert-template)
- [AnalyzeTEMPLATE](#analyze-template)

## Overview

This guide overviews the entire pipeline, including pre-processing (spike sorting), converting
data to a standardized format, and organizing analyses. Each of these steps has it's own template.

To integrate a new task / project into the general workflow:
- Create a new sorting repository, following the [SortTEMPLATE](https://github.com/HSNPipeline/SortTEMPLATE)
    - Follow instructions in the template to process the data through a spike sorter, and extract outputs
- Create a new conversion repository, following the [ConvertTEMPLATE](https://github.com/HSNPipeline/ConvertTEMPLATE)
    - Follow instructions in the template for adding custom code & information, and running data conversion
- Create a new analysis repository, following the [AnalyzeTEMPLATE](https://github.com/HSNPipeline/AnalyzeTEMPLATE)
    - This repository should load NWB files, and add any custom code needed to analyze the data

Note that these steps are set up to be largely independent, so different parts of the above pipeline
can generally be used in isolation. For more information on these templates, see the
[templates](https://hsupipeline.github.io/templates) page.

All of the templates in this pipeline follow the general outline of the
[StructuredScience](https://github.com/structuredscience/) layout.

## Sort Template

Neuro-physiological recordings from human subjects that allow for single-neuron analyses
need to be spike sorted before putative single-neuron activity can be analyzed.

In human patients, single-neuron recordings are typically recorded with microwires,
such as with Behnke-Fried electrodes. Notably, the specifics of these electrodes
has some idiosyncracies that are different from other types of recordings, such as
recordings in animal models that often use dense grids of electrodes.

To address this, this pipeline implements a recommended approach for spike sorting
human single-neuron data, designed to work with microwire recordings.

The [SortTEMPLATE](https://github.com/HSNPipeline/SortTEMPLATE)
contains a template repository for spike sorting data.

## Convert Template

This pipeline uses a standard data standard and includes tools for converting data to this standard.
The goal of using a data standard is to organize data into consistent, shareable formats, as well as to
facilitate using consistent analysis protocols.

The [ConvertTEMPLATE](https://github.com/HSNPipeline/ConvertTEMPLATE)
contains a template repository for converting data for a particular task
into the NWB standard.

Note that convert repositories should only do data conversion, with minimal pre-processing,
but do not include data analyses.

## Analyze Template

The final step for a human single-neuron project is to analyze the data.
The details of this process are necessarily quite custom for any individual project,
however where possible analyses should follow a shared basic toolkit and organization.

The [AnalyzeTEMPLATE](https://github.com/HSNPipeline/AnalyzeTEMPLATE)
repository implements a template layout for an organized analysis repository.
