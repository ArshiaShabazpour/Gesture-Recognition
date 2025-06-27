🤚 **Hand Gesture Recognition & Classification**

A real-time hand-tracking and letter-classification app built with MediaPipe & OpenCV.

---

## 📸 Demo

![Demo GIF](assests/demo.gif)

---

## 🔧 Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/yourusername/hand-gesture-recognition.git
   cd hand-gesture-recognition
   ```

2. **Install dependencies**

   ```bash
   pip install mediapipe opencv-python scikit-learn pandas numpy
   ```

3. **Prepare data folder & model**

   * Create a `data/` directory
   * Place (or generate) `Landmark_data.csv` inside `data/`
   * **Download the ****`hand_landmarker.task`**** model file** and place it in the project root (same directory as `main.py`).

---

## 🚀 Usage

Run the main script to launch the webcam interface:

```bash
python main.py
```

### 🎬 Mode 1: Data Capture

1. Press `1` to switch to Capture Mode
2. Press a letter key (`a–z`) to select which letter to record
3. Perform the sign, then:

   * `SPACE`: record a frame of landmark data
   * `S`: save all recorded frames to `data/Landmark_data.csv`
   * `Z`: undo the last capture
   * `ESC`: go back to mode selection

Captured CSV columns: `letter` (0–25), `handedness` (0=Left,1=Right), `x1,y1,z1 … x21,y21,z21`

### 🔍 Mode 2: Letter Detection

1. Press `2` to enter Detection Mode
2. Show an ASL letter in front of your camera
3. The model predicts the letter if confidence ≥ 0.8; otherwise displays “?”

---

## 📂 Project Structure

```
├── main.py
├── assets/
│   └── demo.gif
├── hand_landmarker.task   <-- Required model file (place here)
├── README.md
```

---

## 📊 Dataset & Training

* **Dataset**: `data/Landmark_data.csv`

  * Col 1: `letter` (0–25)
  * Col 2: `handedness` (0 or 1)
  * Col 3–65: normalized `x,y,z` for 21 landmarks
* **Model**: `SVC(probability=True)` from scikit-learn
* **Train/Test Split**: 75% / 25% (`random_state=42`)
* **Accuracy**: printed to console after training
