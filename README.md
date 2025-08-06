# RehabTrack_Workflow

**RehabTrack_Workflow** is a modular, open-source pipeline for processing, analysing, and visualising upper-limb physiotherapy movements using **video and IMU data**.  
Each stage in the workflow is contained in a separate repository, allowing for flexibility, transparency, and adaptation to different datasets or clinical protocols.

---

## 📦 Modules Overview

### 🔹 IMU Data Processing
Preprocesses raw IMU logger data by **merging, cleaning, and synchronising** multiple loggers.  
🔁 Outputs **time-aligned CSV files** for each session and patient.  
📍 Must be run before `DataSynchronization`.

→ [Go to repo](https://github.com/lrlcardoso/IMU_Data_Processing)

---

### 🔹 Video Data Processing
Preprocesses video recordings to:
- Extract **pose and re-ID features** from all individuals
- Isolate and track the **target person**
- Annotate and save cleaned pose data  

📍 Must be run before `DataSynchronization`.

→ [Go to repo](https://github.com/lrlcardoso/VideoDataProcessing)

---

### 🔹 Data Synchronization
Aligns wrist acceleration signals from IMU loggers and video-based markers using **cross-correlation**.  
Outputs a synchronised dataset for downstream movement analysis.

📍 Depends on the outputs of both `IMU Data Processing` and `Video Data Processing`.

→ [Go to repo](https://github.com/lrlcardoso/Data_Synchronization)

---

### 🔹 Gross Movement Detector
Detects **gross arm movements** from video-based pose data and synchronised timestamps.  
Generates **binary use signals** for each limb and session.

📍 Depends on `DataSynchronization` output.

→ [Go to repo](https://github.com/lrlcardoso/Gross_Mov_Detector)

---

### 🔹 Upper Limb Activity Estimator
Estimates upper limb activity by computing:
- **Repetitions**
- **Duration**
- **Intensity**  

Integrates use signals and IMU-based metrics into a summary for each session and participant.

📍 Depends on `DataSynchronization` and `GrossMovDetector`.

→ [Go to repo](https://github.com/lrlcardoso/UL_Activity_Estimator)

---

### 🖥️ Video–IMU Player (Optional)
Interactive GUI for **visual inspection and validation** of the synchronised video and IMU signals.  
Useful for reviewing movement patterns and signal quality in rehabilitation data.

→ [Go to repo](https://github.com/lrlcardoso/VideoIMUViewer)

---

## 📝 Citation

If you use this workflow or any of its modules in your research, please cite:

```
Cardoso, L. R. L. (2025). RehabTrack_Workflow: A Modular Video–IMU Framework for Analysing Upper-Limb Physiotherapy Data. GitHub. https://doi.org/XXXX/zenodo.XXXXX
```

---

## 🛠 License

- Code: [MIT License](LICENSE)
- Documentation: [CC BY 4.0](LICENSE-docs)

---

## 🤝 Acknowledgments

This framework builds upon open-source tools including:
- PyTorch, TorchReID, OpenCV
- YOLO-Pose
- PyQtGraph, AV
- MATLAB and signal processing libraries

