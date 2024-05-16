# Conversion

The second step in the template is data conversion, including collecting and converting
human single-unit data along with a structured representation of any and all behavioural
data and task information such that all the information can be organized together into
standard data files.

This template doesn't assume any particular file type or structure or structure within files,
and should be applicable to a broad range of recording files.

## Overview

Once you have the neural and behavioral data collected, and pre-processing (e.g. spike
sorting) applied, the next step in the pipeline is to organize the data into a standardized
data format - specifically the [Neurodata Without Borders format](https://www.nwb.org/).

Note that this template does not implement any data standards, etc, but
rather provides a structured approach to use existing tools to organize data
human single unit experiments (see the Resources section for what is used).

## Data Streams

For neural data, this template does not include IO functions for raw data files,
and custom IO procedures may need to be updated / added.

For behavioral data, this template is generally geared towards parsing task
related data from a logfile that is saved out into a txt file, which can be
parsed line-by-line. For other formats of behavioral data, customization may be needed.

## Resources

This pipeline uses a series of existing external tools, standards, and
resources to provide a template structure for converting data to a standardized data
format. The key resources and tools are briefly described in this section.

### NWB & pynwb

[Neurodata Without Borders](https://www.nwb.org/) is a data standard for neuroscientific data,
based on using [HDF5](https://www.hdfgroup.org/solutions/hdf5/) files.

In order to interact read and write NWB files, we use the
[pynwb](https://pynwb.readthedocs.io/en/stable/) Python library.

### convnwb

The underlying general functionality is all implemented in the
[convnwb](https://github.com/HSUPipeline/convnwb) module.
This module is then aliased into the `conv` folder, on top
of which any needed customizations and additions can be made.

## ConvertTEMPLATE

The [ConvertTEMPLATE](https://github.com/HSUPipeline/ConvertTEMPLATE)
provides a template structure for converting various data sources into NWB.

Files to be processed will need to be organized into a consistent layout,
which should follow the directory structure used by `convnwb`.

To do so, the template includes:

- code for parsing task logfiles & organizing data
- a system for organizing and defining metadata to be used and added during data conversion
- basic utilities for preprocessing and aligning data
- script templates to apply conversion procedures to collected data files

Note that this template / procedure does not include pre-processing, such as spike sorting.
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

## Run Procedures

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
