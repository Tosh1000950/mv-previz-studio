# 2.5D MV Previz & Animatics Studio — User Manual

> Note: The app's UI is currently in Japanese. This manual translates all button
> and tab names so English speakers can follow along.

This tool is a browser-only application for previsualizing (previz) 3D camera work
and motion in sync with a song's waveform, using storyboard images and cut-out
character images (transparent PNGs) placed in a 3D space.

---

## 1. Recommended environment
- **Browser**: Google Chrome / Microsoft Edge (latest recommended)
  - A PC Chromium-based browser is recommended for stable video export (`.webm`) and Audio API behavior.
- **Supported files**:
  - **Audio**: `.mp3`, `.wav`, `.ogg`, `.m4a`
  - **Images**: `.png` (transparent PNG recommended), `.jpg`, `.webp`
  - **Project data**: `.json`

---

## 2. Basic workflow

### Step 1: Load the song
1. Use the **「楽曲を変更」 (Change song)** button in the top header to load your music file (MP3/WAV, etc.).
2. A waveform is generated automatically in the timeline at the bottom.
   - A built-in demo track (120 BPM) is loaded at first, so you can test playback right away.

### Step 2: Add cuts and adjust timing (timeline)
1. Click/drag on the waveform in the bottom timeline to move the playhead.
2. Use the **`Space`** key or **「▶ 再生 / 一時停止」 (Play / Pause)** to play the song and picture in sync, and find the timings where cuts should change.
3. **Adding / editing cuts**:
   - Use **「＋ カット追加」 (Add cut)** to create a new cut.
   - Adjust each cut's start/end seconds in the cut list or on the timeline to match the song's beats and structure.

### Step 3: Place artwork and character images (2.5D layers)
Open the **「🧍 レイヤー/キャラ」 (Layers / Character)** tab in the right inspector panel and assign images to each layer.
- **Layer order (back to front)**:
  1. **Background (BG)**: sky, distant scenery, interior walls (placed far on the Z axis)
  2. **Midground (MG)**: buildings, trees, furniture
  3. **Character (Char)**: a cut-out transparent PNG of the character
  4. **Foreground (FG)**: fences, effects, bokeh elements in front (placed near on the Z axis)
- **Character movement / animation settings**:
  - For each cut, set the **start position (X, Y, Z), scale and rotation** and the **end position (X, Y, Z), scale and rotation**.
  - Enable **「歩行バウンス (Walk Bob)」** to automatically add a walking up-down bounce to the movement.

### Step 4: Set the 3D camera work
Open the **「🎥 カメラワーク」 (Camera work)** tab in the right inspector panel.

- **Method A: Decide by mouse (recommended)**
  1. Switch the mode above the preview to **「🎥 自由カメラ編集モード」 (Free camera edit mode)**.
  2. Move the view with the mouse:
     - **Left-drag**: orbit around the subject
     - **Right-drag (or Shift + left-drag)**: pan / tilt (parallel move)
     - **Mouse wheel**: zoom in / out
  3. When the starting framing is decided, click **「📍 現在の視点を開始カメラに記録」 (Record current view as start camera)**.
  4. Set the ending framing the same way and click **「📍 現在の視点を終了カメラに記録」 (Record current view as end camera)**.
  5. Switch back to **「🎬 プレビュー再生モード」 (Preview playback mode)** to check.

- **Method B: Precise numeric adjustment with easing**
  - Camera position (X, Y, Z), target (Target X, Y, Z), field of view (FOV) and roll can be fine-tuned numerically.
  - **Easing** controls the acceleration curve, e.g. "start slowly and stop dead on" or "pan at constant speed".

---

## 3. Exporting for AI video generators

Use the previz output as control input for video generation AI (Runway, Kling, Luma, Sora, etc.).

1. **Start PNG / End PNG export**
   - Saves the selected cut's 0% (start frame) and 100% (end frame) as clean images (`1280×720` PNG) without guide lines.
   - **Use**: feed them as **First Frame / Last Frame** references to force the intended camera move and composition change.

2. **Cut video export (`.webm`)**
   - Exports one selected cut's camera work and character movement as a video file.
   - **Use**: as a base video for **Video-to-Video** or **Motion Control (camera/motion reference)**.

3. **Full recording (`.webm`)**
   - Exports the whole song as one animatic video. Useful for rough editing in an editor or for sharing with a team.

---

## 4. Saving and loading data
- **Save project (JSON)**: downloads your cut layout, camera values and layer placement as a `.json` file.
- **Load project (JSON)**: load a saved `.json` file to resume work.
  - Note: for security reasons, the image and audio files themselves are not stored inside the JSON. After loading, re-select the same image/audio files.

---

## 5. Keyboard shortcuts
- **`Space`**: toggle play / pause
- **`←` / `→` keys**: nudge the play position (frame step back / forward)
- **Mouse wheel (over the preview)**: zoom in free camera edit mode

---

## 6. Troubleshooting
- **Q. Dragging the screen does not move the camera**
  - A. The mode above the preview may be **「🎬 プレビュー再生モード」 (Preview playback mode)**. Switch to **「🎥 自由カメラ編集モード」 (Free camera edit mode)** first.
- **Q. Video export (`.webm`) stalls or is not saved**
  - A. Do not minimize the tab or switch to another tab during export. Background tabs stop rendering due to browser power saving.
- **Q. My character image shows a white background**
  - A. The image is not transparent (JPG or PNG with background). Use a **transparent PNG** made with an image editor or a background-removal tool.
