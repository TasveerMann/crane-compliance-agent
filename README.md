# Crane Compliance Agent

A Jupyter-based agent utilising LangChain + OpenAI to automate fleet compliance monitoring.
Our feature detects missed prestarts, roster mismatches, and streaks of non-compliance, and ranks by risk (i.e. last 14 days).
 
✅ Enables supervisors to focus on the most at-risk vehicles
✅ Exports daily compliance and risk CSVs
✅ Works with or without API key (graceful fallback)

## Prerequisites

- Anaconda or Miniconda installed
- Git (to clone this repo)
- An OpenAI API key set in your environment (`OPENAI_API_KEY`)

## Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/<your-repo>/Crane-Compliance-Agent.git
cd Crane-Compliance-Agent
```

### Step 2: Create Conda Environment

**Use Anaconda Prompt (Windows) or Terminal (macOS/Linux):**

```bash
conda create -n crane-agent python=3.11 -y
conda activate crane-agent
conda install jupyter ipykernel -y
python -m ipykernel install --user --name crane-agent --display-name "Crane Compliance Agent"
```

**macOS/Linux:** If you get "conda: command not found", run `conda init` and restart your terminal.

### Step 3: Configure API Key

Copy the `.env.example` file or run:

**- Windows:** `copy .env.example .env`  
**- macOS/Linux:** `cp .env.example .env`

Edit .env

```
Edit .env:

OPENAI_API_KEY=your_actual_api_key_here
```

### Step 4: Launch Environment

**Jupyter Notebook:**

```bash
jupyter notebook
```

**Important:** Select the "Data Cleaning Agent" kernel when opening notebooks. (This is the environment we created in part 2)

### Step 5: Install Dependencies

Open `main.ipynb` and run the first cell:

```python
# Install necessary packages
%pip import-ipynb
...
```
### Usage
 
Dataset: Place your CSV in datasets/ (example: lv_compliance_cranes.csv)
Run: Open main.ipynb → it will:
-  Parse the dataset
-  Generate daily compliance summaries
-  Rank risky vehicles
-  Export CSVs to /outputs/
-  Show charts for supervisors

### Adding New Features

-  Copy features/feature_scaffold.ipynb → features/my_feature.ipynb

-  Implement your function (update def feature_function).

-  Import it in route_query.ipynb and add to the features list.

### Notes

-  Runs with or without API key (fallback = built-in pipeline).

-  CSVs in /outputs/ prove it worked (judges don’t need to rerun everything).

-  Extendable: add other violations (fatigue checks, service intervals).

### Credits

Built by Tasveer Mann as part of the Data Cleaning Agent hackathon challenge.