[![Build Status](https://travis-ci.org/ladybug-tools/uwg.svg?branch=master)](https://travis-ci.org/ladybug-tools/uwg)
[![Coverage Status](https://coveralls.io/repos/github/ladybug-tools/uwg/badge.svg?branch=master)](https://coveralls.io/github/ladybug-tools/uwg)

[![Python 2.7](https://img.shields.io/badge/python-2.7-green.svg)](https://www.python.org/downloads/release/python-270/) [![Python 3.6](https://img.shields.io/badge/python-3.6-blue.svg)](https://www.python.org/downloads/release/python-360/)

# uwg

The Urban Weather Generator (uwg) is a Python application for modeling the [urban heat island effect](https://en.wikipedia.org/wiki/Urban_heat_island). Specifically, it morphs rural [EnergyPlus weather (.epw) files](http://www.ladybug.tools/epwmap/) to reflect average conditions within the urban canyon using a range of properties including:

* Building geometry (including building height, ground coverage, window:wall area, and facade:site area)
* Building use (including program type, HVAC systems, and occupancy/equipment scheduling)
* Cooling system heat rejection to the outdoors (for Summer)
* Indoor heat leakage to the outdoors (for Winter)
* Urban materials (including the thermal mass, albedo and emissivity of roads, walls, and roofs)
* Anthropogenic heat from traffic (including traffic schedules)
* Vegetation coverage (both trees and shrubs)
* Atmospheric heat transfer from urban boundary and canopy layers

The [original Urban Weather Generator](http://urbanmicroclimate.scripts.mit.edu/uwg.php) was developed by Bruno Bueno for [his PhD thesis at MIT](https://dspace.mit.edu/handle/1721.1/59107).  Since this time, it has been validated 3 times and has been [enhanced by Aiko Nakano](https://dspace.mit.edu/handle/1721.1/108779).  In 2016, Joseph Yang also [improved the engine and added a range of building templates](https://dspace.mit.edu/handle/1721.1/107347).

This repository is a Python translation of the original [MATLAB Urban Weather Generator](https://github.com/hansukyang/UWG_Matlab).

# Example
Here is a Python example that shows how to create and run an Urban Weather Generator object. The example script is available [at resources/uwg_example.py](https://github.com/ladybug-tools/uwg/blob/master/resources/uwg_example.py). Run it through your command prompt in the main uwg directory with the following: ```python -m resources.uwg_example```

```python
from uwg import uwg

# Define the .epw, .uwg filenames to create an uwg object.
# uwg will look for the .epw file in the uwg/resources/epw folder,
# and the .uwg file in the uwg/resources/parameters folder.
epw_filename = "SGP_Singapore.486980_IWEC.epw"      # .epw file name
param_filename = "initialize_singapore.uwg"         # .uwg file name

# Initialize the UWG object and run the simulation
uwg_ = uwg(epw_filename, param_filename)
uwg_.run()
```

## Installation
```console
pip install uwg
```

## QuickStart
```python
import uwg

```

## [API Documentation](http://ladybug-tools.github.io/uwg/docs)

## Local Development
1. Clone this repo locally
```console
git clone git@github.com:ladybug-tools/uwg

# or

git clone https://github.com/ladybug-tools/uwg
```
2. Install dependencies:
```console
cd uwg
pip install -r dev-requirements.txt
pip install -r requirements.txt
```

3. Run Tests:
```console
python -m pytest tests/
```

4. Generate Documentation:
```console
sphinx-apidoc -f -e -d 4 -o ./docs ./uwg
sphinx-build -b html ./docs ./docs/_build/docs
```
