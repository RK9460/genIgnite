# GELGINITE - Emergency Object Detection System (Hackathon 2025)

This project is designed to automatically detect critical emergency response objects such as Fire Extinguishers, First Aid Boxes, Emergency Phones, etc., from image data using YOLOv8 object detection.

## 🗂️ Project Directory Structure

```
GELGINITE/
├── Hackathon2_scripts/
│   ├── ENV_SETUP/
│   │   ├── create_env.bat
│   │   ├── install_packages.bat
│   │   └── setup_env.bat
│   ├── predictions/
│   │   ├── images/
│   │   └── labels/
│   ├── runs/
│   │   └── detect/
│   │       ├── train/
│   │       ├── val/
│   │       └── val2/
│   ├── classes.txt
│   ├── generate_report.py
│   ├── predict.py
│   ├── train.py
│   ├── visualize.py
│   └── yolo_params.yaml
└── hackathon2_test3/
    └── datasets/
        ├── test/
        ├── train/
        ├── val/
        ├── images/
        └── labels/
```

## ⚙️ Environment Setup

1. **Create the virtual environment**:

   ```bash
   ./ENV_SETUP/create_env.bat
   ```

2. **Install dependencies**:

   ```bash
   ./ENV_SETUP/install_packages.bat
   ```

3. **Activate environment** (if not auto-activated):

   ```bash
   ./ENV_SETUP/setup_env.bat
   ```

---

## 🚀 Training the YOLOv8 Model

1. Ensure `yolo_params.yaml` is configured properly:

```yaml
train: hackathon2_test3/datasets/train
val: hackathon2_test3/datasets/val
test: hackathon2_test3/datasets/test
nc: 7
names: ['OxygenTank', 'NitrogenTank', 'FirstAidBox', 'FireAlarm', 'SafetySwitchPanel', 'EmergencyPhone', 'FireExtinguisher']
```

2. Run training:

```bash
python train.py
```

* Trained weights will be saved under: `runs/detect/train*/weights/best.pt`

---

## 🔍 Running Predictions

Ensure `yolo_params.yaml` has the correct test path set. Then run:

```bash
python predict.py
```

This will:

* Load the latest `best.pt` model
* Predict on all test images
* Save output visuals to `predictions/images`
* Save YOLO-format bounding boxes to `predictions/labels`

---

## 📊 Generating Evaluation Report

To generate a results summary:

```bash
python generate_report.py
```

This will create a `results.csv` or similar output.

---

## ⚠️ Notes

* Ensure enough disk space is available. YAML formatting errors or write failures typically arise from storage issues.
* If transferring to a different machine:

  * Install compatible GPU drivers (NVIDIA RTX 3060+ recommended)
  * Reinstall packages using the `.bat` scripts
  * Verify CUDA availability via PyTorch

---

## ✅ Key Dependencies

* Python 3.10+
* Ultralytics YOLOv8
* OpenCV
* PyYAML

---

## 👨‍💻 Developed for: HWI GenIgnite Hackathon 2025

By: [Your Name Here]

For queries or bugs, contact: [your_email@example.com](mailto:your_email@example.com)
