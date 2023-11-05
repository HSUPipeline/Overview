# Guide

This section provides a guide to using the HSUPipeline.

## Table of Contents

- [Overview](#overview)
- [Spike Sorting](#spike-sorting)
- [Data Conversion](#data-conversion)
- [Analysis](#analysis)

## Overview

This guide overviews the entire pipeline, including pre-processing (spike sorting), converting
data to a standardized format, and organizing analyses.

To integrate a new task / project into the general workflow:
- Create a new sorting repository, following the [SortTEMPLATE](https://github.com/HSUPipeline/SortTEMPLATE)
    - Follow instructions in the template to process the data through a spike sorter, and extract outputs
- Create a new conversion repository, following the [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
    - Follow instructions in the template for adding custom code & information, and running data conversion
- Create a new analysis repository, following the [AnalyzeTEMPLATE](https://github.com/HSUPipeline/AnalyzeTEMPLATE)
    - This repository should load NWB files, and add any custom code needed to analyze the data

Note that these steps are set up to be largely independent, so different parts of the above pipeline
can generally be used in isolation. For more information on these templates, see the
[templates](https://hsupipeline.github.io/templates) page.

All of the templates in this pipeline follow the general outline of the
[StructuredScience](https://github.com/structuredscience/) layout.

## Spike Sorting

The first step of the pipeline is pre-processing of the neural data,
most notably, spike sorting. In this first section of the guide, we
outline information related to pre-processing and spike sorting neural recordings.

### Spike Sorters

For resources and a list of available spike sorters, see the
[Spike Resources](https://github.com/openlists/SpikeResources#spike-sorting)
open list.

The current template uses [Combinato](https://github.com/jniediek/combinato/)
for spike sorting.

Combinato is a Python tool for spike sorting:
- For tutorials and documentation, see the
[Wiki](https://github.com/jniediek/combinato/wiki/)
- Combinato is described in
[this paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0166598)

In future iterations, the template is likely to be updated to use
[SpikeInterface](https://github.com/SpikeInterface/spikeinterface)

SpikeInterface is a Python based workflow tool for spike sorting:
- For more information, see the
[documentation](https://spikeinterface.readthedocs.io/en/latest/)
- SpikeInterface is described in
[this paper](https://elifesciences.org/articles/61834)

Additional Resources:
- [Past, present and future of spike sorting techniques](https://www.sciencedirect.com/science/article/pii/S0361923015000684)
- [Quality Metrics to Accompany Spike Sorting of Extracellular Signals](https://www.jneurosci.org/content/31/24/8699.short)

### Template Guide

Words, words, words.

## Data Conversion

The second step in the template is data conversion, including collecting and converting
human single-unit data along with a structured representation of any and all behavioural
data and task information such that all the information can be organized together into
standard data files.

This template doesn't assume any particular file type or structure or structure within files,
and should be applicable to a broad range of recording files.

### Data Organization & Tools

For neural data, this template does not include IO functions for raw data files,
and custom IO procedures may need to be updated / added. For this see
[neo](https://github.com/NeuralEnsemble/python-neo).

For behavioral data, this template is generally geared towards parsing task
related data from a logfile that is saved out into a txt file, which can be
parsed line-by-line. For other formats of behavioral data, customization may be needed.

Note that this template does not itself implement any utilities - the underlying
general functionality is all implemented in the
[convnwb](https://github.com/HSUPipeline/convnwb)
module. This module is then aliased into the `conv` folder, on top
of which any needed customizations and additions can be made.

### Template Guide

Files to be processed will need to be organized into a consistent layout,
which should follow the directory structure used by `convnwb`.

To do so, the template includes:

- code for parsing task logfiles & organizing data
- a system for organizing and defining metadata to be used and added during data conversion
- basic utilities for preprocessing and aligning data
- script templates to apply conversion procedures to collected data files

Note that this template / procedure does not include any processing of the data, such as spike sorting.
Any such processing and analysis steps should be done separate to this data conversion.

In order to apply this template to a new task, the following updates are needed:

- metadata, including required fields and event information, need to be defined
    - this should be done be updating files in the `metadata` folder
- the parser and task code need to customized for the task
    - this should  be done by updating `parser.py` and `task.py` in `conv`
- processing procedures to be applied during the conversion process need to be defined
    - update `process.py` with any pre-processing, potentially adding code to `measures.py`
- the conversion has to be specified, detailing data should be organized in the NWB file
    - this can be interactively explored in `notebooks/01-ConvertToNWB.ipynb`
    - this then needs implementing in `scripts/convert_data.py`
- the scripts and settings need updating for any custom settings / procedures
    - this may include defining and using `settings`, and/or custom processing steps
- data files need to organized into a systematic file organization
    - this should be done following the directory layout used by `convnwb`

After the above, this template should be able to be used for converting data files!

Note that the `notebooks` implement templates that can be run interactively,
however ultimately the goal is to implement procedures in the `scripts` folder.

After the above is set up, data files can be converted as follows:

```
# Prepare data for conversion
python scripts/prepare_data.py

# Convert files to NWB
python scripts/convert_data.py
```

For customization over and above what is detailed above, additional changes may be required
to the stored metadata and/or processing code.
See the `Repository Layout` Section for information.

## Analysis

The third component of the HSUPipeline is a template structure for analyzing the data.

### SpikeTools

``spiketools`` is a Python based module for analyzing spiking data:
- For more information, see the
[documentation](https://spiketools.github.io/spiketools/)
- The spiketools code is available in this
[repository](https://github.com/spiketools/spiketools)
- ``spiketools`` is described in
[this paper](XX)

### Template Guide

Words, words, words.
