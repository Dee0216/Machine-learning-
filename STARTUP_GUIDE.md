# 🚀 Rocket Injector Dashboard - Startup Guide

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║          🚀 ROCKET INJECTOR ML DASHBOARD 🚀              ║
    ║                                                           ║
    ║        ML Model Inference with Dark Theme UI              ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

---

## 🎯 Quick Start (5 minutes)

### Prerequisites
- Python 3.8+ installed
- pip package manager
- ~500MB disk space

### Step 1: Extract Project
```bash
# Extract the rocket_injector folder to your desired location
cd rocket_injector
```

### Step 2: Run Setup (Choose Your OS)

#### Windows
```bash
# Double-click setup.bat OR run in terminal:
setup.bat
```

#### macOS/Linux
```bash
chmod +x setup.sh
./setup.sh
source venv/bin/activate
```

### Step 3: Start Server
```bash
python manage.py runserver
```

### Step 4: Open Dashboard
```
http://127.0.0.1:8000
```

🎉 **You're ready to go!**

---

## 📦 What Gets Installed

```
✓ Django 4.2.0          - Web framework
✓ TensorFlow 2.12.0     - Model loading
✓ NumPy 1.24.3          - Numerical computing
✓ Pandas 2.0.2          - Data processing
✓ h5py 3.8.0            - HDF5 file handling
✓ CORS Headers          - Cross-origin requests
```

**Total size**: ~800MB (first install)

---

## 🧪 Test with Sample Data

```bash
# Generate sample model and data files
python create_samples.py

# Output:
# ✅ Model saved to media/models/sample_injector_model.h5
# ✅ Test data CSV saved to media/data/sample_test_data.csv
# ✅ Test data JSON saved to media/data/sample_test_data.json
# ✅ Test data NPY saved to media/data/sample_test_data.npy
```

Then in dashboard:
1. Refresh page
2. Model appears in "Available Models"
3. Select model → Upload test data
4. Run prediction → View results

---

## 🎮 Dashboard Tour

### Layout Overview

```
┌─────────────────────────────────────────────────────────┐
│  🚀 Rocket Injector Analytics    │ Models: X │ Pred: Y  │  Header
├─────────────────────────────────────────────────────────┤
│                                                         │
│  📤 Upload & Analyze Section                           │
│  ┌──────────────────┬──────────────────┐              │
│  │ 🧠 Upload Model  │ 📊 Upload Data   │              │
│  │ (H5 file)        │ (CSV/JSON/NPY)   │              │
│  └──────────────────┴──────────────────┘              │
│                                                         │
│  📋 Available Models                                   │
│  ┌─────────────────────────────────────┐             │
│  │ Model 1  │ Model 2  │ Model 3       │             │
│  └─────────────────────────────────────┘             │
│                                                         │
│  🎯 Run Predictions                                   │
│  ┌──────────────────────────────────────┐            │
│  │ Select Model │ Select Data │ Run     │            │
│  └──────────────────────────────────────┘            │
│                                                         │
│  📈 Recent Results                                    │
│  ┌─────────────────────────────────────┐             │
│  │ Result 1  │ Result 2  │ Result 3    │             │
│  │ MSE: X.XX │ MAE: X.XX │ R²: X.XX    │             │
│  └─────────────────────────────────────┘             │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### Key Sections

**1. Upload & Analyze**
- Left card: Upload H5 model file
- Right card: Upload test data
- Both require metadata (name, optional description)

**2. Available Models**
- Shows all uploaded models
- Lists associated datasets
- Click model to view details

**3. Run Predictions**
- Select model from dropdown
- Select test data file
- Click "Run Prediction"
- Real-time status updates

**4. Recent Results**
- Shows prediction history
- Click result to view detailed metrics
- Shows execution time and sample predictions

---

## 📝 Common Tasks

### Upload a Model
```
1. Click "Upload Model (H5)" section
2. Drag H5 file OR click to browse
3. Enter model name (auto-filled from filename)
4. Add optional description
5. Click "Upload Model"
6. Wait for success message ✓
```

### Upload Test Data
```
1. Select model from dropdown first
2. Click "Upload Test Data" section
3. Drag data file OR click to browse
4. File types: CSV, JSON, NPY, NPZ
5. Add optional description
6. Click "Upload Data"
7. Wait for success message ✓
```

### Run Predictions
```
1. Go to "Run Predictions" section
2. Select model from first dropdown
3. Select data file from second dropdown
4. Click "Run Prediction"
5. Wait for completion (shows execution time)
6. Results appear in "Recent Results"
```

### View Detailed Results
```
1. Click any result card in "Recent Results"
2. Modal opens with full details
3. View metrics:
   - MSE, MAE, RMSE, R²
   - Min, Max, Mean, Std Dev
4. See sample predictions
5. Close modal with X button
```

---

## 🎨 UI Features

### Dark Theme Benefits
- 🌙 Reduces eye strain during long sessions
- 🔥 Modern, technical aesthetic
- 💙 Better for focusing on data
- 🚀 Rocket theme with orange/cyan accents

### Interactive Elements
- **Drag-and-Drop**: Upload files easily
- **Real-time Validation**: Instant feedback
- **Loading States**: Know when processing
- **Success Messages**: Confirm actions
- **Error Details**: Understand problems

### Responsive Design
- 📱 Mobile: Single column layout
- 📱 Tablet: Adjusted grid layout
- 🖥️ Desktop: Full 2-3 column layout
- 🌐 Any screen size supported

---

## ⚙️ Configuration Guide

### Change Upload Size Limit
Edit `config/settings.py`:
```python
# Default: 50MB
DATA_UPLOAD_MAX_MEMORY_SIZE = 52428800  # Change this value
FILE_UPLOAD_MAX_MEMORY_SIZE = 52428800
```

### Change Server Port
```bash
# Run on port 8001 instead of 8000
python manage.py runserver 8001
```

### Enable Admin Panel
```bash
# Create superuser
python manage.py createsuperuser

# Access admin at http://127.0.0.1:8000/admin/
```

---

## 🐛 Troubleshooting

### Issue: Module not found error
```bash
# Solution: Install dependencies
pip install -r requirements.txt
```

### Issue: Port 8000 already in use
```bash
# Solution: Use different port
python manage.py runserver 8001
```

### Issue: TensorFlow installation fails
```bash
# Solution: Install CPU version
pip install tensorflow-cpu

# OR check: https://tensorflow.org/install
```

### Issue: Database errors
```bash
# Solution: Reset database
python manage.py migrate --run-syncdb
```

### Issue: File upload fails
```bash
# Solution 1: Check file format (must be .h5, .csv, .json, etc.)
# Solution 2: Check file size (max 50MB)
# Solution 3: Clear browser cache
```

### Issue: Model not loading
```bash
# Check:
# - File is valid H5/Keras format
# - TensorFlow is installed
# - Model architecture is compatible
```

---

## 📊 Example Workflow

### Scenario: Test Rocket Injector Efficiency Model

```
Step 1: Prepare Files
├── model.h5 (trained Keras model)
├── test_data.csv (500 test cases)
└── README.txt (file descriptions)

Step 2: Start Dashboard
├── python manage.py runserver
├── Open http://127.0.0.1:8000
└── See empty dashboard

Step 3: Upload Model
├── Click "Upload Model"
├── Select model.h5
├── Enter: "Injector Efficiency v1.0"
├── Click Upload
└── ✓ Success! Model appears in list

Step 4: Upload Test Data
├── Select model from dropdown
├── Click "Upload Test Data"
├── Select test_data.csv
├── Click Upload
└── ✓ Success! Shows 500 rows, 4 columns

Step 5: Run Predictions
├── Select model: "Injector Efficiency v1.0"
├── Select data: "test_data.csv"
├── Click "Run Prediction"
├── Wait 5-10 seconds
└── ✓ Results appear!

Step 6: Review Results
├── Check metrics:
│   ├── MSE: 0.034 (good!)
│   ├── MAE: 0.142
│   ├── R²: 0.956
│   └── Execution: 2.3 seconds
├── View sample predictions
├── Click for detailed analysis
└── ✓ Mission accomplished!
```

---

## 🚀 Performance Notes

| Operation | Time | Notes |
|-----------|------|-------|
| First Load | 3-5s | TensorFlow initialization |
| Model Upload | 1-2s | File transfer + validation |
| Data Upload | 1-5s | Depends on file size |
| Prediction (100 rows) | 0.5-2s | Depends on model complexity |
| Prediction (1000 rows) | 2-10s | Batch processing |

---

## 💾 File Organization

```
rocket_injector/
├── 📄 README.md              # Quick reference
├── 📄 SETUP.md               # Detailed docs
├── ⚙️  manage.py             # Django entry point
├── 📋 requirements.txt       # Dependencies
├── 🐍 create_samples.py      # Sample generator
├── 🛠️  setup.bat / setup.sh  # Auto-setup
│
├── 📁 config/
│   ├── settings.py           # Configuration
│   ├── urls.py               # URL routing
│   └── wsgi.py               # WSGI config
│
├── 📁 core/
│   ├── models.py             # Database models
│   ├── views.py              # API handlers
│   ├── urls.py               # App URLs
│   └── utils.py              # ML utilities
│
├── 📁 templates/
│   └── index.html            # Dashboard UI
│
├── 📁 media/ (auto-created)
│   ├── models/               # H5 files
│   └── data/                 # Test data
│
└── 📁 static/
    └── (CSS, JS if added)
```

---

## 🎓 Learning Resources

### For Beginners
1. **Django Basics**: https://docs.djangoproject.com/en/stable/intro/
2. **Python HTTP Requests**: https://docs.python.org/3/library/urllib.html
3. **HTML/CSS/JS**: https://developer.mozilla.org/en-US/docs/Web/

### For ML Engineers
1. **TensorFlow Models**: https://www.tensorflow.org/guide/keras
2. **Model Saving/Loading**: https://keras.io/api/models/
3. **NumPy Arrays**: https://numpy.org/doc/stable/reference/

### For Data Science
1. **Pandas DataFrames**: https://pandas.pydata.org/docs/
2. **File Formats**: https://docs.scipy.org/doc/numpy/reference/generated/numpy.load.html
3. **Metrics**: https://scikit-learn.org/stable/modules/model_evaluation.html

---

## 📞 Getting Help

### Issue Not Listed?
1. Check SETUP.md for detailed troubleshooting
2. Review PROJECT_OVERVIEW.md for architecture
3. Check Django logs: Look for error messages in terminal
4. Enable DEBUG mode for detailed errors (development only)

### Common Fixes
- **Restart server**: `Ctrl+C` then `python manage.py runserver`
- **Clear cache**: `Ctrl+Shift+Delete` in browser
- **Reinstall deps**: `pip install -r requirements.txt --force-reinstall`
- **Reset DB**: Delete `db.sqlite3` and run `python manage.py migrate`

---

## 🎉 Next Steps

1. ✅ Run setup script
2. ✅ Start server
3. ✅ Generate sample data
4. ✅ Upload sample model
5. ✅ Upload sample data
6. ✅ Run prediction
7. ✅ Review results
8. 🎓 Customize for your needs!

---

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║  🚀 Ready to Launch Your ML Models? 🚀                   ║
    ║                                                           ║
    ║  Open: http://127.0.0.1:8000                             ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**Happy analyzing! 🎯**
