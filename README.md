# nlp-03-text-exploration

[![Python 3.14+](https://img.shields.io/badge/python-3.14%2B-blue?logo=python)](#)
[![MIT](https://img.shields.io/badge/license-see%20LICENSE-yellow.svg)](./LICENSE)

> Professional Python project for Web Mining and Applied NLP.

Web Mining and Applied NLP focus on retrieving, processing, and analyzing text from the web and other digital sources.
This course builds those capabilities through working projects.

In the age of generative AI, durable skills are grounded in real work:
setting up a professional environment,
reading and running code,
understanding the logic,
and pushing work to a shared repository.
Each project follows a similar structure based on professional Python projects.
These projects are **hands-on textbooks** for learning Web Mining and Applied NLP.

## This Project

This project focuses on **exploratory analysis of text data**.

The goal is to analyze a small, structured corpus and observe how
patterns emerge from token distributions, category comparisons,
and contextual relationships.

You will:

- tokenize and clean text data
- build frequency distributions
- compare token usage across categories
- examine co-occurrence (context windows)
- analyze bigrams (local structure)
- visualize results and interpret patterns

This project illustrates how **structure appears in text before any machine learning is applied**.
These patterns support later pipelines, embeddings, and retrieval.

You'll work with just these files as you update authorship and experiment:

- **notebooks/nlp_corpus_explore_case.ipynb** - notebook version
- **src/nlp/nlp_corpus_explore_case.py** - Python script
- **pyproject.toml** - project configuration and dependencies
- **zensical.toml** - project metadata

## First: Follow These Instructions

Follow the [step-by-step workflow guide](https://denisecase.github.io/pro-analytics-02/workflow-b-apply-example-project/) to complete:

1. Phase 1. **Start & Run**
2. Phase 2. **Change Authorship**
3. Phase 3. **Read & Understand**

## What to Look For

As you run the script and notebook, focus on:

- which tokens dominate each category
- how categories differ in vocabulary
- which words appear in similar contexts
- how local structure (bigrams) appears in text

These observations are the foundation for later modules.

## Success

After running the script successfully, you will see:

```shell
========================
Pipeline executed successfully!
========================
```

You will also see:

- frequency tables printed to the console
- visualizations of token distributions
- examples of co-occurrence and bigram patterns

A file named `project.log` will appear in the project folder.

## Command Reference

The commands below are used in the workflow guide above.
They are provided here for convenience.

Follow the guide for the **full instructions**.

<details>
<summary>Show command reference</summary>

### In a machine terminal (open in your `Repos` folder)

After you get a copy of this repo in your own GitHub account,
open a machine terminal in your `Repos` folder:

```shell
git clone https://github.com/sydsailors/nlp-03-text-exploration
cd nlp-03-text-exploration
code .
```

### In a VS Code terminal

```shell
uv self update
uv python pin 3.13
uv sync --extra dev --extra docs --upgrade

uvx pre-commit install
git add -A
uvx pre-commit run --all-files

# Later, we install spacy data model and
# en_core_web_sm = english, core, web, small
# It's big: spacy+data ~200+ MB w/ model installed
#           ~350–450 MB for .venv is normal for NLP
# uv run python -m spacy download en_core_web_sm

# First, run the module
# IMPORTANT: Close each figure after viewing so execution continues
uv run python -m nlp.nlp_corpus_explore_case

# Then, open the notebook.
# IMPORTANT: Select the kernel and Run All:
# notebooks/nlp_corpus_explore_case.ipynb

uv run ruff format .
uv run ruff check . --fix
uv run zensical build

git add -A
git commit -m "update"
git push -u origin main
```

</details>

## Notes

- Use the **UP ARROW** and **DOWN ARROW** in the terminal to scroll through past commands.
- Use `CTRL+f` to find (and replace) text within a file.

## Project Modifications

Changes made to this project to make it my own include:

**Phase 4: Make a Technical Modification**
- Added stopwords to clean the text.
- Updated the context window from 2 to 3.

**Phase 5: Apply the Skills to a New Problem**
- Created a new corpus with 9 documents that includes 3 categories: patient, hospital, and doctor.
- Included stopwords to clean the text.
- Used word cloud to give a quick sense of the most important or frequent bigrams.
- Observations:
  - Tokenization revealed what tokens dominate in each category:
    - Patient: "patient", "treatment", "after", "care", "follows"
    - Hospital: "hospital", "patients", "manages", "provides"
    - Doctor: "doctor", "patient", "reviews", "prescribes", "results"
  - Co-occurrence shows relationships between roles and actions
    - "patient" appears near "doctor", "hospital", "care", "mild", "treatment"
    - "hospital" occurs near "admits", "emergency", "provides"
    - "doctor" co-occurs with "examines", "prescribes", "medication", "reviews"
  - Bigrams help to identify common patterns in sentences and frequent action-object relationships

## Terminology

In preparation for large language models (LLM) and related methods,
our analysis does not begin with semantic interpretation.
Instead, we focus on **proximity** and observable **patterns** in the text.

We evaluate **co-occurrence (context windows)**, that is, _which words tend to appear near each other_.

The full collection of text is called a **corpus** (a set of documents).
For this analysis, each document is represented as a single line of text.

## Example Output

```text
Corpus contains 9 documents.
Tokenization complete.
shape: (10, 2)
┌──────────┬───────────┐
│ category ┆ token     │
│ ---      ┆ ---       │
│ str      ┆ str       │
╞══════════╪═══════════╡
│ patient  ┆ patient   │
│ patient  ┆ reports   │
│ patient  ┆ mild      │
│ patient  ┆ pain      │
│ patient  ┆ patient   │
│ patient  ┆ rests     │
│ patient  ┆ after     │
│ patient  ┆ treatment │
│ patient  ┆ patient   │
│ patient  ┆ follows   │
└──────────┴───────────┘
Top global tokens:
shape: (10, 2)
┌────────────┬─────┐
│ token      ┆ len │
│ ---        ┆ --- │
│ str        ┆ u32 │
╞════════════╪═════╡
│ patient    ┆ 5   │
│ hospital   ┆ 3   │
│ doctor     ┆ 3   │
│ care       ┆ 2   │
│ after      ┆ 1   │
│ prescribes ┆ 1   │
│ results    ┆ 1   │
│ mild       ┆ 1   │
│ examines   ┆ 1   │
│ rests      ┆ 1   │
└────────────┴─────┘
Top tokens by category:
shape: (12, 3)
┌──────────┬───────────┬─────┐
│ category ┆ token     ┆ len │
│ ---      ┆ ---       ┆ --- │
│ str      ┆ str       ┆ u32 │
╞══════════╪═══════════╪═════╡
│ patient  ┆ patient   ┆ 3   │
│ patient  ┆ treatment ┆ 1   │
│ patient  ┆ after     ┆ 1   │
│ patient  ┆ care      ┆ 1   │
│ patient  ┆ follows   ┆ 1   │
│ …        ┆ …         ┆ …   │
│ patient  ┆ reports   ┆ 1   │
│ patient  ┆ mild      ┆ 1   │
│ patient  ┆ pain      ┆ 1   │
│ hospital ┆ hospital  ┆ 3   │
│ hospital ┆ patients  ┆ 1   │
└──────────┴───────────┴─────┘
PATIENT top tokens: ['patient', 'treatment', 'after', 'care', 'follows']
HOSPITAL top tokens: ['hospital', 'patients', 'manages', 'provides', 'patient']
DOCTOR top tokens: ['doctor', 'patient', 'reviews', 'prescribes', 'results']

Context for 'patient':
['reports', 'mild', 'rests', 'after', 'follows', 'care', 'doctor', 'examines', 'hospital', 'manages']

Context for 'hospital':
['admits', 'new', 'provides', 'emergency', 'manages', 'patient']

Context for 'doctor':
['examines', 'patient', 'prescribes', 'medication', 'reviews', 'results']
Top bigrams:
shape: (10, 2)
┌────────────────────┬─────┐
│ bigram             ┆ len │
│ ---                ┆ --- │
│ str                ┆ u32 │
╞════════════════════╪═════╡
│ hospital provides  ┆ 1   │
│ reviews results    ┆ 1   │
│ hospital admits    ┆ 1   │
│ provides emergency ┆ 1   │
│ after treatment    ┆ 1   │
│ admits new         ┆ 1   │
│ doctor examines    ┆ 1   │
│ emergency care     ┆ 1   │
│ patient rests      ┆ 1   │
│ reports mild       ┆ 1   │
└────────────────────┴─────┘
```

## Text Categorization Analysis

- Which words appear **most often in each category**, and why?
- Which words tend to appear near **dog**, **cat**, or **truck**?
- What **differences** do you observe between animal-related and vehicle-related text?
- Which words seem **interchangeable** based on how they are used?
- What **patterns** help infer meaning from the data?

## General Insights

These categories are artificial and were chosen to illustrate the process.
Related approaches are used to prepare and analyze large text corpora for modern LLMs.

By examining token frequency, category differences, and co-occurrence
(which words appear near each other),
the **measurable structure of text** begins to appear.

Words used in similar contexts exhibit similar patterns,
and groups of related terms emerge naturally from the data.

Even before any modeling, we can begin to distinguish categories
and see how meaning is reflected through **patterns of use**.
