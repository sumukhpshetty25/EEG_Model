# 🧠 EEG-Based Imagined Speech Classification with 3D-CNN + BiLSTM  

## 📌 Project Overview  
This project implements a **hybrid deep learning model** for **imagined speech classification** using EEG signals.  
The pipeline converts EEG time-series data into **spatio-temporal topographic maps**, which are processed by a **3D-CNN + BiLSTM** network.  

✨ The model is trained and evaluated using **10-fold cross-validation**, achieving an **average accuracy of 81.67%**.  

---

## ⚡ Data Processing Workflow  

### 🔹 1. Data Preprocessing  
- 📂 Load EEG data from `.mat` files  
- ⚡ **40 Hz Notch Filter** → removes power line noise  
- 🧹 **Common Average Referencing (CAR)** → reduces common noise  
- 🎯 Select **19 EEG channels** (frontal, central, temporal, parietal lobes)  

### 🔹 2. Feature Engineering  
- ⏱️ Segment EEG into **125 ms windows** (50% overlap)  
- 🗺️ Generate **32×32 topographic maps** via cubic interpolation  
- 🎨 Convert maps into **RGB images** (jet colormap)  
- 📊 Each trial → sequence of **48 maps** → shape: `(32, 32, 3, 48)`  

### 🔹 3. Model Architecture  
- 🧩 **3D-CNN** → extracts spatio-temporal features  
- 🔄 **Bi-LSTM** → learns forward + backward temporal dependencies  
- 🎯 **Dense + Softmax** → classifies into **5 imagined speech classes**  

---

## 📊 Training & Evaluation  

- ✅ **10-Fold Cross Validation**  
- ⚙️ Optimizer: **Adam**  
- 📉 Loss: **Categorical Cross-Entropy**  
- 🔁 Epochs: **150**  
- 📈 Metrics: Accuracy, Precision, Recall, F1-score  

**Final Result:**  
- 🏆 **Average Accuracy: 81.67%**  
- ✔️ Detailed performance reported with **confusion matrix & classification report**  

---

## 🚀 How to Run  

1. **Clone the repository**  
   ```bash
   git clone https://github.com/sumukhpshetty25/EEG_Model.git
   cd EEG_Model
2. **Open the Jupyter Notebook**
   ```bash
     jupyter notebook 3DCNN-BILSTM.ipynb
3. **Run**
   Run all cells → preprocessing → feature generation → model training → evaluation
