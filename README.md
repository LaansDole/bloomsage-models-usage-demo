# BloomSage ML Pipeline Demo

### ***Disclaimer***
**REQUIRED PYTHON VERSION: 3.10**

This is a very barebone project intended as a demonstration on how to utilize our machine learning pipeline for real-time inference in a web application with 2 components: Backend API (using FastAPI) and Frontend UI (using Streamlit).

Please note that this project is only configured to run on your local machine, and no consideration were made for streamlining deployment.

## Getting Started 🚀

Clone this repository:

```bash
git clone https://github.com/rmit-denominator/bloomsage-models-usage-demo.git
```

***At the same time, open 3 terminal consoles to run 3 servers below***
### Setup Development Environment and fetch ML Assets (Compiled recommender database and trained models from [BloomSage ML Repository Latest Release](https://github.com/rmit-denominator/bloomsage-ml/releases/latest)):


#### Backend Setup `cd backend`:

  ```bash
  python -m venv .venv
  source .venv/bin/activate
  pip install -r ./requirements.txt
  python ./ml_fetch.py
  deactivate
  ```
  ```bash
  source .venv/bin/activate
  python ./main.py
  ```

---

These folders will be created during ML assets fetching:

1. `backend/data/`: This folder contains the compiled and compressed recommender database.
2. `backend/models/`: This folder contains trained models.

---

#### Frontend Setup `cd frontend`:

  ```bash
  python -m venv .venv
  source .venv/bin/activate
  pip install -r ./requirements.txt
  deactivate
  ```
  ```bash
  source .venv/bin/activate
  streamlit run ./main.py --server.port 8081
  ```

- ***Develop Locally with Secrets***

When developing your app locally, you need to manage your secrets. Follow the steps below:

1. Add a file called `secrets.toml` in a folder called `.streamlit` at the `frontend/` of your app repository.
2. Copy and paste your secrets into the `secrets.toml` file.

Further instructions are available in the [Streamlit library Secrets management documentation](https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app/secrets-management).

> :warning: **Important**: Be sure to add `secrets.toml` to your `.gitignore` so you don't commit your secrets!

Here's what your local `frontend/` should look like:

```
frontend/
|
├── .streamlit/
|   ├── config.toml
|   └── secrets.toml  # Make sure to gitignore this!
```
**Finally, replace `MONGODB_PASSWORD` in [.env](./frontend/.env) as well as your MONGODB Cluster in [features.py](./frontend/features.py)**

#### Mockup Ecommerce Setup `cd mockup-ecommerce`:

**Demo**: https://bloomsage-mockup.netlify.app/

  ```bash
  python -m venv .venv
  source .venv/bin/activate
  pip install -r ./requirements.txt
  deactivate
  ```
  ```bash
  source .venv/bin/activate
  flask --app app --debug run
  ```

Refer to `backend/requirements.txt`, `frontend/requirements.txt`, `mockup-ecommerce/requirements.txt` for information on project dependencies.
