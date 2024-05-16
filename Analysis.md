# Analysis

The third component of the HSUPipeline is a template structure for analyzing the data.

## Overview

Once the data is pre-processed and organized into a standard format, the next
task is to analyze it! While the analysis of any given project will be
specific to the task and research questions, this section of the pipeline
provides a structure layout for organizing these analyses.

## Resources

As with other sections of this pipeline, the template itself does implement
any key tooling, but rather provides an organized structure to a human single-unit
analysis, while using external analysis tools. The key resources and tools are
briefly described in this section.

### SpikeTools

``spiketools`` is a Python based module for analyzing spiking data:
- For more information, see the
[documentation](https://spiketools.github.io/spiketools/)
- The spiketools code is available in this
[repository](https://github.com/spiketools/spiketools)
- ``spiketools`` is described in
[this paper](https://doi.org/10.21105/joss.05268)

## AnalyzeTEMPLATE

The [AnalyzeTEMPLATE](https://github.com/HSUPipeline/AnalyzeTEMPLATE)
provides a template structure for organizing the analysis of a project
examining human single unit data.

The suggested structure of the template includes:
- a sub-module for custom analysis code
- a set of notebooks for developing, exploring, and demonstrating analyses
- an organized set of script templates for running analyses across the dataset

Typically, analyses can be organized at different levels, for example:
- group level analyses, that summarize / analyze data across the whole group
- session level analyses, that run analyses across each session of data (e.g. behavioural results)
- unit level analyses, that run a set of analyses on each unit (neuron)

In doing these analysis, the recommended approach is to organize analyses, each with
their own visualizations, and then create `reports` that collect together all the
visualizations for each analysis.

## Run Procedures

The suggested process for developing and applying analyses is as follows:
- analyses can be developed in notebooks dedicated to each analysis
- as analyses mature, any custom code can be organized and moved into the local code folder
- once analyses are ready to run across the data, they can be added / converted into scripts
- at this point, the entire set of analyses can be run be re-running the scripts
- additional notebooks can be created to collect across analyses, and create final figures

For example, the following would re-run all analyses:
```
# Run analyses across the group / sessions / all units
python scripts/group_analysis.py
python scripts/session_analysis.py
python scripts/unit_analysis.py
```
