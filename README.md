# industrial safety detection
### Industrial Safety Gear Detection using YOLOv11

This repository showcases the implementation of an industrial safety gear detection system using the **YOLOv11m (medium-sized model)**. The system is trained to accurately identify five essential safety-related classes: **person**, **helmet**, **gloves**, **boots**, and **vest**, making it an effective solution for ensuring workplace safety in diverse industrial environments.

---

### **Features**
- **YOLOv11 Medium Model**: Utilizes the medium-sized variant of YOLOv11 for a balanced tradeoff between speed and accuracy.
- **Fine-Tuned Hyperparameters**: Adjusted training and testing parameters for optimal performance, especially in handling class imbalance.
- **Advanced Augmentation**: Enhanced dataset variability using mosaic, mixup, copy-paste, and other augmentation techniques.
- **Comprehensive Testing**: Evaluated using metrics such as Precision, Recall, mAP@50, and mAP@50-95 on the test dataset.

---

### **Detected Classes**
1. **Person**
2. **Helmet**
3. **Gloves**
4. **Boots**
5. **Vest**

---

### **Training Configuration**
The model was trained using the following fine-tuned hyperparameters to maximize performance:

- **Training Parameters**:
  - `epochs=100`: Trained for 100 epochs.
  - `batch=16`: Batch size set to 16 for efficient GPU utilization.
  - `imgsz=640`: Input image size of 640x640 pixels.
  - `device=0`: Training on GPU (`device=0`).
  - `cos_lr=True`: Enabled cosine learning rate scheduling for smoother convergence.
  - `box=10.0`: Increased box loss weight to improve object localization.
  - `cls=0.75`: Reduced class loss weight to balance classification performance.
  - `patience=20`: Early stopping applied if no improvement for 20 epochs.

- **Data Augmentation**:
  - `augment=True`: Enabled advanced augmentations.
  - `hsv_h=0.015`: Simulated lighting variations by adjusting hue.
  - `hsv_s=0.7`: Enhanced color intensity with saturation adjustments.
  - `hsv_v=0.4`: Introduced brightness variability.
  - `translate=0.1`: Applied random translations to simulate object shifts.
  - `mosaic=1.0`: Fully utilized mosaic augmentation.
  - `mixup=0.6`: Applied mixup augmentation with 40% probability.
  - `copy_paste=0.7`: Enabled copy-paste augmentation with 70% probability.

---

### **Testing Configuration**
The model was evaluated on the **test dataset** using the following hyperparameters:

- `imgsz=640`: Input image size of 640x640 pixels.
- `batch=16`: Batch size of 16.
- `iou=0.6`: IoU threshold of 0.6 for non-max suppression.
- `conf=0.3`: Confidence threshold of 0.3 for object predictions.
- `split='test'`: Used the test dataset split for evaluation.
- `device=0`: Testing performed on GPU (`device=0`).

---

### **Results**
The model achieved the following results on the test dataset, comprising 502 images with 2818 total instances across all classes:

| **Class**   | **Images** | **Instances** | **Precision (P)** | **Recall (R)** | **mAP@50** | **mAP@50-95** |
|-------------|------------|---------------|--------------------|----------------|------------|---------------|
| **All**     | 502        | 2818          | 0.826              | 0.852          | 0.855      | 0.574         |
| **Boots**   | 158        | 271           | 0.684              | 0.775          | 0.715      | 0.463         |
| **Gloves**  | 183        | 294           | 0.792              | 0.79           | 0.812      | 0.53          |
| **Helmet**  | 465        | 924           | 0.867              | 0.908          | 0.919      | 0.618         |
| **Person**  | 464        | 934           | 0.842              | 0.928          | 0.925      | 0.555         |
| **Vest**    | 465        | 395           | 0.827              | 0.806          | 0.905      | 0.702         |



### **Conclusion**
This implementation leverages YOLOv11m to achieve robust industrial safety gear detection with reliable performance metrics. The integration of fine-tuned hyperparameters and advanced augmentation ensures the model's applicability across diverse industrial environments.
