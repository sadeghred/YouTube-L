# Download & Delivery Flow

## Pipeline

1. Receive a YouTube request.
2. Validate the authenticated YouTube session when required.
3. Read video metadata and discover actually available qualities.
4. Validate the selected quality.
5. Download the video stream.
6. Download a compatible audio stream when required.
7. Merge/remux the streams into MP4 with FFmpeg.
8. Inspect the final MP4 with ffprobe.
9. Extract duration, width, and height.
10. Upload to the Telegram archive as native video.
11. Deliver the archived media to the user.

## Why Explicit Metadata Matters

An MP4 container alone does not guarantee correct Telegram presentation. Supplying duration and dimensions explicitly fixes generic/small file-card presentation and incorrect `00:00` duration while enabling normal native-video behavior.
