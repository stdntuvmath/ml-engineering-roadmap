# 10-Week Machine Learning Engineer Portfolio Roadmap

A structured roadmap to build a Machine Learning Engineer (MLE – Machine Learning Engineer) portfolio in 10 weeks.

The roadmap focuses on:

• Independent machine learning projects  
• Collaboration (Kaggle – Data Science Competition Platform, GitHub – Git Repository Hosting Platform)   
• Weekly LinkedIn updates
• Posts to this repository as an progress update (with pictures)
• A web-based machine learning trading system  
 

---

# Why I built this road map

I aim to prove that companies hire Machine Learning Engineers based on evidence of engineering capability, not certificates.

This roadmap produces that evidence through:

1. Real projects
2. Public code repositories
3. Collaboration
4. Technical writing
5. Documentation of System designs


---

# Development Environment

Primary IDE:

VS Code – Visual Studio Code (Integrated Development Environment)

extensions:

Python Extension  
Jupyter Notebook Extension  
GitLens  

Python libraries to install:

pip install numpy  
pip install pandas  
pip install matplotlib  
pip install seaborn  
pip install scikit-learn  
pip install jupyter  
pip install flask  
pip install requests  

---

# Phase 0 — AI Image Generator (Week 1)

Goal: Create an AI system that can generate an image from existing image data (not full generation yet — structured arrangement and transformation of images).

---

# Concept (IMPORTANT)

This is NOT full image generation.

This phase focuses on:

• Sampling images  
• Preprocessing images  
• Arranging image components  
• Producing a composed output  

Pipeline:

Sampling → Preprocessing → Arrangement → Output

This builds the foundation for future generative AI work.

---

# Step 1 — Project Setup

Create project folder:

projects/00-ai-image-generator

Initialize structure:

ai-image-generator
│
├── data
├── src
├── output
└── README.md

Install required libraries:

pip install numpy  
pip install opencv-python  
pip install matplotlib  
pip install pillow  

---

# Step 2 — Data Collection (Sampling)

Goal: Gather a dataset of images to work with.

Options:

• Download images manually (simple start)  
• Use a dataset (Kaggle – Data Science Competition Platform)  
• Use an API (optional advanced)  

Start simple:

Collect 20–50 images of a similar category:

Examples:

• faces  
• cars  
• houses  
• charts (this might align well with your trading focus later)  

Store in:

data/raw/

---

# Step 3 — Preprocessing

Goal: Standardize images so they can be used together.

Tasks:

• Resize all images to the same dimensions (e.g., 128x128)  
• Convert to same color format (RGB or grayscale)  
• Normalize pixel values (0–255 → 0–1)  

Example workflow:

from PIL import Image  
import numpy as np  

img = Image.open("image.jpg")  
img = img.resize((128, 128))  

arr = np.array(img) / 255.0  

Save processed images:

data/processed/

---

# Step 4 — Image Representation

Goal: Convert images into usable numerical data.

Tasks:

• Store images as NumPy arrays  
• Create a dataset array:

Example:

dataset = [img1_array, img2_array, img3_array]

Optional (slightly advanced):

Flatten images:

img.flatten()

Purpose:

• Prepares data for model-driven arrangement later  

---

# Step 5 — Arrangement Logic (Core of Phase 0)

Goal: Build logic that combines multiple images into a new output.

Start simple — DO NOT overcomplicate.

Option A — Averaging (Recommended Start)

• Take multiple images  
• Average pixel values  

Example:

output = (img1 + img2 + img3) / 3

Result:

• Blended image  

---

Option B — Grid Composition

• Place multiple images into a grid  

Example:

[img1 | img2]  
[img3 | img4]

---

Option C — Region-Based Composition

• Take sections from different images  

Example:

• top half from image A  
• bottom half from image B  

---

Purpose:

• This is your first “AI-like” transformation system  
• You are controlling how images are combined  

---

# Step 6 — Output Generation

Goal: Convert processed data back into an image.

Example:

from PIL import Image  

output_img = Image.fromarray((output * 255).astype('uint8'))  
output_img.save("output/result.png")

Store results in:

output/

---

# Step 7 — (Light) Model-Driven Arrangement

Goal: Introduce decision-making.

Simple approach:

• Randomly select images  
• Randomly choose arrangement type  

Slightly smarter approach:

• Choose images based on similarity (mean brightness, color, etc.)  

Example:

if img.mean() > threshold:  
    use in composition  

Purpose:

• This is your first step toward AI behavior  
• Not true ML yet — controlled logic  

---

# Step 8 — Documentation

README.md should include:

• Project goal  
• Explanation of pipeline:
  Sampling → Preprocessing → Arrangement → Output  
• Example inputs  
• Example outputs (images)  
• Code snippets  

---

# Step 9 — Blog Post

Title:

Building My First AI Image System (Without Using AI Models)

Content outline:

• What the system does  
• Why this is NOT true image generation yet  
• Explanation of your pipeline  
• Key lessons learned  

---

# Step 10 — LinkedIn Post

Short version:

• Announce start of your ML journey  
• Show one output image  
• Explain the pipeline in simple terms  
• State what’s coming next  

---

# Deliverables

• Working image transformation system  
• Structured project folder  
• README with visuals  
• Blog post  
• LinkedIn post  

---

# Outcome of Phase 0

You now understand:

• How image data is structured  
• How to manipulate images programmatically  
• How to build a data pipeline  

This sets the foundation for:

• Machine Learning  
• Computer Vision  
• Generative AI  

You are now ready to move into real modeling.


---

# Phase 1 — Long Term Stock Data Visualizer (Weeks 2)

This one just needs a little bit of work because I already 
designed most of it.

Goal: Demonstrate data literacy.

Download stock market datasets from yfinance.

Example datasets:
  
• daily stock market history 
• custom produced momentum indicators  
• buy/sell indications

Load dataset with Pandas.

Example workflow:

import pandas as pd  
df = pd.read_csv("dataset.csv")

Inspect dataset:

df.head()  
df.describe()  
df.info()

Create visualizations:

import matplotlib.pyplot as plt  
df["price"].hist()  
plt.show()

Deliverables:

Project folder:

projects/01-data-analysis

README explaining:

• dataset  
• variables  
• insights  

Blog post:

Exploratory Data Analysis of Housing Prices

LinkedIn update summarizing results.

---

# Phase 2 — Baseline Machine Learning Model (Weeks 3)

Goal: Build your first predictive model.

Choose a problem:

• regression  
• classification  

Split dataset:

from sklearn.model_selection import train_test_split

Train model:

from sklearn.linear_model import LinearRegression

Evaluate model:

from sklearn.metrics import mean_squared_error

Example workflow:

X_train, X_test, y_train, y_test = train_test_split(X, y)

model = LinearRegression()

model.fit(X_train, y_train)

predictions = model.predict(X_test)

### Docker Integration (Introduction)

Create your first Docker container for this project.

Tasks:

• Write a `Dockerfile` that installs Python and required libraries  
• Copy your project code into the container  
• Define a command to run your training script automatically  
• Build the container using: `docker build -t ml-model .`  
• Run the container using: `docker run ml-model`  

Purpose:

• Ensures your model runs consistently across environments  
• Introduces containerization early without complexity  
• Demonstrates reproducibility — a key MLE skill  

Deliverables:

projects/02-baseline-model

Blog post:

Building My First Machine Learning Model

LinkedIn summary.

---

# Phase 3 — Feature Engineering (Weeks 4-5)

Goal: Improve model performance.

Handle missing values.

df.fillna()

Normalize features.

from sklearn.preprocessing import StandardScaler

Create engineered features.

Example:

df["price_per_sqft"] = df["price"] / df["square_feet"]

Tune hyperparameters.

from sklearn.model_selection import GridSearchCV

Deliverables:

projects/03-feature-engineering

Blog post:

Feature Engineering for Better Machine Learning Models

---

# Phase 4 — Kaggle Collaboration (Weeks 6-7)

Goal: Gain collaborative experience.

Steps:

1. Join a Kaggle competition
2. Study top notebooks
3. Fork a notebook
4. Improve model
5. Submit predictions

Deliverables:

projects/04-kaggle-project

Blog post:

What I Learned from My First Kaggle Competition

---

# Phase 5 — Open Source Contribution (Weeks 7-8)

Goal: Demonstrate collaboration with developers.

Search GitHub for repositories.

Look for issues labeled:

good first issue

Steps:

1. Clone repository
2. Fix documentation or bug
3. Commit changes
4. Submit Pull Request (PR – Pull Request)

Deliverables:

• one merged pull request  
• documentation of contribution  

Blog post:

My First Open Source Contribution

---

# Phase 6 — Machine Learning Pipeline (Weeks 8)

Goal: Learn production ML architecture.

Pipeline steps:

1. Data ingestion
2. Preprocessing
3. Feature generation
4. Model training
5. Evaluation

### Docker Integration (Core Usage)

Break your pipeline into containerized components.

Tasks:

• Create separate Docker containers for each pipeline stage  
  - ingestion container  
  - preprocessing container  
  - training container  
• Use `docker-compose` to orchestrate multi-container execution  
• Define clear inputs/outputs between containers (files or APIs)  

Purpose:

• Simulates real-world ML systems  
• Demonstrates modular architecture  
• Shows ability to scale and isolate components  

### AWS Integration (Introduction)

Introduce cloud storage into your pipeline.

Tasks:

• Create an S3 (Simple Storage Service) bucket  
• Upload datasets to S3  
• Modify your pipeline to pull data from S3 instead of local files  
• Optionally push trained models back to S3  

Purpose:

• Separates compute from storage  
• Introduces cloud-native workflows  
• Demonstrates handling of external data sources  

Deliverables:

projects/05-ml-pipeline

Blog post:

Building a Machine Learning Pipeline

---

# Phase 7 — Time Series Modeling (Weeks 9)

Goal: Work with financial data.

Download stock market data using APIs.

Example library:

yfinance

Create time series features:

• moving averages  
• volatility  
• momentum  

Train prediction models.

### AWS Integration (Automation)

Automate data collection and processing.

Tasks:

• Use EC2 (Elastic Compute Cloud) to run scheduled data collection scripts  
OR  
• Use Lambda (serverless functions) for lightweight automation  
• Schedule jobs using cron or CloudWatch  

Purpose:

• Introduces automation and scheduling  
• Demonstrates real-time or periodic data pipelines  
• Shows transition from manual to production workflows  

Deliverables:

projects/06-time-series-model

Blog post:

Machine Learning for Stock Market Prediction

---

# Phase 8 — Web-Based ML Trading System (Weeks 10-12)

Goal: Build a full machine learning application.

Components:

1. Data collector
2. Prediction model
3. Web API
4. Dashboard

Create API using Flask – Python Web Framework.

Example structure:

trading-system
│
├── data_collector
├── model
├── api
└── dashboard

### Docker Integration (Full System)

Containerize the entire application.

Tasks:

• Create Docker containers for:
  - Flask API  
  - ML model service  
• Use `docker-compose` to run the full system locally  
• Ensure all services communicate correctly  

Purpose:

• Demonstrates full system containerization  
• Enables easy deployment  
• Mirrors real-world microservice architecture  

### AWS Integration (Production Deployment)

Deploy your application to the cloud.

Tasks:

• Launch an EC2 instance to host your application  
• Deploy your Docker containers on EC2  
• Store datasets and models in S3  
• (Optional) Use RDS (Relational Database Service) for structured data  

Purpose:

• Demonstrates real deployment experience  
• Shows ability to run ML systems in production  
• Bridges gap between development and real-world usage  

Deliverables:

projects/07-ml-trading-system

Blog post:

Building a Machine Learning Trading System

---

# Phase 9 — Portfolio Completion (Week 12)

Goal: Prepare portfolio for job applications.

Tasks:

Create portfolio website.

Include:

• project descriptions  
• architecture diagrams  
• GitHub links  

### AWS + System Design Documentation

Document your system architecture clearly.

Tasks:

• Create diagrams showing:
  User → Web App → API (EC2) → Model → S3  
• Explain how Docker containers interact  
• Describe data flow and deployment setup  

Purpose:

• Demonstrates system design thinking  
• Helps recruiters understand your work quickly  
• Elevates portfolio from code to engineering  

Write final article:

My 12 Week Journey to Becoming a Machine Learning Engineer

Publish final LinkedIn post.

---

# Weekly Publishing Schedule

Every week:

• 1 GitHub project update  
• 1 blog post  
• 1 LinkedIn progress update  

This builds a **public learning record** employers can see.

---

# Final Portfolio Outcome

At the end of of this journey I should have:

• 9 machine learning projects  
• Kaggle competition experience  
• Open source contributions  
• a machine learning trading system  
• 12+ blog posts  
• a complete GitHub portfolio  

This portfolio will demonstrate real Machine Learning Engineering capability.
