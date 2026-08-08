🎓 Student Performance Prediction System

An end-to-end Machine Learning application that predicts a student'sMathematics Score using academic, demographic, and social factors.

This project goes beyond model training by implementing a complete,modular ML workflow including data ingestion, data validation, datatransformation, model training, artifact management, and web-basedprediction.

🚀 Project Overview

The Student Performance Prediction System takes student-relatedinformation as input and predicts the expected Mathematics score using atrained Machine Learning model.

The project is designed using a production-oriented structure so thatindividual stages of the ML workflow remain modular, reusable, andeasier to maintain.

What the application does

Accepts student information through a web interface.

Processes categorical and numerical features.

Applies the same preprocessing pipeline used during training.

Loads the trained ML model.

Generates a Mathematics Score prediction.

Displays the prediction through a user-friendly web interface.

✨ Key Features

📊 End-to-end Machine Learning pipeline

🧹 Automated data ingestion and preprocessing

🔍 Data validation before model training

⚙️ Reusable data transformation pipeline

🤖 Automated model training and evaluation

💾 Model and preprocessor artifact storage

🌐 Flask-based prediction application

🎨 HTML/CSS frontend

📦 Modular and scalable project architecture

🐳 Docker support

📝 Logging and custom exception handling

🔁 Reproducible train-test split

🧩 Configuration-driven ML workflow

📊 Dataset

The project is based on a student performance dataset containingacademic, demographic, and social attributes.

Input Features

Feature                 Description             Type

Gender                  Student gender          Categorical

Race/Ethnicity          Student's ethnicity     Categoricalgroup

Parental Level of       Parent/guardian         CategoricalEducation               education level

Lunch                   Type of lunch received  Categorical

Test Preparation Course Whether the student     Categoricalcompleted testpreparation

Reading Score           Student's reading score Numerical

Writing Score           Student's writing score Numerical

Target Variable

Math Score

The trained model uses the input features above to estimate thestudent's Mathematics Score.

🧠 Machine Learning Workflow

The project follows a structured ML pipeline:

Raw Dataset
     │
     ▼
Data Ingestion
     │
     ▼
Data Validation
     │
     ▼
Data Transformation
     │
     ▼
Model Training
     │
     ▼
Model Evaluation
     │
     ▼
Model Artifact (.pkl)
     │
     ▼
Flask Application
     │
     ▼
User Input
     │
     ▼
Prediction

1. Data Ingestion

The dataset is loaded and divided into training and testing datasets.

Generated artifacts include:

train.csv

test.csv

These files are stored inside the artifacts directory.

2. Data Validation

The validation stage checks whether the incoming dataset follows theexpected structure and schema.

This helps prevent unexpected data issues from reaching later stages ofthe pipeline.

3. Data Transformation

The transformation stage prepares the dataset for Machine Learning.

Typical operations include:

Handling categorical variables

Encoding categorical features

Processing numerical features

Applying preprocessing consistently

Preparing the final feature matrix

The fitted preprocessing object is saved as:

preprocessor.pkl

4. Model Training

The transformed training data is passed to the model training stage.

The trained model is serialized and stored as:

model.pkl

This allows the web application to load the trained model withoutretraining it for every prediction.

5. Prediction

When a user submits the form:

The Flask application receives the input.

The saved preprocessor transforms the input.

The saved model generates a prediction.

The predicted Mathematics Score is returned to the user.

🏗️ Project Structure

MLPROJECT/
│
├── artifacts/
│   ├── model.pkl
│   ├── preprocessor.pkl
│   ├── train.csv
│   └── test.csv
│
├── catboost_info/
│
├── logs/
│
├── notebook/
│
├── src/
│   ├── components/
│   │   ├── artifacts/
│   │   ├── logs/
│   │   ├── __init__.py
│   │   ├── data_ingestion.py
│   │   ├── data_transformation.py
│   │   └── model_trainer.py
│   │
│   ├── pipeline/
│   │   ├── __init__.py
│   │   ├── exception.py
│   │   ├── logger.py
│   │   └── utils.py
│   │
│   └── __init__.py
│
├── templates/
│   ├── home.html
│   └── index.html
│
├── .dockerignore
├── .gitignore
├── application.py
├── Dockerfile
├── README.md
├── requirements.txt
└── setup.py

📁 Important Files and Their Responsibilities

application.py

Main Flask application responsible for:

Starting the web server

Rendering frontend pages

Receiving user input

Calling the prediction pipeline

Returning prediction results

src/components/data_ingestion.py

Responsible for:

Loading the dataset

Creating train/test splits

Saving processed datasets to the artifacts directory

src/components/data_transformation.py

Responsible for:

Feature preprocessing

Categorical encoding

Numerical feature processing

Creating and saving the preprocessing pipeline

src/components/model_trainer.py

Responsible for:

Training Machine Learning models

Evaluating models

Selecting the best-performing model

Saving the trained model

src/pipeline/exception.py

Contains custom exception handling used throughout the project.

src/pipeline/logger.py

Provides centralized logging functionality for tracking pipelineexecution and errors.

src/pipeline/utils.py

Contains reusable utility functions used across different parts of theproject.

templates/

Contains the HTML templates used by the Flask application.

artifacts/

Stores generated ML artifacts such as:

model.pkl
preprocessor.pkl
train.csv
test.csv

🛠️ Tech Stack

Programming Language

Python

Data Science & Machine Learning

NumPy

Pandas

Scikit-learn

CatBoost

Web Development

Flask

HTML

CSS

Development & Deployment

Git

GitHub

Docker

Virtual Environment

Project Engineering

Modular Python architecture

Logging

Custom exception handling

Serialized ML artifacts

Configuration-driven workflow

⚙️ Installation & Setup

1. Clone the repository

git clone https://github.com/rohit-thecoder/Student---Performance---System
cd YOUR_REPOSITORY

Replace the repository URL with your actual GitHub repository URL.

2. Create a virtual environment

Windows

python -m venv venv
venv\Scripts\activate

macOS / Linux

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Run the application

python application.py

The Flask application will start locally.

Open the URL shown in your terminal, commonly:

http://127.0.0.1:5000/

🐳 Run with Docker

Build the Docker image:

docker build -t student-performance-prediction .

Run the container:

docker run -p 5000:5000 student-performance-prediction

Then open:

http://localhost:5000/

📈 Model Training

The project separates data processing and model training from theprediction application.

A typical training workflow is:

Dataset
   ↓
Data Ingestion
   ↓
Train/Test Split
   ↓
Data Transformation
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Best Model
   ↓
model.pkl

The saved model can then be reused by the Flask application forpredictions.

🔐 Reproducibility

The project uses a reproducible train-test split so that experiments canbe repeated consistently.

The preprocessing pipeline is also saved along with the trained model.This is important because prediction-time data must undergo the sametransformations that were applied to the training data.

🌐 Application Interface

The web application provides a simple interface where users can enterstudent information and receive a predicted Mathematics Score.

Prediction Flow

User
 │
 ▼
HTML Form
 │
 ▼
Flask Backend
 │
 ▼
Input Processing
 │
 ▼
Saved Preprocessor
 │
 ▼
Saved ML Model
 │
 ▼
Predicted Math Score
 │
 ▼
Result Display

📸 Screenshots

Add your application screenshots here after uploading them to yourGitHub repository.

Example:



Recommended screenshots:

Home page

Prediction form

Prediction result

Project folder structure

Model training output

📂 Generated Artifacts

The training pipeline generates reusable artifacts:

Artifact             Purpose

model.pkl          Stores the trained Machine Learning modelpreprocessor.pkl   Stores the fitted preprocessing pipelinetrain.csv          Training dataset splittest.csv           Testing dataset split

🧪 Example Prediction

A user can provide values such as:

Gender: Female
Race/Ethnicity: Group B
Parental Education: Bachelor's Degree
Lunch: Standard
Test Preparation: Completed
Reading Score: 72
Writing Score: 74

The application processes these values and returns the predictedMathematics Score.

The prediction is generated by the trained model and should be treatedas a model estimate, not an official academic assessment.

📚 What I Learned

Building this project helped me understand how a Machine Learning modelcan be converted into a complete application.

Key learnings include:

Designing modular ML projects

Data ingestion and validation

Feature preprocessing

Training and evaluating ML models

Saving and loading trained models

Building reusable ML pipelines

Flask application development

Connecting frontend forms with ML predictions

Logging and exception handling

Managing project dependencies

Dockerizing an ML application

Structuring code for maintainability

🔮 Future Improvements

Possible improvements for future versions include:

Add model performance metrics to the UI

Add prediction confidence or error estimates where appropriate

Add interactive data visualizations

Add model comparison dashboard

Add database support for prediction history

Add REST API endpoints

Improve frontend styling and responsiveness

Add automated testing

Add CI/CD pipeline

Deploy the application to a cloud platform

🎯 Project Goals

This project was built to demonstrate practical understanding of:

Machine Learning + Software Engineering + Web Development +Deployment

Rather than creating only a Jupyter Notebook model, the goal was tobuild a complete workflow from raw data to a usable predictionapplication.

👨‍💻 Author

Rohit Kumar

B.Tech Computer Science & Engineering StudentMachine Learning & AI Enthusiast

Connect With Me

LinkedIn: https://www.linkedin.com/in/rohitkumar2428

GitHub: https://github.com/rohit-thecoder



⭐ Support

If you found this project useful or interesting, consider giving therepository a ⭐ on GitHub.

📄 License

This project is available for educational and learning purposes. You maymodify and extend it for your own projects and experimentation.#   S t u d e n t - - - P e r f o r m a n c e - - - S y s t e m 
 
 