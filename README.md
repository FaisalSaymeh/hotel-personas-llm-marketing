## Notebooks

| # | Notebook | Purpose |
|---|----------|---------|
| 1 | `1- Data Preprocessing.ipynb` | Flatten nested reservation JSON, handle missing values, build customer-level features |
| 2 | `2- Clustering.ipynb` | Filter high-CLV customers, embed with Sentence-BERT, cluster with HDBSCAN |
| 3 | `3- Persona.ipynb` | Generate personas and Meta Ads text across nine LLM providers |
| 4 | `4- Persona Images Alignment & Report Generation.ipynb` | Score AI-generated images against persona text using CLIP / BLIP-2, produce HTML report |

## How to run

The project is a set of Jupyter notebooks. Open each one in Jupyter Lab, Jupyter Notebook, or VS Code and **run the cells top to bottom**. Notebooks must be run in order (1 → 2 → 3 → 4), because each one produces the input files for the next.

## Data

The reservation dataset is proprietary (Yanovis Datahub, provided by Brandnamic) and is **not** included in this repository. Input files expected in the project folder:

- `Reservations.json` — raw reservation export (input to notebook 1)
- `data.json`, `schema.json` — preprocessed data (produced by notebook 1, input to notebook 2)
- `high_clv_bookings_with_persona_clusters.csv` — clustered customers (produced by notebook 2, input to notebook 3)
- `personas_metaads_*.csv` — one file per LLM provider (produced by notebook 3, input to notebook 4)
- `images/` — AI-generated persona images (input to notebook 4)

## Requirements

- Python 3.10+
- Jupyter (Lab or Notebook)
- `pandas`, `numpy`, `scikit-learn`, `hdbscan`, `sentence-transformers`, `torch`, `transformers`
- `openai`, `anthropic`, `google-generativeai`
- `Pillow`, `matplotlib`, `seaborn`, `plotly`, `tqdm`

## API keys

Notebook 3 calls nine LLMs across five providers. In the notebook, the keys are set as placeholders like `"API-KEY"`. Open notebook 3, find the cell that sets `os.environ[...]`, and paste your own keys in place of the placeholders:

- OpenAI (GPT-5)
- Anthropic (Claude Sonnet 4.5, Claude Opus 4.6)
- Google (Gemini 2.5 flash / 2.5 pro / 3 / 3.1 Pro)
- xAI (Grok 4.1 fast reasoning)
- DeepSeek (deepseek-chat)

You only need keys for the providers you want to use — remove the others from the `PROVIDERS` list.

## Thesis

This code accompanies the Master's thesis *"Data-Driven Persona Discovery in Hospitality Using Unsupervised Learning and Foundation Models"*, defended at the Free University of Bozen-Bolzano, Faculty of Engineering, 2026.

Supervisor: Prof. Giuseppe Di Fatta  
Industry collaboration: Brandnamic / Yanovis

## Citation

If you use this code in academic work, please cite:

> Saimeh, F. (2026) *Data-Driven Persona Discovery in Hospitality Using Unsupervised Learning and Foundation Models*. Master's thesis, Free University of Bozen-Bolzano, Faculty of Engineering.

## License

Released for academic reference. The reservation data and any derived customer-level artifacts remain the property of Brandnamic / Yanovis and are not covered by this repository.
