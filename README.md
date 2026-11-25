# VisionLog

An automated facial recognition attendance system built with Python and Jupyter Notebooks. VisionLog processes known face datasets, generates facial encodings, recognizes faces in real time, and logs attendance records to date-stamped CSV files.

## Project Structure

```text
VisionLog/
├── known_faces/                  # Subfolders named by person containing reference face images
│   ├── Person_Name_1/
│   │   └── *.jpg
│   └── Person_Name_2/
│       └── *.jpg
├── download_dataset.ipynb        # Notebook to download and organize reference face images
├── encode_faces.ipynb            # Notebook to extract face embeddings and generate encodings.pkl
├── attendance_system.ipynb       # Main notebook to run face recognition and log attendance
├── encodings.pkl                 # Serialized facial embeddings generated from known_faces/
├── attendance_YYYY-MM-DD.csv     # Auto-generated daily attendance log
└── README.md                     # Project documentation
```

## Prerequisites

- **Python 3.8+** installed on your system
- **CMake & C++ Build Tools** (required if installing `dlib` / `face_recognition` from source)
- **Webcam** (for live camera attendance capture)
- **Jupyter Notebook** or **VS Code** with the Jupyter extension
- **Git** (optional, required only if cloning via terminal)

## Getting Started

### 1. Download or Clone the Repository

**Option A: Clone via Git**
```bash
git clone [https://github.com/grananyarao/VisionLog.git](https://github.com/grananyarao/VisionLog.git)
cd VisionLog
```

**Option B: Download ZIP**
1. Click the green **Code** button at the top right of this repository page.
2. Select **Download ZIP**.
3. Extract the downloaded archive (`VisionLog-main.zip`) to a folder on your computer.
4. Open a terminal or command prompt inside the extracted folder.

### 2. Set Up a Virtual Environment (Recommended)

Creating a virtual environment isolates project dependencies from your global Python installation.

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

Install Jupyter and the core computer vision and data processing libraries used across the notebooks:

```bash
pip install jupyter opencv-python face_recognition numpy pandas scikit-learn
```

*(Note: If you have a `requirements.txt` file, you can run `pip install -r requirements.txt` instead.)*

### 4. Launch Jupyter Notebook

Start Jupyter from inside the project directory:

```bash
jupyter notebook
```

### 5. Run the Workflow

Execute the notebooks in the following order:

1. **`download_dataset.ipynb` (Optional):** Run this notebook if you need to download and populate sample face folders inside `known_faces/`. The repository already includes pre-populated folders in `known_faces/` and pre-computed `encodings.pkl`, so you can skip straight to Step 3 unless you add new people.
2. **`encode_faces.ipynb`:** Run this notebook whenever you add or update person folders in `known_faces/` to regenerate `encodings.pkl`.
3. **`attendance_system.ipynb`:** Run this notebook to launch the facial recognition attendance system. Recognized individuals are automatically recorded with timestamps in `attendance_YYYY-MM-DD.csv`.

## Adding New People

1. Create a new folder inside `known_faces/` named after the individual (e.g., `known_faces/Jane_Doe/`).
2. Add clear, front-facing `.jpg` images of that person into their folder.
3. Re-run `encode_faces.ipynb` to update `encodings.pkl`.
4. Run `attendance_system.ipynb` to start recognizing the newly added person.
