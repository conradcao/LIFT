<div align="center">  
  <img src="./image/Lift_logo.png" width="300"> 
</div>  

# LIFT: Lifetime Inference via Fuel-cell Transformer
LIFT is a specialized deep learning framework designed for the prognostics of PEMFC operating under aviation-specific mission profiles. Unlike standard stationary or automotive datasets, this project focuses on the high-frequency dynamics and long-term degradation patterns unique to urban air mobility environments.

## 🚀 Key Innovations: Why "Aviation-Specific"?
Traditional PHM models often fail when applied to aviation because they do not account for the unique stress factors of 3D mobility. This project introduces two major breakthroughs:
1. Flying Car Mission Profile SimulationMost open-source fuel cell data is based on the New European Driving Cycle (NEDC). LIFT is trained on data simulating eVTOL (Electric Vertical Take-off and Landing) cycles, characterized by:High-Power Take-off/Landing: Rapid transients that accelerate membrane degradation.Compressor Power Penalty: Dynamic modeling of auxiliary system losses at varying altitudes.Aviation Ambient Dynamics: Environmental impacts on the Net Power Loss Rate (RNPLR).
2. Global Lifetime Clock (GLC)To solve the "Naive Predictor" trap (where models simply lag behind the previous time step), we inject a Global Lifetime Clock into the Transformer's attention mechanism. This allows the model to differentiate between "Youth," "Middle-age," and "End-of-Life" phases, ensuring accurate trend extrapolation rather than simple value repetition.🛠 Architecture
The core engine is a Time-Aware Transformer that processes multi-dimensional health indicators:Inputs: [Global_Time, Current_Load, Compressor_Penalty, RNPLR_History]Model: Multi-head Self-Attention + Positional Encoding.Output: Direct estimation of the Health Indicator (Net Power Loss Rate).

## 📊 Performance 
MetricsThe model achieves high precision in capturing the non-linear degradation slope of aviation fuel cells:MetricValueDescriptionRMSE~0.0149Root Mean Square Error (Absolute Accuracy)MAPE25.46%Mean Absolute Percentage Error$R^2$ Score0.85+Coefficient of Determination (Trend Capture)

## 📈 Visualizations
The model is evaluated by comparing the First 300 Steps (Initial Stability) vs. the Last 300 Steps (Accelerated Degradation).[Insert generated comparison plot here: results/prediction_comparison.png]

## 📦 Installation & Usage
Clone the repo:
```bash
git clone https://github.com/conradcao/LIFT.git
cd LIFT
```
Install dependencies:
```bash
pip install -r requirements.txt
```
Train and Evaluate:
```bash
python main.py
```


## 📂 Project Structure
```Plaintext
├── data/                   # Aviation Mission Profile Datasets
├── models/                 # Transformer & Global Clock implementation
├── utils/                  # Preprocessing & Aviation Metrics
├── main.py                 # Training & Evaluation entry point
└── README.md
```

## 📜 License & Citation
Distributed under the MIT License.If you use this work in your research, please cite the foundational aviation degradation studies:Lv et al. (2024). Transformer Based Long-Term Prognostics for Dynamic Operating PEM Fuel Cells.Kang et al. (2025). Performance degradation in PEMFC systems for aviation applications.Author: conradcao Keywords: Flying Cars, eVTOL, Fuel Cell, PHM, Transformer, Aviation AI.
