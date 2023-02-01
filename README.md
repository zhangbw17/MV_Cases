# MV_Cases
Failure cases of MV-Adapter

We summarize two failure modes from case study. (1) Since we use a fixed number of frames per video in training, it may fail to capture fine movements in long videos as the differences between frames aggregate. Employing sliding window of videos may be helpful. (2) Results may be incorrect when the caption is related to the audio aspect.
The cases for these are put into ./long_video and ./audio respectively.