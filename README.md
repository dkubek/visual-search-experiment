# Visual Search Experiment

View the render of the report here:
https://dkubek.github.io/visual-search-experiment/


## Setup

Firstly, you need to have [poetry](https://python-poetry.org/docs/) installed.
```sh
curl -sSL https://install.python-poetry.org | python3 -
```

Then setup the environment by running
```sh
poetry install
```

Finally, enter the environment with
```sh
poetry shell
```

## Getting data

Install ``dvc`` with ssh support (the ``dev`` group in the poetry environment
already lists it as a dependency).

Run this command if password login is mandatory.
```sh
dvc remote modify <myremote> ask_password true
```

## Generating report

Firstly, install [Quarto](https://quarto.org/docs/get-started/index.html) and
enter the poetry environment with all dependencies installed (``publish`` group
is sufficient).

To generate an html report run
```sh
quarto render visual_search_experiment.qmd --to html
```

To generate a pdf run
```sh
quarto render visual_search_experiment.qmd --to pdf
```

The output of these commands will be stored in ``output/``.

## Publishing to github pages

Enter the ``poetry`` environment.

Locally run
```sh
quarto publish gh-pages
```
this will render the report and push the output to branch ``gh-pages``.

**NOTE**: If you specify more then one format (pdf + html) in the ``.qmd``
*document and set custom output directory, the publish command will fail to
generate the pdf document. Either disable the custom out directory or disable
one the generation of the pdf.

