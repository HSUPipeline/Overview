# Templates

Overview of the templates available on HSUPipeline.

This section covers the templates specifically.
For a broader overview of the Human Single Unit Pipeline, see the
[overview](https://hsupipeline.github.io/).

## Table of Contents

- [SortingTEMPLATE](#sorting-template)
- [ConvertTEMPLATE](#convert-template)
- [AnalyzeTEMPLATE](#analyzing-data)
- [Using the Pipeline](#using-the-pipeline)

## Sorting Template

Neuro-physioloigcal recordings from human subjects that allow for single-unit analyses
need to be spike sorted before putative single-neuron activity can be analyzed.

Notably, the specifics of the eletrodes in human patients which are typically recorded
with microwires such as in Behnke-Fried electrodes, has some specific requirements that
differ from what is typically done in other contexts, such as in work in animal models.

To address this, this pipeline implements a recommended approach for spike sorting
human single-unit data.

The [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE)
contains a template repository for spike sorting data.

## Convert Template

To facilitate common tool usage and having shareable data,
this pipeline uses a standard data standard and includes
tools for converting data to this standard.

The [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
contains a template repository for conversting data for a particular task
into the NWB standard.

Note that convert repositories should only do data conversion, with minimal pre-processing,
but do not include data analyses.

## Analyze Template

The final step for a human single-unit project is to analyze the data.
This details of this process are necessarily more custom for each projects,
however where possible analyses should follow are shared basica toolkit and organization.

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
