# MindCast — Student Mental Health Score Prediction

MindCast is a machine learning web application that predicts student mental health scores using demographic, academic, social media usage, and lifestyle-related features. It combines a Scikit-learn regression model with a FastAPI backend and an interactive frontend built using HTML, CSS, and JavaScript.

## Features

- **Mental Health Score Prediction:** Predicts student mental health scores using a Random Forest regression model.
- **Data Preprocessing:** Uses feature engineering, categorical encoding, and numerical feature scaling.
- **REST API:** Provides prediction endpoints using FastAPI.
- **Input Validation:** Uses Pydantic to validate incoming user data.
- **Interactive Frontend:** Allows users to enter relevant information and view prediction results.

## Model Performance

The model's reported test-set evaluation metrics are:

| Metric | Result |
|---|---:|
| R² Score | 91.18% |
| Mean Squared Error (MSE) | 0.1549 |

*These metrics reflect the model evaluation results from the project notebook.*

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation and preprocessing |
| Scikit-learn | Model training, preprocessing, and prediction |
| FastAPI | Backend REST API |
| Pydantic | Request data validation |
| HTML | Frontend structure |
| CSS | Frontend styling |
| JavaScript | Frontend interactivity |
| Uvicorn | ASGI server for running the API |

## Project Architecture

1. **User Input:** The frontend collects student demographic, academic, social media usage, and lifestyle information.
2. **API Request:** JavaScript sends the input data to the FastAPI backend.
3. **Input Validation:** Pydantic validates the request payload.
4. **Model Inference:** The trained Scikit-learn pipeline preprocesses the input and generates a prediction.
5. **Result Display:** The frontend displays the predicted mental health score.

## Getting Started

### Prerequisites

- Python 3.12
- Git
- A web browser

### 1. Clone the Repository

```bash
git clone https://github.com/aaxhay/MindCast.git
cd MindCast
```

### 2. Create a Virtual Environment

**Windows:**

```bash
py -3.12 -m venv .venv
.venv\Scripts\activate
```

**macOS/Linux:**

```bash
python3.12 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Ensure that the installed Scikit-learn version is compatible with the version used to save the trained model. The model was saved with Scikit-learn 1.6.1, so use that version unless you retrain and resave the model.

### 4. Start the FastAPI Server

```bash
uvicorn main:app --reload
```

The API should be available at:

```text
http://127.0.0.1:8000
```

### 5. Explore the API Documentation

FastAPI provides interactive API documentation at:

- Swagger UI: `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

## API Usage

### Health Check

**Endpoint:** `GET /`

Returns a welcome message when the API is running.

### Mental Health Score Prediction

**Endpoint:** `POST /predict`

The endpoint accepts student information, validates the request, and returns a predicted mental health score.

Example request:

```json
{
  "age": 23,
  "gender": "Male",
  "country": "India",
  "academic_level": "Undergraduate",
  "most_used_platform": "Instagram",
  "purpose_of_use": "Education",
  "avg_daily_usage_hours": 4.5,
  "daily_unlocks": 60,
  "study_hours": 5.0,
  "physical_activity_hours": 1.0,
  "sleep_hours_per_night": 7.0,
  "stress_level": "Medium"
}
```

Example response:

```json
{
  "predicted_mental_health_score": 6.78
}
```

*The response above is illustrative; actual predictions depend on the trained model and supplied input.*

## Machine Learning Workflow

1. Load and inspect the dataset.
2. Perform data preprocessing and feature engineering.
3. Encode categorical variables and scale numerical features as required.
4. Train and evaluate the Random Forest regression model.
5. Save the trained preprocessing and prediction pipeline.
6. Load the saved model in FastAPI for inference.
7. Connect the backend to the frontend for interactive predictions.

## Project Structure

```text
MindCast/
├── main.py
├── Mental_Health_Model.pkl
├── requirements.txt
├── README.md
├── *.ipynb
└── frontend files
```

*The notebook and frontend filenames should be updated to match the actual files in the repository.*

## Limitations

- Predictions depend on the quality and representativeness of the training data.
- Model evaluation scores do not establish clinical validity.
- Predicted scores should not be used as a substitute for professional mental health assessment.

## Future Improvements

- Add automated model and API tests.
- Improve input validation and error handling.
- Deploy the frontend and backend with reliable dependency versioning.
- Monitor model performance on unseen data.

## Author

**Aashay Dongre**

- GitHub: [@aaxhay](https://github.com/aaxhay)

---

*MindCast is an educational machine learning project intended for experimentation and learning.*
