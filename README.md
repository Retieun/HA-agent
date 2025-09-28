
# HA-Agent: Homological Algebra Assistant

A deployable proof-sketching and reasoning assistant for homological algebra, powered by Retrieval-Augmented Generation (RAG), open-source LLMs, and optional computational tools (Macaulay2, Sage). Built as a learning-first GitHub project.

---

## Features
- Retrieval-Augmented Generation over license-compliant notes, lectures, or public resources.
- Proof sketch generation with citations to sources.
- Optional tool integration: Macaulay2 / Sage.
- Minimal Streamlit UI for queries and references.
- Dockerized deployment and GitHub Actions CI/CD.
- (Optional) LoRA fine-tuning on custom datasets.

---

## Quickstart

### 1. Clone Repository
```bash
git clone https://github.com/<your-username>/ha-agent.git
cd ha-agent
```

### 2. Install Dependencies
Using [uv](https://github.com/astral-sh/uv):
```bash
uv sync
```

Or with Poetry:
```bash
poetry install
```

### 3. Prepare Corpus
Place your **license-compliant** materials (notes, slides, open-access texts) into:
```
data/corpus/
```

### 4. Build Index
```bash
uv run python scripts/build_index.py --src data/corpus --out data/index
```

### 5. Run API Server
```bash
uv run uvicorn src.ha_agent.server:app --reload
```
Access the API at: [http://localhost:8000/docs](http://localhost:8000/docs)

### 6. (Optional) Run Streamlit UI
```bash
uv run streamlit run src/ha_agent/ui/app.py
```

---

## Project Structure
```
ha-agent/
  README.md
  LICENSE
  pyproject.toml
  src/
    ha_agent/
      server.py
      rag/
      reasoning/
      tools/
      eval/
  data/
    corpus/
    index/
  scripts/
  docker/
  .github/workflows/
```

---

## Roadmap
- **Phase 0 (Week 1):** Setup GitHub repo, CI/CD, linting, testing.
- **Phase 1 (Weeks 2–3):** MVP: RAG + proof sketching.
- **Phase 2 (Weeks 4–6):** Add reasoning planner + optional Macaulay2/Sage tools.
- **Phase 3 (Weeks 7–8):** Build evaluation dataset + metrics.
- **Phase 4 (Weeks 9–10):** Streamlit frontend.
- **Phase 5 (Weeks 11–12):** Dockerize + deploy to Render/Fly.io/Railway.
- **Phase 6 (Weeks 13–16, optional):** Fine-tuning with LoRA.

---

## Contributing
1. Fork the repo and create a new branch.
2. Run `pre-commit install` to set up linting hooks.
3. Submit pull requests with clear commit messages.

---

## License
MIT License (see `LICENSE`).

---

## Disclaimer
This project is for research and educational purposes. Do **not** include copyrighted textbooks or restricted material in the corpus or training data.
