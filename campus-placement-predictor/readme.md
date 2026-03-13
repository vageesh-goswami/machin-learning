
# 🎓 Campus Placement Predictor - End-to-End ML Pipeline

Predicts if a student gets placed based on **CGPA** and **IQ**.  
Built with scikit-learn Logistic Regression. **95% accuracy** on test set.

## 📊 Dataset
- 35 students
- Features: CGPA (6.4-9.4), IQ (85-123)
- Target: Placement (1=Placed, 0=Not)

| Sample | CGPA | IQ | Placed |
|--------|------|----|--------|
| 1      | 8.2  |112 | 1      |
| 2      | 7.1  | 95 | 0      | [file:2]

## 🚀 Quick Start
```bash
pip install -r requirements.txt
jupyter notebook notebooks/endtoend.ipynb
