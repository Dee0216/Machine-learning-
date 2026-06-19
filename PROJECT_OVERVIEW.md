# 🚀 Rocket Injector ML Analysis Dashboard

## Project Overview

A complete Django web application for machine learning model inference with a dark, rocket-themed interface. Upload H5 models, test data, run predictions, and visualize results in an interactive dashboard.

---

## ✨ Key Features

### 🧠 Model Management
- Upload TensorFlow/Keras H5 models
- Store model metadata and descriptions
- Support for multiple models simultaneously
- Automatic model validation on upload

### 📊 Data Management
- Upload test data in multiple formats (CSV, JSON, NPY, NPZ)
- Link data to specific models
- Support for large datasets (up to 50MB)
- Data validation and format checking

### 🎯 Predictions & Analysis
- Run batch predictions on uploaded data
- Automatic metric calculation:
  - Mean Squared Error (MSE)
  - Mean Absolute Error (MAE)
  - Root Mean Squared Error (RMSE)
  - R² Score
  - Statistical summaries (mean, std, min, max)
- Execution time tracking
- Result storage and history

### 🎨 User Interface
- **Dark Theme**: Midnight blue background with orange/red accents
- **Rocket Aesthetic**: Rocket emoji, space-themed colors
- **Interactive Dashboard**: Real-time updates, smooth animations
- **Responsive Design**: Works on desktop, tablet, and mobile
- **Intuitive Layout**: Clear upload zones, easy navigation

### 📈 Results Dashboard
- Visual metrics cards
- Prediction samples (first 20 for quick preview)
- Complete result history
- Click-to-view detailed results
- Execution performance metrics

---

## 🏗️ Architecture

### Technology Stack
- **Backend**: Django 4.2 (Python web framework)
- **Database**: SQLite (development) / PostgreSQL (production)
- **Frontend**: Vanilla JavaScript + CSS3
- **ML Framework**: TensorFlow/Keras for model loading
- **Data Processing**: NumPy, Pandas

### Project Structure
```
rocket_injector/
├── manage.py              # Django entry point
├── requirements.txt       # Python dependencies
├── create_samples.py      # Sample data generator
├── setup.sh/bat          # Quick setup scripts
├── README.md             # Quick reference
├── SETUP.md              # Detailed documentation
│
├── config/               # Django configuration
│   ├── settings.py      # App settings
│   ├── urls.py          # URL routing
│   └── wsgi.py          # WSGI config
│
├── core/                 # Main application
│   ├── models.py        # Database models (ModelFile, DataFile, PredictionResult)
│   ├── views.py         # Request handlers (upload, predict, results)
│   ├── urls.py          # App URLs
│   ├── utils.py         # ML utilities (ModelLoader, prediction engine)
│   └── apps.py          # App configuration
│
├── templates/
│   └── index.html       # Dashboard UI (dark-themed)
│
└── media/               # Uploaded files (auto-created)
    ├── models/          # H5 model files
    └── data/            # Test data files
```

### Database Models

**ModelFile**
- Stores uploaded H5 model files
- Fields: name, file, created_at, description
- Relationships: has many DataFiles, has many PredictionResults

**DataFile**
- Stores test data files
- Fields: name, file, model_id, created_at, description
- Relationships: belongs to ModelFile, has many PredictionResults

**PredictionResult**
- Stores prediction results
- Fields: model_id, data_id, predictions_json, metrics_json, execution_time, created_at
- Stores full prediction data and calculated metrics

---

## 🎯 User Workflows

### Workflow 1: Quick Test
1. Open dashboard
2. Generate sample model: `python create_samples.py`
3. Upload sample model from media/models/
4. Upload sample data from media/data/
5. Run prediction
6. View metrics and results

### Workflow 2: Production Use
1. Prepare trained H5 model
2. Prepare test data (CSV/JSON/NPY)
3. Upload model to dashboard
4. Upload test data
5. Run inference
6. Review results and metrics
7. Export/analyze predictions

### Workflow 3: Model Comparison
1. Upload multiple models
2. Use same test dataset
3. Run predictions with each model
4. Compare metrics in dashboard
5. Identify best performing model

---

## 🎨 UI/UX Design

### Color Palette
- **Primary** (#ff6b35): Bright orange - call-to-action buttons
- **Secondary** (#004e89): Deep blue - accent elements
- **Dark Background** (#0a0e27): Space-black
- **Card Background** (#151933): Slightly lighter for contrast
- **Accent Neon** (#00d4ff): Cyan for data highlights
- **Success** (#00c896): Green for positive states
- **Text Primary** (#e8eef7): Light for readability

### Design Principles
1. **Dark Theme**: Reduces eye strain, modern aesthetic
2. **Rocket Motif**: 🚀 emoji, space colors, technical feel
3. **Clear Hierarchy**: Section titles, organized cards
4. **Smooth Interactions**: Hover effects, loading states
5. **Accessible**: Good contrast ratios, keyboard navigation

### Interactive Elements
- Drag-and-drop upload areas
- Form validation and feedback
- Real-time model/data selection
- Loading indicators
- Success/error messages
- Modal for detailed results

---

## 🔌 API Endpoints

### Upload APIs
```
POST /api/upload/model/
- model_file: file (H5)
- name: string
- description: string (optional)
Returns: {success, model_id, size_mb}

POST /api/upload/data/
- data_file: file (CSV/JSON/NPY/NPZ)
- model_id: int
- description: string (optional)
Returns: {success, data_id, rows, columns, size_mb}
```

### Prediction API
```
POST /api/predict/
- model_id: int
- data_id: int
Returns: {success, result_id, execution_time, metrics, sample_predictions}
```

### Query APIs
```
GET /api/models/
Returns: {models: [{id, name, created_at}]}

GET /api/models/{id}/data/
Returns: {data_files: [{id, name, created_at}]}

GET /api/result/{id}/
Returns: {metrics, predictions, model_name, data_name, created_at}
```

---

## 📋 Supported Formats

### Models
- **H5 Files**: TensorFlow/Keras neural networks
- Input validation on upload
- Automatic format detection

### Data
- **CSV**: Standard comma-separated values
- **JSON**: Array of arrays format
- **NPY**: NumPy binary format
- **NPZ**: NumPy compressed format

### Data Requirements
- Float values (auto-converted if needed)
- Shape matching model input
- No missing values
- Any number of rows

---

## 🚀 Getting Started

### Installation (Windows)
```bash
setup.bat
python manage.py runserver
```

### Installation (macOS/Linux)
```bash
chmod +x setup.sh
./setup.sh
python manage.py runserver
```

### With Sample Data
```bash
python create_samples.py
```

### Open Dashboard
```
http://127.0.0.1:8000
```

---

## 📊 Example Workflow

### Sample Use Case: Rocket Injector Efficiency Prediction

1. **Train Model** (external)
   - Collect injector performance data
   - Features: pressure, temperature, flow_rate, chamber_size
   - Target: efficiency (0-100%)
   - Save as H5: `injector_model.h5`

2. **Prepare Test Data**
   - New injector test cases: 50-1000 rows
   - Same 4 features
   - Save as CSV: `test_injectors.csv`

3. **Upload & Predict**
   - Open dashboard → http://127.0.0.1:8000
   - Upload: injector_model.h5
   - Upload: test_injectors.csv
   - Run Prediction → See efficiency predictions
   - View: MSE, R² score, execution time

4. **Analyze Results**
   - Check metrics for model quality
   - Review sampled predictions
   - Compare with expected values
   - Export results if needed

---

## 🛠️ Configuration Options

### File Upload Limits
```python
# in config/settings.py
DATA_UPLOAD_MAX_MEMORY_SIZE = 52428800  # 50MB
FILE_UPLOAD_MAX_MEMORY_SIZE = 52428800
```

### Database
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

### CORS
```python
CORS_ALLOWED_ORIGINS = [
    "http://localhost:8000",
    "http://127.0.0.1:8000",
]
```

---

## 🎓 Learning Resources

### Django Documentation
- Official: https://docs.djangoproject.com/
- Models: https://docs.djangoproject.com/en/stable/topics/db/models/
- Views: https://docs.djangoproject.com/en/stable/topics/http/views/

### TensorFlow/Keras
- Load Models: https://www.tensorflow.org/api_docs/python/tf/keras/models/load_model
- Predictions: https://www.tensorflow.org/api_docs/python/tf/keras/Model#predict

### NumPy/Pandas
- Array Operations: https://numpy.org/doc/
- DataFrame: https://pandas.pydata.org/docs/

---

## 🔒 Production Considerations

### Security
1. Change `SECRET_KEY` in settings.py
2. Set `DEBUG = False`
3. Configure `ALLOWED_HOSTS`
4. Use environment variables for secrets
5. Enable HTTPS/SSL
6. Implement user authentication
7. Add rate limiting

### Performance
1. Use PostgreSQL instead of SQLite
2. Add caching layer (Redis)
3. Implement async task queue (Celery)
4. Use CDN for static files
5. Optimize model loading
6. Add result pagination

### Scalability
1. Docker containerization
2. Load balancer setup
3. Database replication
4. Model file storage (S3/GCS)
5. Distributed task processing

---

## 📈 Future Enhancements

### Potential Features
- [ ] Model performance comparison charts
- [ ] Prediction visualization graphs
- [ ] Batch processing with progress tracking
- [ ] Model versioning and rollback
- [ ] User authentication and permissions
- [ ] Result export (CSV, JSON, PDF)
- [ ] Automated model retraining
- [ ] A/B testing framework
- [ ] Model deployment to production
- [ ] Real-time monitoring dashboard

---

## 📝 Notes

- **First TensorFlow Load**: ~3-5 seconds (framework initialization)
- **Model Caching**: Models kept in memory during predictions
- **Result Storage**: Indefinite (consider cleanup in production)
- **Large Datasets**: >100MB may need optimization
- **Concurrent Predictions**: SQLite limited, use PostgreSQL for scaling

---

**Built with ❤️ for machine learning engineers**

*Ready to launch your ML projects to the next level? 🚀*
