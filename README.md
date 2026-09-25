# Alice's website

This Quarto website contains personal posts and computational analyses using Python and R.
The bonus post uses Python to calculate average penguin body mass by species, then passes the result to R through reticulate to create a plot.

## Prerequisites

Install these tools before building. Versions used for this project:

- Quarto 1.10.18
- uv 0.12.7
- R 4.6.1
- Git

Python 3.14 is specified in `.python-version`; uv can install it.
The project's renv setup bootstraps renv automatically.

## Build from a fresh clone

Run these commands in a terminal, starting in a directory where you want to download the repository:

```bash
git clone https://github.com/alicezyj26/alicezyj26.github.io.git
cd alicezyj26.github.io
uv sync --locked
```

Start an R session with this repository as its working directory.
In the R Console, run:

```r
renv::restore(project = ".", prompt = FALSE)
```

Return to the terminal, still at the repository root, and run:

```bash
uv run quarto render
```

The generated website is saved in `docs/`.

To view the website locally, run from the same directory:

```bash
uv run quarto preview
```

Open the local URL printed in the terminal. Press Ctrl+C to stop the preview.

## Data

All three computational posts use
[Palmer Penguins](https://allisonhorst.github.io/palmerpenguins/).

The data comes with the Python and R `palmerpenguins` packages.
The posts do not download data from a remote URL during rendering.

An internet connection is needed for initial tool and package installation and environment restoration.

## Environments

Python dependencies are recorded in `pyproject.toml` and `uv.lock`.
The Python version is specified in `.python-version`.

R dependencies are recorded in `renv.lock`.
`.Rprofile` and `renv/activate.R` activate the project environment.

The bonus post runs R and Python together using knitr and reticulate.
Reticulate is included in renv.lock. Python runs in the project's .venv.

Run all build commands from the repository root.

