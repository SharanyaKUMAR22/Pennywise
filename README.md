# Pennywise — Vercel-ready web app

This is a static HTML/JavaScript conversion of the Pennywise Streamlit student expense prediction and budget advisor. It can be deployed directly to Vercel without a Python server.

## Features
- CSV upload and included sample dataset
- Overview KPIs, dataset health checks, and data preview
- Category spending chart and descriptive statistics
- Browser-side multiple linear regression expense estimate with MAE, RMSE, and R² holdout metrics
- Logistic overspending classifier, adjustable threshold, F1/AUC approximation, confusion matrix, flagged rows
- Simple exponential smoothing monthly forecast
- Interactive student budget planner
- Responsive dark navy / mint / violet Pennywise theme

## Deploy to Vercel
1. Create a GitHub repository (for example `pennywise-vercel`).
2. Upload `index.html`, `sample_monthly_expenses.csv`, and `README.md` to the repository root.
3. Sign in to https://vercel.com/ using GitHub.
4. Select **Add New → Project**, import the repository, and choose **Other** as the framework if asked.
5. Leave build command and output directory blank; deploy the static site.
6. Open the generated `.vercel.app` URL.

## Notes and differences from original Streamlit build
This version runs in the browser and does not require a Python backend. It preserves the main user-facing workflow and features, but the predictive implementation is not identical to the original: the expense estimate uses multiple linear regression rather than scikit-learn RandomForestRegressor; the overspending classifier uses a lightweight logistic model; and the monthly forecast is level-only simple exponential smoothing. The AUC is calculated from test-set ranks and is approximate in small samples. The charts use Chart.js and CSV parsing uses Papa Parse via public CDNs, so the browser needs internet access to load those libraries.

Expected CSV columns include `total_expenses`, `budget`, `monthly_income`, and `month`. Category columns are optional. Included sample data is synthetic.
