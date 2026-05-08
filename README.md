# Credit Card Fraud Detection Studio

A visually interactive, single-file web application for **Credit Card Fraud Detection** using a **Logistic Regression + SMOTE** baseline trained on the Kaggle credit card fraud dataset.

This project is designed as a practical fraud-classification system for demos, academic submissions, and portfolio use. It combines model-driven fraud scoring, dataset analysis, batch screening, Firebase logging, and browser-side custom model training in one standalone HTML application.

## Overview

Fraud detection is a classic **imbalanced binary classification** problem where fraudulent transactions are rare, but the cost of missing them is high.

This application focuses on:
- Detecting whether a transaction is **fraudulent** or **legitimate**
- Using **Precision, Recall, F1-score, and PR-AUC** instead of misleading accuracy
- Providing an interactive UI for **single transaction scoring**
- Allowing **batch transaction screening**
- Letting users upload **same-schema fraud datasets** and train their own browser-side classifier
- Optionally logging activity and model metadata with **Firebase / Firestore**

## Key Features

- Single-file HTML application
- Pre-trained **Logistic Regression + SMOTE** fraud baseline
- Interactive fraud probability scoring
- Adjustable decision threshold
- Risk-band output: `Low`, `Elevated`, `High`
- Feature contribution view for individual predictions
- Kaggle dataset upload and visualization
- Batch CSV/ZIP screening and downloadable scored output
- Custom same-schema dataset upload and browser-side model training
- Saved custom model registry in browser storage
- Optional Firebase integration for event logging and model metadata

## Tech Stack

- HTML, CSS, JavaScript
- Plotly.js for charts
- PapaParse for CSV parsing
- JSZip for ZIP dataset support
- Firebase Firestore for optional logging
- Client-side logistic regression inference
- Embedded model parameters from an offline trained fraud baseline

## Dataset

This project uses the **Kaggle Credit Card Fraud Detection dataset**, which contains:

- `Time`
- `Amount`
- `V1` to `V28`
- `Class`

Where:
- `Class = 0` means legitimate transaction
- `Class = 1` means fraudulent transaction

The `V1` to `V28` features are PCA-transformed variables used to preserve privacy.

## Model Approach

### Embedded Baseline
The default classifier in this app is based on:

- **Logistic Regression**
- **Robust Scaling**
- **SMOTE** for class imbalance handling
- Evaluation centered on **PR-AUC**, **Precision**, **Recall**, and **F1-score**

### Custom Dataset Training
Users can also upload another dataset with the **same schema** and train a browser-side classifier that:
- uses the same feature structure
- performs class balancing for minority fraud rows
- can be activated inside the same simulator and batch monitor

## Application Modules

### 1. Overview
Shows:
- PR-AUC
- threshold trade-offs
- precision / recall / F1 trends
- top model coefficients
- most correlated fraud-related features

### 2. Dataset Analyzer
Users can:
- upload the Kaggle dataset or a similar labeled dataset
- inspect fraud rate and class distribution
- see fraud by hour of day
- analyze top feature correlations

### 3. Live Classifier
Users can:
- enter transaction values
- simulate single predictions
- view fraud probability
- inspect feature-level contribution impact

### 4. Batch Monitor
Users can:
- upload a full transaction batch
- classify all rows at once
- inspect flagged high-risk transactions
- download the scored results as CSV

### 5. Custom Model Registry
Users can:
- train a custom fraud model from an uploaded dataset
- save it in browser storage
- switch between baseline and custom models
- reuse the same prediction and batch features

### 6. Ops Log
Tracks:
- local event history
- Firebase logging status
- saved custom model count
- active classifier details

## Firebase Integration

This app includes your Firebase web configuration for optional client-side logging.

Firebase is used for:
- storing event logs
- storing trained custom model metadata

Important:
- Firebase web config is safe for client apps
- secret server-side API keys should **not** be embedded in a public HTML file
- Firestore write access depends on your Firebase security rules

## How to Run

Because this is a standalone HTML app, no backend setup is required.

### Option 1: Open directly
Just open:

`credit_card_fraud_detection.html`

in any modern browser.

### Option 2: Host it
You can host it on:
- GitHub Pages
- Netlify
- Vercel
- Firebase Hosting
- any static hosting platform

## How to Use

1. Open the app in a browser
2. Use the default Kaggle baseline model
3. Upload the Kaggle dataset to unlock live dataset analysis
4. Score individual transactions in the Live Classifier tab
5. Upload a batch file in Batch Monitor to classify multiple rows
6. Train a custom same-schema model if you want dataset-specific behavior
7. Optionally connect Firestore logging through your Firebase project

## File Structure

- `credit_card_fraud_detection.html` — complete application in one file

## Security Note

This project intentionally keeps the app as a **client-side HTML file**.

That means:
- Firebase web config can be included
- secret AI keys should not be hardcoded
- no authentication system is included
- sensitive backend-only operations should be moved to a secure API if needed later

## Ideal Use Cases

- Academic mini project
- IEEE-style fraud detection prototype
- Interactive ML demo
- Portfolio project
- Static-hosted fraud analytics app

## Future Improvements

- Secure backend API for protected AI features
- downloadable PDF fraud analysis reports
- threshold optimization assistant
- richer custom model training controls
- confusion matrix for uploaded labeled batch files
- model comparison dashboard

## Author

Built as an interactive **Credit Card Fraud Detection** system focused on practical classification, interpretability, and deployment simplicity.
