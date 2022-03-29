# Python Web Scraping Workshop materials

These are the materials for a workshop on web scraping with python that I'm developing. I'm trying some new tooling in `poetry` and `jupyter-book`, so if you're reading this, you're looking at a work in progress.

## Developing

The dependencies of this repo are managed by `poetry`. To use poetry to manage the dependencies, install it on your system, then run `poetry install` to set up the dependencies, then use this command to set up a shell that uses the new environment:

    source`poetry env info --path`/bin/activate

The dependencies are also articulated in `pyproject.toml`, so that can be used as a reference for installation. Maybe there's a way to use those dependencies with `pip` or `conda`, which people who aren't as deep into Python are more likely to have, but I don't know yet.

There are two steps to building the materials: building and deploying to the `gh-pages` branch with `ghp-import`
- To build, run `jupyter-book build book` (book refers to the folder in this root dir)
- To deploy, run `ghp-import -n -p -f -m "<commit message>" book/_build/html`
    - The commit message is optional, but helpful