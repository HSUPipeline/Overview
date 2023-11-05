# Templates

Overview of the templates available as part of the HSUPipeline.

For a broader overview of the Human Single Unit Pipeline, see the
[overview](https://hsupipeline.github.io/).

For a detailed guide to using these templates to organize a project, see the pipeline
[guide](https://hsupipeline.github.io/guide).

## Table of Contents

- [SortTEMPLATE](#sort-template)
- [ConvertTEMPLATE](#convert-template)
- [AnalyzeTEMPLATE](#analyze-template)

## Sort Template

Neuro-physiological recordings from human subjects that allow for single-unit analyses
need to be spike sorted before putative single-neuron activity can be analyzed.

In human patients, single-unit recordings are typically recorded with microwires,
such as with Behnke-Fried electrodes. Notably, the specifics of these electrodes
has some idiosyncracies that are different from other types of recordings, such as
recordings in animal models that often use dense grids of electrodes.

To address this, this pipeline implements a recommended approach for spike sorting
human single-unit data, designed to work with microwire recordings.

The [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE)
contains a template repository for spike sorting data.

## Convert Template

This pipeline uses a standard data standard and includes tools for converting data to this standard.
The goal of using a data standard is to organize data into consistent, shareable formats, as well as to
facilitate using consistent analysis protocols.

The [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
contains a template repository for converting data for a particular task
into the NWB standard.

Note that convert repositories should only do data conversion, with minimal pre-processing,
but do not include data analyses.

## Analyze Template

The final step for a human single-unit project is to analyze the data.
The details of this process are necessarily quite custom for any individual project,
however where possible analyses should follow a shared basic toolkit and organization.

The [AnalyzeTEMPLATE](https://github.com/HSUPipeline/AnalyzeTEMPLATE)
repository implements a template layout for an organized analysis repository.
