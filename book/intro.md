# Web Scraping with Python

This site is a collection of materials for a workshop on web scraping with Python. It's intended to be used during the workshop, and for participants to reference after the fact. Even if you're not attending this workshop, you might find it valuable to go through the code examples on your own, just know that that's not the primary purpose of the materials.

## Getting set up

The materials here require Python 3.8+, as well as a number of libraries. There are a few different ways to make sure that you have all of the dependencies set up. For any of them, it's best if you download or clone the [repository for this site](https://github.com/jaguillette/python-web-scraping-workshop). All of the files for the contents of the workshop are in the `book` directory of the repository, but downloading the repository will also give you the setup information outside of that repository.

### Option 1: Poetry

I'm using poetry to manage my environment for this workshop, to make sure that I have an accurate list of what libraries are required for you to run my code. If you want to do the same, you can [install poetry](https://python-poetry.org/docs/), then run `poetry install` in your terminal the directory where you saved this repository. That will create a virtual environment that matches mine.

You still need to activate the environment after creating it. There are [a few options for activating your environment](https://python-poetry.org/docs/basic-usage/#using-your-virtual-environment), but I prefer running this line of code:

    source `poetry env info --path`/bin/activate

If you're on Windows, `poetry shell` might be the best option, although I find that the best way to use Python in Windows is to use the [Windows subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/about). That isn't required for this workshop by any means, but it's worth checking out if you're using Windows and tired of it being weird for coding.

### Option 2: pip

If you're more comfortable with pip, or just don't want to get set up with `poetry`, I've included a `requirements.txt` as well. Running `pip install -r requirements.txt` in the directory where you saved the workshop materials should also get your dependencies set up.

### Option 3: Manual install

If you don't want to do any of that, here's just a list of the libraries to install, that you can do with as you please. This is the method that's most likely to run into version conflicts, but as long as your Python version is more recent than 3.8, you should be okay. Hopefully.

    requests
    beautifulsoup4
    jupyterlab
    pandas
    selenium

### Selenium

The last part of the workshop uses the `selenium` library, and is set up to use Firefox's `geckodriver` to make a Python-controlled browser. In order to make that work, you'll need to [install Firefox](https://www.mozilla.org/en-US/firefox/new/) if you don't already have it, and then set up [geckodriver](https://github.com/mozilla/geckodriver/).

To set up geckodriver, you'll need to download and decompress the appropriate version for your OS from the [geckodriver releases page](https://github.com/mozilla/geckodriver/releases). That will give you a `geckodriver` file, which needs to be in a location on your `PATH`. A simple way to do this is to run `printenv PATH` on Mac/Linux or `PATH` in a Windows terminal. That will give you a list of locations already on your `PATH`, so you can just move your `geckodriver` file to one of them. My `geckodriver` file is located at `/usr/local/bin/`, for reference.

### M1 ARM Architecture / Mac OS Catalina

M1 Macs still have some issues with Python. If you run into issues with the Jupyter kernel around `psutil`, such as `import psutil - mach-o file, but is an incompatible architecture (have 'x86_64', need 'arm64e'` or similar, this is due to the `psutil` wheels not being compatible with ARM, which is the architecture the newer Mac M1 processors use. You can confirm this is the issue by running the python CLI and importing `psutil`, which will fail: `python3`, `import psutil`. Hopefully [this PR fix](https://github.com/giampaolo/psutil/issues/1954) will be merged for `psutil` soon. Until then, you can fix this issue by uninstalling and reinstalling `psutil`, and building from scratch instead:
- `poetry shell`
- `pip3 uninstall psutil`
- `pip install --no-binary :all: psutil`
Now try `poetry run jupyter lab` and navigating to a notebook file - hopefully your kernel will not crash.

Mac users may also need to overcome a security issue with `geckodriver`. After adding `geckodriver` to your path, right click the executable and choose "Open". This will open a security dialog which allows you to trust `geckodriver` manually. If you don't do this, you may not be able to use it in your notebook as that trust dialog will not appear when `geckodriver` is first called by a script.

## Using these materials

With the repository downloaded, you'll find all of the files used in the workshop in the `book` directory, which is also what powers this site. You don't need to run anything for the first section on the Chrome Scraper extension, but starting with the section on `requests`, you'll want to run the corresponding Python notebook on your own system. They are numbered in the order that we'll use them in the workshop.

```{tableofcontents}
```
