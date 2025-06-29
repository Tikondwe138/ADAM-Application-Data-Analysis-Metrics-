# ADAM — Application Data Analysis & Metrics

**ADAM** is a modular, lightweight, AI-augmented web application designed for field deployment in environments with limited or no internet connectivity. It enables structured tracking, analysis, and strategic forecasting of job and internship applications — specifically tailored for use in developing job markets such as Malawi.

---

## Key Features

* **CSV-Based Local Database**: No external database dependencies. Fully portable and offline-capable.
* **Sector & Method Tracking**: Categorize applications by sector (e.g., Finance, Health) and submission method (Online/Physical).
* **Full CRUD Functionality**: Add, edit, delete, and retrieve application records via terminal or web UI.
* **Weekly Metrics Dashboard**:

  * Average response time
  * Sector-based response rates
  * Conversion ratios (Application → Interview → Offer)
* **Visualization Support**: Generates interactive analytical charts using Plotly and Matplotlib.
* **AI-Driven Insights**:

  * Predictive feedback on application success
  * Percentile-based confidence scoring
  * Textual summaries outlining performance trends and weaknesses
* **Offline-First Design**: All features work without internet access, ideal for decentralized or bootstrapped deployments.

---

## Technology Stack

| Layer         | Technology                                       |
| ------------- | ------------------------------------------------ |
| Backend       | Python 3.10+, FastAPI                            |
| Frontend      | TailwindCSS (White, Purple, Black theme), Jinja2 |
| Data Handling | Pandas, CSV files                                |
| AI Logic      | Custom rule-based models (scikit-learn optional) |
| Visualization | Plotly, Matplotlib                               |
| Templating    | Jinja2                                           |

---

## AI Insight Engine

The AI component in ADAM is a lightweight, rule-based engine powered by application metadata and historical feedback data. It includes:

* **Success Probability Estimation**: Based on empirical patterns in application response times, outcomes, and feedback.
* **Feedback Pattern Recognition**: Highlights missing steps, late submissions, or poor targeting strategies.
* **Performance Forecasting**: Outputs plain-language summaries to guide users in refining their application approach.

> NOTE: This is a probabilistic system based on historical heuristics — not a deterministic AI or real-time model. It is intended to assist, not replace, human judgement.

---

## Use Case Background

ADAM is grounded in primary field research conducted across public, private, and NGO institutions in Malawi. The application is a response to observed challenges such as:

* Lack of transparency and responsiveness in application processes
* Extended timelines for feedback (ranging from weeks to several months)
* General market saturation and applicant discouragement
* Poor data collection methods among job/internship seekers

These realities have shaped ADAM’s structure as an **offline-first**, **data-aware**, and **user-guided** solution.

---

## Installation & Local Deployment

### Prerequisites

* Python 3.10+
* Node.js & npm (for TailwindCSS)
* Git

### Setup Instructions

```bash
# Clone the repository
git clone https://github.com/yourusername/ADAM.git
cd ADAM

# Create and activate virtual environment
python -m venv env
source env/bin/activate  # For Windows: env\Scripts\activate

# Install Python dependencies
pip install -r requirements.txt

# Install TailwindCSS and build styles
npm install
npx tailwindcss -i ./static/css/styles.css -o ./static/css/output.css --watch

# Start the application
uvicorn main:app --reload
```

---

## Folder Structure

```plaintext
ADAM/
├── app/
│   ├── models/              # Application data models
│   ├── routes/              # API route definitions
│   ├── services/            # Core business logic and analytics
│   ├── ai_engine/           # AI feedback and success predictor
│   ├── templates/           # HTML templates (Jinja2)
│   └── static/              # TailwindCSS assets
├── data/
│   └── applications.csv     # Main dataset
├── main.py                  # FastAPI entry point
├── requirements.txt
└── README.md
```

---

## Sample AI Logic (Conceptual)

The AI module evaluates:

* `response_time < 7 days` = +10%
* `feedback = 'positive'` = +15%
* `sector = 'NGO'` and `method = 'physical'` = historically higher success
* `no response + >30 days` = flagged as low probability

It then outputs a probability score (`e.g. 78%`) and a diagnostic comment:

> "This application to XYZ NGO shows high likelihood of success due to quick response time and positive interview feedback. Continue targeting this sector."

---

## Development & Contribution

This project is maintained by **TIKO COLLECTIVE** under open consultancy and freelance data development services. Contributions and collaborators are welcome. Ensure all code follows linting and documentation standards.
