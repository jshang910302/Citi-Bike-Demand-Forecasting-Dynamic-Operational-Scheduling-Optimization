Citi Bike Station Operations Optimization

This repository contains the code and deliverables for the Citi Bike station operations optimization project. We developed both frontend and backend components to support data-driven decision making for bike rebalancing, staffing, and resource allocation.

🚀 Project Overview

Motivation: Optimize Citi Bike station operations to increase revenue, reduce costs, and improve service availability.

Approach: Use multivariate linear regression and LSTM forecasting models, combined with dynamic scheduling optimization.

📁 Repository Structure

/├── backend/        # Backend API services and model code
   ├── api/          # Flask endpoints for predictions and scheduling
   ├── models/       # Trained regression and LSTM models
   ├── data_pipeline/# ETL scripts to preprocess Citi Bike, weather, and traffic data
   └── requirements.txt
/├── frontend/       # Frontend React application and assets
   ├── src/          # React components, hooks, and services
   ├── public/       # Static assets and index.html
   ├── package.json
   └── README.md     # Local instructions for frontend
/├── docs/           # Supplementary figures, diagrams, and report excerpts
└── README.md        # This file

🔧 Frontend Deliverables

Interactive Dashboard: Built with React and D3.js, featuring:

Real-time heatmaps of station utilization and idle docks

Time-series charts for historical borrowing patterns (weekday vs. weekend)

Member vs. non-member usage breakdowns

User Interface: Responsive design with filters for date ranges, neighborhoods, and weather conditions.

Visualizations: Integrated map view (Leaflet) showing station locations and forecasted demand.



⚙️ Backend Deliverables

Data Pipeline (/backend/data_pipeline): Python scripts to:

Ingest Citi Bike trip data, weather observations, and traffic volumes

Clean, impute missing values, and feature-engineer time-based and spatial variables

Store processed records in PostgreSQL database

Predictive Models (/backend/models):

Linear Regression: Multi-variate model predicting per-station docking and staffing needs

LSTM Forecast: Time-series model (720-hour lookback) forecasting hourly borrowing counts

REST API (/backend/api): Flask service exposing endpoints:

POST /predict/regression → station-level demand and staffing forecast

POST /predict/lstm       → short-term hourly borrow volume predictions

POST /optimize/schedule  → dynamic staffing and redistribution schedule

# Example: predict with regression model
curl -X POST http://localhost:5000/predict/regression \
     -H "Content-Type: application/json" \
     -d '{"neighborhood":"Upper West Side","hour":8,"weather":"Sunny"}'

🗃 Data Sources

Citi Bike Trip Data (May 2023, multiple years for long-term trends)

Weather Observations (timeanddate.com) with dummy encoding for 4 categories

Traffic Volume (NYC OpenData), aggregated by neighborhood and hour

Demographics & Infrastructure (NYC OpenData): population density, transit coverage, public facilities

🏃 Usage Instructions

Backend Setup

cd backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python api/app.py

Frontend Setup

cd frontend
npm install
npm start

Access Dashboard: Navigate to http://localhost:3000 in your browser.

🤝 Contributing

Fork this repository

Create a feature branch (git checkout -b feature/xyz)

Commit your changes (git commit -m 'Add xyz')

Push to the branch (git push origin feature/xyz)

Open a Pull Request

📜 License

This project is licensed under the MIT License. See LICENSE for details.

