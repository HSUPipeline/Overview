# Sorting

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

### Sort: Template Guide

Notes on using the Combinato spike sorter:

#### Automatic Processing Notes

- Event detecting requires a detection polarity (positive or negative)
    - Only one polarity can be run at a time
    - BlackRock & Ripple: typically always negative polarity
    - Neuralynx: uses positive polarity
- By default, Combinato defaults to 2 rounds of template matching, but this can be changed to do more

#### Manual Curation

GUI Actions:
- To select a cluster press 'enter'
  - This highlights the selected cluster across the visualizations
- To mark a cluster as bad click 'A' for artifact
  - This moves a cluster to the 'Artifacts' group
- To move a cluster, in "AllGroups" click (select) a cluster, and then click the new location to move it to
- To merge a cluster to an existing other cluster:
    - from "All Groups", click on cluster to move and then click an existing cluster to move it to
- To separate out a cluster to a new (empty) cluster:
    - click on Actions / New Group to create a new (empty) cluster
    - From "All Groups", click on the cluster to split out, then to the new (empty) group to move it there

GUI Notes:
- The GUI has 3 categories of clusters: artifacts, unassigned, assigned clusters
- The cluster colors:
    - dark blue: events from the first template matching
    - light blue: events from the second template matching
    - orange: spikes matched to the cluster
- The GUI has buttons for labelling a cluster as 'SU' (single-unit), 'MU' (multi-unit), or 'Artifact'
    - DO NOT use these labels to mark artifacts, as this does not move or remove the cluster, just gives it a label

Curation Notes:
- It is generally normal that some channels but no detected spikes, but if whole shanks or subjects have nothing, you should check the original data, and see if something can be done to improve spike yields (by doing something to the data, and/or tweaking combinato settings)
- While it is worth quickly checking automatically designated "artifact" & "unassigned" clusters, combinato is usually good at automatically designating this, and this rarely has to be changed.
- In general, the usual situation is Combinato will detect more clusters / groups than appear to be real units, meaning it is very common to reject clusters / groups and/or merge clusters. As such, the typical outcome of manual curation is to end up many fewer groups than automatically detected - but
- Real units (that can be analyzed) are ideally present across the whole recording. If a unit is only detected during a specific / short time periodic it is likely an artifact. If it does appear to be a real unit (e.g. has a nice waveform), check for other clusters that might reflect the same unit at different time ranges.
- For ISIs, ideally real units should have less than \~3% of spikes within 3 ms
