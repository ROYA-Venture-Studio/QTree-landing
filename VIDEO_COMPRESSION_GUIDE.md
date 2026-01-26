# Video Compression Guide

## Best Practices for Background Videos

### Recommended Settings:
- **Resolution**: 1920x1080 (Full HD) is sufficient for most displays
- **Frame Rate**: 24-30 fps (no need for higher on background videos)
- **Bitrate**: 2-4 Mbps for good quality/size balance
- **Duration**: Keep it short (10-30 seconds) and loop it

### Compression Methods:

#### Option 1: HandBrake (Free, Easy)
1. Download HandBrake (https://handbrake.fr/)
2. Open your video
3. Settings:
   - Preset: "Web" → "Gmail Large 3 Minutes 720p30"
   - Adjust dimensions to 1920x1080 if needed
   - Video tab: H.264, Quality RF 20-23, Framerate 24-30fps
   - Audio: AAC, 128kbps (or remove audio entirely for background videos)
4. Export as MP4

#### Option 2: FFmpeg (Command Line, More Control)
```bash
# Create optimized MP4 (H.264)
ffmpeg -i input.mp4 -c:v libx264 -preset slow -crf 23 -vf scale=1920:1080 -r 24 -an public/video/background.mp4

# Create WebM version for better compression
ffmpeg -i input.mp4 -c:v libvpx-vp9 -crf 30 -b:v 0 -vf scale=1920:1080 -r 24 -an public/video/background.webm
```

#### Option 3: Online Tools
- **CloudConvert** (https://cloudconvert.com)
- **Clipchamp** (https://clipchamp.com)

### Tips for Minimal Quality Loss:
1. **Remove audio** - Background videos don't need it (saves 30-50% file size)
2. **Trim unnecessary frames** - Keep only the looping portion
3. **Use two formats** - MP4 (H.264) for compatibility, WebM (VP9) for better compression
4. **Target file size** - Aim for under 5MB for fast loading

### After Compression:
Place your compressed video(s) in: `public/video/`
- `background.mp4` (primary, best compatibility)
- `background.webm` (optional, better compression)

The code will automatically use the video once it's in place!
