# AgentsForQA

Learning notebooks for using LangChain agents and models in QA workflows: prompt
chains, PDF-based retrieval, log summaries, and BDD test-case generation.

## Requirements

- Python 3.12 (the environment used for this project)
- A Google Gemini API key for `BddTestCaseCreatorWithRequirements.ipynb`
- Ollama installed and running for notebooks that use `ChatOllama` or
  `OllamaEmbeddings`
- Chromium for the Playwright browser-automation examples

## Setup

From the repository root, create and activate a virtual environment:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m playwright install chromium
```

On Windows, activate the environment with `.venv\Scripts\activate`.

Start Jupyter from the repository root:

```bash
jupyter lab
```

The notebooks refer to files using relative paths, so use the working directory
indicated below:

| Notebook | Working directory | Additional setup |
| --- | --- | --- |
| `Langchain_basics.ipynb` | Repository root | Ollama server and the models named in the notebook |
| `Section7_LogReaderAgent/LogReader.ipynb` | `Section7_LogReaderAgent/` | Ollama server and the models named in the notebook |
| `Section8_BddTestCaseAgent/BddTestCaseCreator.ipynb` | `Section8_BddTestCaseAgent/` | Ollama server and the models named in the notebook |
| `Section8_BddTestCaseAgent/BddTestCaseCreatorWithRequirements.ipynb` | `Section8_BddTestCaseAgent/` | `GOOGLE_API_KEY` or `GEMINI_API_KEY` in the repository-root `.env` file |

For Google Gemini, create a `.env` file at the repository root:

```dotenv
GOOGLE_API_KEY=your_api_key
```

Do not commit `.env`; `.env.example` may be committed with placeholder values.
If an Ollama model named in a notebook is not available in your Ollama
installation, pull that model or change the notebook's model name to one you
have installed.

## Included sample data

The `Docs/` directories contain sample PDFs used by the document and BDD
notebooks. The log-reader notebook reads files from
`Section7_LogReaderAgent/logs/`. Chroma vector databases under `qa_db/` are
generated locally and are ignored by Git.

## Notes

These are educational notebooks, not a packaged application. Run notebook cells
in order. Model availability, external APIs, and platform-specific PDF/browser
dependencies can affect whether an example runs in a particular environment.
