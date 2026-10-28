# Credit Ledger — Credit Risk Assessment using SHAP

A machine learning web application for assessing the risk of default on consumer loan applications.

**Live Demo:** https://credit-risk-assessment-b8bm.onrender.com

## About the Project

Credit Ledger is a web application I built to explore how machine learning can help with credit risk assessment. The idea is to take information about a loan applicant and use a trained machine learning model to estimate the likelihood of loan default.

The application provides a simple interface where users can enter applicant details, loan information, and credit history. After submitting the information, the system displays an estimated default probability and the model's assessment against a decision threshold.

I also wanted to make the result easier to understand, rather than displaying only a prediction. That's where SHAP comes in: it can help explain which input features contribute to a model's prediction.

This project gave me an opportunity to work on the complete flow, from a web interface to a Python backend and a machine learning model.

## What the Application Does

### 1. Applicant Information

The application collects basic information about the applicant, including:

- Age
- Annual income
- Home ownership status
- Length of employment

These details provide context for the model's assessment.

### 2. Loan Details

Users can enter information about the loan they want to assess:

- Loan purpose, such as personal, education, medical, or debt consolidation
- Loan grade, from A to G
- Requested loan amount
- Interest rate
- Loan-to-income ratio

The loan-to-income ratio is calculated from the applicant's income and requested loan amount. The interface also allows the ratio to be adjusted manually.

### 3. Credit History

The application includes two credit-related inputs:

- Whether a previous default is recorded
- Length of credit history

These inputs are passed to the model along with the other application details.

### 4. Default Risk Assessment

After the user submits the form, the application displays the estimated probability of default.

For example, a result of **1.7% default probability** represents the model's estimated probability for that particular set of inputs. It is not a guarantee that the applicant will or will not default.

The interface also displays a decision threshold, which can be used to compare the predicted probability with a configured cutoff. The final interpretation depends on how the model and threshold are implemented in the application.

### 5. Model Explainability with SHAP

SHAP (SHapley Additive exPlanations) is a technique for understanding machine learning predictions.

It can help show how individual features influence a model's output, making the assessment easier to investigate than a prediction alone.

The project uses SHAP as part of its explainability approach. The exact explanations depend on the trained model, the input values, and how the SHAP results are presented by the application.

## Tech Stack

The project uses the following technologies:

- **Python** — application and machine learning logic
- **FastAPI** — backend API
- **Uvicorn** — local ASGI server
- **Pandas** — data handling and preprocessing
- **Scikit-learn** — machine learning utilities
- **XGBoost** — gradient-boosted machine learning model
- **SHAP** — model explainability
- **Joblib** — loading and saving serialized model objects
- **HTML** — page structure
- **CSS** — styling and layout
- **JavaScript** — frontend interactions
- **Render** — deployment

## How It Works

The application follows a simple request-and-response flow:

1. The user opens Credit Ledger in the browser.
2. The frontend collects the applicant, loan, and credit history details.
3. JavaScript sends the form data to the backend.
4. FastAPI receives the request and processes the input.
5. The backend prepares the input in the format expected by the trained model.
6. The model generates a prediction.
7. The application returns the result to the frontend.
8. The interface displays the estimated default probability and decision information.

SHAP can be used to explain the prediction when the relevant explanation logic is enabled.

## Running the Project Locally

You can run the application on your own computer by following these steps.

### Prerequisites

Install the following:

- Python compatible with the project's dependencies
- Git
- A code editor, such as Visual Studio Code

### 1. Clone the repository

Replace `YOUR-USERNAME` with your GitHub username.

```bash
git clone https://github.com/YOUR-USERNAME/Credit-Risk-Assessment-SHAP.git
cd Credit-Risk-Assessment-SHAP
```

If your GitHub repository has a different name, use its actual URL and folder name.

### 2. Create a virtual environment

On Windows PowerShell:

```powershell
python -m venv .venv
```

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

Make sure `requirements.txt` is present in the project directory.

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If the application imports SHAP but it is missing from the requirements file, install a version compatible with the rest of the environment and add it to `requirements.txt`.

### 4. Start the application

If the FastAPI instance is named `app` inside `main.py`, run:

```powershell
uvicorn main:app --reload
```

Open the application in your browser:

http://127.0.0.1:8000

FastAPI's interactive API documentation is generally available at:

http://127.0.0.1:8000/docs

Keep the terminal open while using the local application. Press `Ctrl + C` to stop the development server.

## Deployment

The application is deployed on Render and can be accessed here:

**https://credit-risk-assessment-b8bm.onrender.com**

The deployed version allows users to try the web interface without setting up the project locally. Availability and response time depend on the deployment configuration and hosting service.

## Project Structure

The exact files may vary depending on the repository, but the project includes the following main components:

```text
Credit-Risk-Assessment-SHAP/
│
├── main.py                 # FastAPI application
├── requirements.txt        # Python dependencies
├── .gitignore              # Files excluded from Git
├── README.md               # Project documentation
├── style.css               # Frontend styling
├── script.js               # Frontend interactions
└── ...                     # Model, data, and other project files
```

The model and dataset filenames are intentionally not listed here because they depend on the files included in the repository.

## Security and Data Handling

The project should be used with appropriate care when handling applicant information.

- Do not commit passwords, API keys, or private configuration files to GitHub.
- Keep local environment files and private datasets out of version control.
- Avoid entering real applicants' personal or financial information into a public demo.
- Do not treat a model prediction as the sole basis for a real lending decision.
- Review the model's limitations, training data, and performance before using it for consequential decisions.

The default probability is a model estimate, not a guarantee of future behaviour. A displayed decision threshold is a configuration choice and should not be interpreted as proof that an applicant is creditworthy or uncreditworthy.

## What I Learned

Working on Credit Ledger helped me connect several parts of a machine learning application: collecting input through a web interface, passing data to a Python backend, loading a trained model, and presenting its prediction in a useful format.

It also gave me a chance to explore model explainability with SHAP and understand why a machine learning application should communicate more than just a predicted result.

## Future Improvements

Some areas I would like to explore further include:

- Improving input validation and error handling
- Adding clearer explanations of individual predictions
- Evaluating model performance on unseen data
- Improving accessibility and responsive design
- Adding automated tests for the API and prediction pipeline
- Documenting model limitations and appropriate use

## Disclaimer

Credit Ledger is a machine learning project intended for educational and demonstration purposes. Its predictions should not be treated as financial advice or used as the sole basis for lending decisions. The quality of its predictions depends on the model, its training data, input quality, and evaluation methodology.

---

**Built with Python, FastAPI, machine learning, and SHAP.**
