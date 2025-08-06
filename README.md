# MP4 to ASCII Converter

A Python script that converts MP4 videos into real-time ASCII art animations displayed directly in your terminal with full color support.

## Features

- **Real-time ASCII conversion**: Converts video frames to ASCII characters in real-time
- **Full color support**: Preserves original video colors using ANSI escape codes
- **Interactive playback controls**:
  - `Space`: Pause/Resume playback
  - `Left Arrow`: Slow down playback (2x slower)
  - `Right Arrow`: Speed up playback (2x faster)
  - `Q`: Quit the player
- **Automatic terminal sizing**: Adapts video resolution to fit your terminal window
- **Cross-platform compatibility**: Works on macOS, Linux, and Windows
- **Threaded processing**: Uses separate threads for frame processing and display for smooth playback

## Requirements

- Python 3.6+
- OpenCV (`cv2`)
- A terminal that supports ANSI color codes

## Installation

1. Clone or download this repository
2. Install the required dependency:
   ```bash
   pip install opencv-python
   ```

## Usage

```bash
python ascii.py <video_file.mp4>
```

### Example
```bash
python ascii.py my_video.mp4
```

## Controls

| Key | Action |
|-----|--------|
| `Space` | Pause/Resume playback |
| `←` (Left Arrow) | Slow down playback speed |
| `→` (Right Arrow) | Speed up playback speed |
| `Q` | Quit the player |

## How It Works

1. **Frame Processing**: The script reads video frames using OpenCV
2. **Resizing**: Each frame is resized to match your terminal dimensions
3. **ASCII Mapping**: Grayscale values are mapped to ASCII characters from a predefined table:
   ```
   "     .'`^\",:;Il!i><~+_-?][}{1)(|\\/tfjrxnuvczXYUJCLQ0OZmwqpdbkhao*#MW&8%B@$"
   ```
4. **Color Preservation**: Original RGB colors are applied to each ASCII character using ANSI escape codes
5. **Display**: The colored ASCII art is displayed in your terminal with playback controls

## Technical Details

- **ASCII Character Mapping**: Uses 77 different characters ranging from space (darkest) to `$` (brightest)
- **Color Format**: Uses 24-bit RGB ANSI escape codes (`\033[38;2;r;g;b;m`)
- **Terminal Features**: 
  - Alternate screen buffer for clean display
  - Hidden cursor during playback
  - Non-blocking input handling for real-time controls
- **Performance**: Multi-threaded architecture with frame queue for smooth playback

## Limitations

- Terminal size determines maximum video resolution
- Performance depends on terminal rendering capabilities
- Some terminals may have limited color support
- Very large videos may require significant processing power

## Troubleshooting

**Video won't open**: Ensure the video file path is correct and the format is supported by OpenCV

**No colors displayed**: Your terminal may not support ANSI color codes. Try using a modern terminal emulator

**Playback too slow/fast**: Use the arrow keys to adjust playback speed, or check your terminal's performance settings

## License

This project is open source. Feel free to modify and distribute as needed.

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.
