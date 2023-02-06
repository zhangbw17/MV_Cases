# Failure cases of MV-Adapter

We summarize two failure modes from the case study. (1) Since we use a fixed number of frames per video in training, it may fail to capture fine movements in long videos as the differences between frames aggregate. (2) Results may be incorrect when the caption is related to the audio contents. The cases for each mode are put into ./long_video and ./audio respectively. Each directory contains one retrieval result, including caption.txt (the query we use to search), gt_\*.mp4 and pred_\*.mp4 (the groundtruth and predicted video, where * represents the index number of the video in MSR-VTT.)

To be more specific, we will go over each example:
- **long_video_0.** The groundtruth video is long and the shot that corresponds to the target in the query ("walking down a short runway) is relatively short. Since the number of input frames is fixed, non-target information in videos tends to dominate the input, making the model fail to parse out the fine movement ("walking" and "short runway") from the groundtruth. Eventually, the model returns a similar video that contains "walking" but on a "long runway" (should be a short runway).

- **long_video_1.** This case is similar to long_video_0. In the groundtruth video, the queried object "cushion seat" only gets recognizable in a very short time in the 6th second (unrecognizable due to bad angles and/or occlusions at other times). As key information may be deficient in sampled frames, the model can hardly perceive the queried object from that video.

- **audio_0.** Audio information is necessary in order to determine whether a woman or a man is speaking.

- **audio_1.** Though the retrieved result is visually similar to groundtruth, the contents of the talk do not match that of the query text. With the help of audio content (like transcripts from ASR), the results can be corrected.