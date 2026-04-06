# TP1 - Prompt Engineering For Multi Agent Systems

Ce projet contient un notebook de TP dedie au prompt engineering applique aux systemes multi-agents et aux LLMs.

Le notebook principal est:

- `TP1 SMA- Prompt Engineerin For Multi Agent Systems.ipynb`

## Lien du Repository GitHub

Ajoutez ici le lien de votre repository:

- GitHub: `https://github.com/<votre-username>/<votre-repository>`

## Objectifs du TP

Ce TP montre comment:

- Interagir avec differents modeles (OpenAI, Ollama, Groq) via LangChain.
- Concevoir et comparer des prompts (`zero-shot`, `few-shot`, `Chain-of-Thought`).
- Evaluer la qualite des prompts sur une tache de classification de sentiment.
- Utiliser des capacites multimodales (generation et description d'images).

## Contenu du Notebook

Le notebook couvre notamment:

- Introduction au prompt engineering pour systemes multi-agents.
- Appels LLM avec `ChatOpenAI` (API) et via clients HTTP (ex: Postman).
- Appels LLM locaux avec `ChatOllama` et interactions HTTP avec Ollama.
- Exemple avec `ChatGroq`.
- Prompting multimodal:
  - Generation d'image.
  - Description d'image (encodage base64 + requete vision).
- Use case principal: analyse de sentiment sur IMDB.
  - Chargement du dataset IMDB (`datasets`).
  - Preparation des donnees (`pandas`, `numpy`).
  - Construction d'exemples few-shot / gold examples.
  - Evaluation avec la metrique `micro-F1` (`scikit-learn`).

## Arborescence

- `TP1 SMA- Prompt Engineerin For Multi Agent Systems.ipynb`: notebook principal du TP.
- `main.py`: script Python minimal.
- `pyproject.toml`: configuration du projet et dependances.
- `README.md`: documentation du projet.

## Prerequis

- Python `>= 3.13`.
- Un gestionnaire d'environnement Python (`uv` recommande dans ce projet).
- Une cle API OpenAI (et eventuellement Groq si vous utilisez cette partie).
- Pour la partie locale: Ollama installe et service actif.

## Installation

### 1. Creer l'environnement et installer les dependances

Depuis la racine du projet:

```powershell
uv sync
```

Le notebook utilise aussi des bibliotheques de data science qui peuvent necessiter une installation supplementaire selon votre environnement:

```powershell
uv add pandas numpy scikit-learn matplotlib tqdm datasets python-dotenv session-info langchain-groq
```

### 2. Variables d'environnement

Creez un fichier `.env` a la racine du projet:

```env
OPENAI_API_KEY=your_openai_api_key_here
GROQ_API_KEY=your_groq_api_key_here
```

## Execution

1. Ouvrir le notebook:
   - `TP1 SMA- Prompt Engineerin For Multi Agent Systems.ipynb`
2. Selectionner le kernel Python de `.venv`.
3. Executer les cellules dans l'ordre.

## Partie Ollama (local)

Si les cellules Ollama echouent, verifier:

1. Le service Ollama est lance.
2. Le modele est telecharge localement (exemple):

```powershell
ollama pull llama3.2
```

3. Le nom du modele correspond exactement a celui utilise dans le notebook (`llama3.2`).

## Evaluation des Prompts

Le notebook compare plusieurs strategies de prompting pour la classification binaire (`positive` / `negative`) avec:

- Verite terrain (gold labels).
- Metrique principale: `micro-F1`.
- Analyse de la variabilite des scores selon l'echantillonnage few-shot.

## Notes

- Le fichier `main.py` sert surtout de point d'entree minimal et n'implemente pas la logique du TP.
- La majorite du travail est dans le notebook.
