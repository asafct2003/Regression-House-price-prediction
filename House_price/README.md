# carprice

Compact repository for training and deploying a car price prediction model.

## Summary
Predict car sale prices from vehicle features (make, model, year, mileage, engine, fuel type, transmission, etc.). Includes data preprocessing, training, evaluation, and simple inference script.

## Repository layout
- data/               — raw and processed datasets (CSV)
- notebooks/          — EDA and experiments
- src/                — preprocessing, models, utilities
- models/             — saved model artifacts
- scripts/            — train.py, predict.py, evaluate.py
- README.md

## Dataset
Place a CSV in data/ named `cars.csv`. Expected columns (example):
- id, make, model, year, mileage, engine_size, fuel_type, transmission, doors, price

Adjust column names in src/config.py if different.

## Quickstart

1. Create environment
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

2. Train
```bash
python scripts/train.py --data data/cars.csv --out models/carprice.pkl
```

3. Predict (single record)
```bash
python scripts/predict.py --model models/carprice.pkl \
    --input '{"year":2016,"make":"Toyota","model":"Corolla","mileage":45000,"fuel_type":"Petrol","transmission":"Manual","engine_size":1.8}'
```

## Scripts
- scripts/train.py: Load CSV, preprocess, train model, save artifact.
- scripts/evaluate.py: Run evaluation on holdout set, output metrics (MAE, RMSE, R^2).
- scripts/predict.py: Load model and perform single/batch predictions (JSON/CSV).

## Model & Metrics
Default configuration trains a regression model (e.g., RandomForest). Track MAE/RMSE on validation. Update src/models.py to change algorithm.

## Configuration
Edit src/config.py to change hyperparameters, feature list, random seed, test split ratio, and paths.

## Testing
- Unit tests (if present) in tests/
- Run: `pytest -q`

## Contributing
Open issues or pull requests. Follow repository coding and testing conventions.

## License
Specify a license (e.g., MIT) in LICENSE file.

## Contact
For questions, open an issue.
