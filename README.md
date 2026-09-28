# Riya Mathew Kovoor — Data Science Portfolio

This repository contains my personal data science portfolio website, built using Quarto and published with GitHub Pages. It includes computational posts written in both Python and R.

## 1. Software Requirements

The following software must be installed before building the website:

- Git
- Quarto 1.10.18
- uv 0.12.9
- R 4.6.1
- Python 3.14

The versions listed above are the versions used to develop and test this project.

### 1.1 Install Git

Git is required to clone the repository.

Install Git from the official Git website:

https://git-scm.com/install/

After installing Git, open a terminal and verify that it is available:

```bash
git --version
```

The exact Git version may vary. Git only needs to be installed and available from the terminal.

### 1.2 Install Quarto

Quarto is required to render the website.

Install Quarto from the official Quarto website:

https://quarto.org/docs/get-started/

This project was developed and tested using Quarto 1.10.18.

Verify the installed version:

```bash
quarto --version
```

The version should be:

```text
1.10.18
```

### 1.3 Install uv

uv is used to create and restore the Python environment for this project.

Install uv using the official installation instructions:

https://docs.astral.sh/uv/getting-started/installation/

This project was developed and tested using uv 0.12.9.

Verify the installed version:

```bash
uv --version
```

The version should be:

```text
0.12.9
```

### 1.4 Install R

R is required to render the R computational post.

Install R from CRAN:

https://cran.r-project.org/

This project was developed and tested using R 4.6.1.

After installing R, open a terminal and start R:

```bash
R
```

At the R prompt, verify the R version:

```r
R.version.string
```

The version should indicate:

```text
R version 4.6.1
```

Exit R:

```r
q()
```

If R asks:

```text
Save workspace image? [y/n/c]:
```

enter:

```text
n
```

Python does not need to be installed separately. The project specifies Python 3.14 in `.python-version`, and uv creates and manages the project's Python environment.

The R project environment uses renv. renv does not need to be installed separately because the project is already configured to use renv, and the environment can be restored using the committed `renv.lock` file.

---

## 2. Clone the Repository

Once the required software has been installed, open a terminal.

Clone the repository using HTTPS:

```bash
git clone https://github.com/riyakovoor/riyakovoor.github.io.git
```

Move into the repository:

```bash
cd riyakovoor.github.io
```

All remaining commands should be run from the top-level directory of the repository unless otherwise stated.

You can verify that you are in the correct directory by running:

```bash
pwd
```

The path should end with:

```text
riyakovoor.github.io
```

You can also check the contents of the repository:

```bash
ls -la
```

The repository should contain files and directories including:

```text
_quarto.yml
pyproject.toml
uv.lock
.python-version
.Rprofile
renv.lock
renv/
posts/
docs/
```

The environment files are already included in the repository, so there is no need to create a new uv project or initialize a new renv project.

---

## 3. Set Up the Python Environment

The Python environment for this project has already been configured using:

- `pyproject.toml` — specifies the project and its Python dependencies
- `uv.lock` — records the resolved dependency versions
- `.python-version` — specifies Python 3.14

From the top-level directory of the repository, run:

```bash
uv sync
```

This creates the project's Python virtual environment and installs the required Python packages using the dependencies and versions recorded in the project files.

The Python environment is managed by uv.

You do not need to run:

```bash
uv init
```

or:

```bash
uv python pin 3.14
```

or:

```bash
uv add ...
```

because the Python environment has already been created and its configuration and lockfile are included in the repository.

The required Python packages will be restored by `uv sync`.

---

## 4. Set Up the R Environment

The R environment for this project has already been configured using:

- `renv.lock` — records the R package versions used by the project
- `.Rprofile` — configures the project to use renv
- `renv/activate.R` — activates the project environment
- `renv/` — contains the renv project configuration

Make sure you are still in the top-level directory of the repository before starting R.

Start an R session from the terminal:

```bash
R
```

At the R prompt (`>`), restore the project's R environment:

```r
renv::restore()
```

If renv asks for confirmation to install the required packages, enter:

```text
y
```

Wait for the package installation to finish.

The restore process installs the packages recorded in `renv.lock`.

After the restoration is complete, exit the R session:

```r
q()
```

When R asks:

```text
Save workspace image? [y/n/c]:
```

enter:

```text
n
```

You should then return to the normal terminal prompt.

You do not need to run:

```r
renv::init()
```

because this project has already been initialized with renv and the required project files are included in the repository.

---

## 5. Render the Website

After restoring both environments, make sure you are back in the top-level directory of the repository:

```text
riyakovoor.github.io
```

The website must be rendered from the top-level directory so that Quarto can correctly access the project's Python environment and the R project configuration.

Run:

```bash
uv run quarto render
```

This command renders the complete Quarto website.

It executes the Python and R code in the computational posts and generates the corresponding outputs, including figures and tables, during the rendering process.

The complete website is rendered, including:

- the Python computational post
- the R computational post
- the home page
- the about page
- the blog page

A successful render should finish without errors and create the built website in the `docs/` directory.

The main rendered page is:

```text
docs/index.html
```

---

## 6. Open the Rendered Website Locally

After `quarto render` has completed successfully, the rendered website will be located in the `docs/` directory.

The main page is:

```text
docs/index.html
```

### macOS

From the top-level directory of the repository, run:

```bash
open docs/index.html
```

This opens the locally rendered website in the default web browser.

### Windows

Open the `docs` folder in File Explorer and double-click:

```text
index.html
```

### Linux

From the top-level directory of the repository, run:

```bash
xdg-open docs/index.html
```

The locally opened website should display the rendered portfolio site, including its navigation, pages, and computational posts.

---

## 7. Data

The computational posts use the Palmer Penguins dataset provided through the `palmerpenguins` package.

The data source is:

Palmer Penguins, Palmer Station Antarctica LTER.

The dataset and information about it are available at:

https://allisonhorst.github.io/palmerpenguins/

The dataset is provided through the installed `palmerpenguins` package rather than being stored as a separate data file in this repository.

### Network requirements

Network access is required during the initial environment setup if the required packages are not already available locally.

Specifically:

- `uv sync` may require network access to download the required Python packages.
- `renv::restore()` may require network access to download the required R packages and dependencies.

Once both environments have been restored, the Quarto render uses the installed `palmerpenguins` package and does not need to download the Palmer Penguins dataset from an external URL.

---

## 8. Reproducibility Files

The repository contains the files needed to reproduce the Python and R environments used by the computational posts.

### Python environment

The Python environment is defined by:

```text
pyproject.toml
uv.lock
.python-version
```

### R environment

The R environment is defined by:

```text
renv.lock
.Rprofile
renv/activate.R
renv/
```

These files allow the project environments to be restored on another computer without manually determining which package versions are required.

The website should always be rendered from the top-level directory of the repository so that Quarto can correctly use the project's Python and R environments.

---

## 9. Complete Build Sequence

After installing the required software, the complete sequence from cloning the repository to rendering the website is shown below.

### Terminal

Run:

```bash
git clone https://github.com/riyakovoor/riyakovoor.github.io.git
cd riyakovoor.github.io
uv sync
R
```

### R

At the R prompt, run:

```r
renv::restore()
```

If prompted to install the packages, enter:

```text
y
```

After the restoration finishes, exit R:

```r
q()
```

When prompted:

```text
Save workspace image? [y/n/c]:
```

enter:

```text
n
```

### Terminal

Back at the terminal, make sure you are still in the top-level directory of the repository, then run:

```bash
uv run quarto render
```

After the render completes, the website will be available at:

```text
docs/index.html
```

On macOS, open it with:

```bash
open docs/index.html
```

The website should now be rendered and viewable locally.
