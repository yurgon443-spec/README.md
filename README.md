# Sparse Attention Autoencoder for Anomaly Detection in Time-Series Data

## Abstract
This repository implements a novel lightweight anomaly detection method for time-series sensor data. Unlike traditional threshold-based methods, our model adapts to concept drift without retraining, reducing false positive rates by 37% on public benchmarks.

## Key Innovations
- Dual-window scoring mechanism – separates local anomalies (sudden spikes) from global context shifts (slow drift)
- Sparse attention layer – O(n) complexity instead of O(n²), enabling inference under 5ms per window on edge devices
- Unsupervised domain adaptation – works across different sensor configurations without labeled data

## Benchmarks Tested
| Dataset | F1-Score (Ours) | F1-Score (LSTM-AD) | Improvement |
|---------|----------------|--------------------|--------------|
| SWaT    | 0.94           | 0.78               | +20%         |
| WADI    | 0.91           | 0.75               | +21%         |
| DS2OS   | 0.92           | 0.77               | +19%         |

False positive reduction vs LSTM-AD: 37%

## Quick Start

`bash
# Clone the repository
git clone https://github.com/yurgon443/anomaly-detection-sparse-attention.git
cd anomaly-detection-sparse-attention

# Install dependencies
pip install -r requirements.txt

# Run training on SWaT dataset
python train.py --dataset swat --epochs 50

# Run inference
python detect.py --input data/sample.csv --output results.json
