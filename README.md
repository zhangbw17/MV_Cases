# MV_Cases
Failure cases of MV-Adapter

We summarize two failure modes from the case study. (1) Since we use a fixed number of frames per video in training, it may fail to capture fine movements in long videos as the differences between frames aggregate. (2) Results may be incorrect when the caption is related to the audio aspect. The cases for each mode are put into ./long_video_* and ./audio_* respectively. Each directory contains one retrieval result, including caption.txt (the query we use to search), gt_*.mp4 and pred_*.mp4 (the groundtruth and predicted video, where * represents the index number of the video in MSR-VTT.)

To be more specific, we will go over each example:
- long_video_0
The groundtruth video is long and the shot of "walking down a short runway"' is relatively short. The gap between sampled frames is larger when dealing with long videos as the number of frames is fixed. As a result, the model may fail to capture fine movements and select the video that models are walking (**all the time and obviously**) on the **long** runway.

- long_video_1
This is a similar case to long_video_0. Even though the video is not as long as gt_8914.mp4 (30 seconds), the shot that clearly indicates "cushion seat" (we think only the sixth second) is too short, so it is confusing for the model.

- audio_0:
Audio information is necessary in order to determine whether a woman or a man is speaking.

- audio_1:
Though the retrieved result is visually similar to the ground-truth, the contents of the talk do not match that of query text. With the help of audio contents (like transcripts from ASR), the results can be corrected.