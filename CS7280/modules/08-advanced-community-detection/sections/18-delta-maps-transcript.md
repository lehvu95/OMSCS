# Delta Maps

| Text |
|------|
| We will now look at an application of community detection in the analysis of  |
| spatiotemporal data, and in climate science in particular. The method that we'll be using  |
| to detect communities is called Delta maps. And it was developed by the instructor and  |
| the PhD student, Ilias Fountalis. Delta maps is appropriate for any application in which  |
| we are given spatiotemporal data. That's so an activity time series of its point of a  |
| grid space. The goal of delta maps is to detect contiguous blocks of space referred to as  |
| functional domains or simply domains. That behave in a very homogeneous manner over time.  |
| So its applications are common in climate science where the activity time series may be  |
| temperature, humidity, pressure at different points on the planet, or the atmosphere.  |
| Delta maps can also be used to analyze spatiotemporal data that represents neural  |
| activity. Here the activity time series may be EEG signals from different electrodes or  |
| FMRI measurements at different voxels. After delta maps detects the homogeneous  |
| communities or domains, it forms a weighted network between domains based on the strength  |
| of the statistical correlation between the aggregate signal of each domain pair. |
