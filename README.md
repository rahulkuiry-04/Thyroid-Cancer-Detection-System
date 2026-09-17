# Thyroid Cancer Detection System

An AI-powered web application for detecting thyroid cancer from medical images using deep learning and Grad-CAM interpretability.

## Features

- **AI-Powered Analysis**: Uses a custom FibonacciNet deep learning model for accurate thyroid cancer detection
- **Grad-CAM Visualization**: Provides interpretable heatmaps showing which regions the AI focused on
- **Interface**: Streamlit dashboard
- **Report Generation**: Download detailed DOCX reports with analysis results
- **Professional UI**: Clean, medical-themed interface

🔗 **[Try the app here](<https://thyroid-cancer-detection-system-bfvyfsr2xneyzevvv4cwvd.streamlit.app/>)**

##  Project Structure

```
Thyroid new/                    
├── app_streamlit.py            # Streamlit application
├── model_architecture.py       # Custom neural network layers
├── requirements.txt            # Python dependencies
├── utils/
│   ├── config.py              # Configuration
│   ├── processing.py          # Image preprocessing
│   ├── gradcam.py             # Grad-CAM implementation
│   ├── report_generator.py   # DOCX report generation
│   └── logger.py              # Logging configuration
└── logs/
    └── app.log                # Application logs
```

##  Installation

### Prerequisites
- Python 3.8+
- pip

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd "Thyroid new"
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   venv\Scripts\activate  # Windows
   # source venv/bin/activate  # Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Hugging Face** (if model is private)
   ```bash
   huggingface-cli login
   ```

##  Usage

### Streamlit Dashboard

1. **Run Streamlit**
   ```bash
   streamlit run app_streamlit.py
   ```

2. **Access dashboard**
   Opens automatically in browser (usually `http://localhost:8501`)

##  Model Architecture

**FibonacciNet** - Custom CNN with:
- SE (Squeeze-and-Excitation) blocks
- Depthwise separable convolutions
- Avg2Max pooling layers
- Progressive channel expansion following Fibonacci sequence

**Input**: 224x224 RGB images  
**Output**: Binary classification (Benign/Malignant)

## Test Results

Evaluated on a held-out test set of 381 thyroid ultrasound images (balanced across both classes after upsampling):

| Metric | Negative (Class 0) | Positive (Class 1) | Overall |
|---|---|---|---|
| Precision | 0.86 | 0.87 | 0.86 (macro/weighted avg) |
| Recall | 0.87 | 0.86 | 0.86 (macro/weighted avg) |
| F1-score | 0.86 | 0.86 | 0.86 (macro/weighted avg) |
| Support | 191 | 190 | 381 |

**Overall Test Accuracy: 86%**

**Dataset**: 3,115 thyroid ultrasound images ([Kaggle: thyroid-cancer-classification-ultrasound-dataset](https://www.kaggle.com/datasets/diveshzz/thyroid-cancer-classification-ultrasound-dataset)), originally imbalanced (1,905 negative / 1,210 positive), balanced via upsampling before an 80/10/10 train/validation/test split.

##  Technologies

- **ML Framework**: TensorFlow/Keras
- **Model Hosting**: Hugging Face Hub
- **Visualization**: Grad-CAM, Matplotlib
- **Reporting**: python-docx
- **UI Framework**: Streamlit

##  Configuration

Edit `utils/config.py` to change:
- Hugging Face repository ID
- Model filename
- Other settings

## Logging

Logs are stored in `logs/app.log` and include:
- Model loading events
- Prediction requests
- Errors and warnings
- Grad-CAM generation status

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

##  License

GNU General Public License v3.0 (GPLv3) — see [LICENSE](LICENSE) for details.

## Author

Rahul Kuiry

##  Acknowledgments
## Acknowledgments & References

The FibonacciNet architecture and Avg-2Max pooling technique used in this project are based on:

> Roy, S., Suresh, A., Gupta, A., Tiwari, S., Sahu, P., Adhikari, P., Shekhawat, Y. S. (2025). *Fibonacci-Net: A Lightweight CNN Model for Automatic Brain Tumor Classification.* arXiv preprint arXiv:2503.13928 [eess.IV]. https://arxiv.org/abs/2503.13928

- Grad-CAM interpretability method: Selvaraju, R. R. et al. (2017). *Grad-CAM: Visual Explanations from Deep Networks via Gradient-Based Localization.* ICCV 2017.
- Medical imaging community and open-source thyroid imaging datasets used for training/fine-tuning.


