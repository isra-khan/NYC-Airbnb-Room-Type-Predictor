# NYC Airbnb Room Type Predictor

A web app that predicts an Airbnb listing's room type from its location, price, stay, availability, review, and host listing details. The frontend is a static HTML/CSS/JavaScript page, and predictions are served by a FastAPI API using a pre-trained scikit-learn model.

## Requirements

- Python 3.12 (the project runtime is specified in `runtime.txt`)
- A modern web browser

## Run locally

Run these commands from the project directory.

### 1. Set up the Python environment

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

### 2. Start the API

In the same terminal, start FastAPI:

```bash
uvicorn main:app --reload
```

The API runs at <http://127.0.0.1:8000>. Interactive API documentation is available at <http://127.0.0.1:8000/docs>.

### 3. Start the frontend

Open a second terminal, move to the project directory, and serve the frontend:

```bash
python3 -m http.server 5500
```

Open <http://127.0.0.1:5500> in your browser. The frontend is configured to send prediction requests to the local API at `http://127.0.0.1:8000`.

To stop either server, press `Ctrl+C` in its terminal.

## API

- `GET /` — health check
- `POST /predict` — predicts the room type from listing features

The prediction request expects latitude, longitude, price, minimum nights, number of reviews, reviews per month, host listing count, availability days, borough (`neighbourhood_group`), and neighbourhood. The response includes the predicted room type and class probabilities.

## Project files

- `main.py` — FastAPI application and prediction endpoint
- `Model_Pipeline.pkl` — pre-trained model pipeline
- `index.html`, `style.css`, `script.js` — web interface
- `nyc_airbnb_room_type_classification.ipynb` — model exploration and classification notebook
- `requirements.txt` — Python dependencies
