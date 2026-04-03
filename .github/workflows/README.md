# 📺 Daily YouTube Live Stream via GitHub Actions

Streams a pre-recorded video to YouTube daily using FFmpeg.

## Setup

### 1. Add your YouTube Stream Key
- Go to your repo → Settings → Secrets and variables → Actions
- Click **New repository secret**
- Name: `YOUTUBE_STREAM_KEY`
- Value: your stream key from YouTube Studio

### 2. Upload your video to Google Drive
- Right click → Share → Anyone with the link → Viewer
- Copy the file ID from the link:
  `https://drive.google.com/file/d/FILE_ID_IS_HERE/view`

### 3. Update the workflow
- Open `.github/workflows/stream.yml`
- Replace `YOUR_FILE_ID` with your actual Google Drive file ID
- Change the cron time to your preferred UTC time

### 4. Set your stream time (UTC)
Cron format: `minute hour * * *`

| Your Time | Cron |
|-----------|------|
| 12:00 AM UTC | `0 0 * * *` |
| 6:00 AM UTC | `0 6 * * *` |
| 12:00 PM UTC | `0 12 * * *` |
| 2:00 PM UTC | `0 14 * * *` |
| 6:00 PM UTC | `0 18 * * *` |
| 8:00 PM UTC | `0 20 * * *` |

Use https://crontab.guru to find your local time in UTC.

### 5. Enable Actions
- Go to your repo → Actions tab
- Click **Enable Actions** if prompted

### 6. Test manually
- Go to Actions tab → Daily YouTube Stream → Run workflow

## How it works
1. GitHub Actions runs daily at your scheduled time
2. Downloads your video from Google Drive using gdown
3. Streams it to YouTube for exactly 2 hours on loop
4. Job stops automatically after 2 hours

## Notes
- Keep your repo **private** to protect your stream key via secrets
- Make sure YouTube Live is enabled on your channel
- Stream key can be found in YouTube Studio → Go Live → Stream
- Uses ~60 minutes of your 2,000 free GitHub Actions minutes per day
