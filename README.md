# fluto

Metabolic network completion with respect to topological and linear reaction rate constraints based on the stoichiometry.

Tested with Python 3.7.6.

So far only level 2 [SBML](http://sbml.org/Documents/Specifications) files are supported.

## Installation and requirements

A good practice is to perform the Python installations into a [virtualenv](https://virtualenv.pypa.io/en/stable/installation/) or a [conda environment](https://conda.io/docs/user-guide/tasks/manage-environments.html)

Create a conda environment for fluto from the `environment.yml`.

- `conda env create -f environment.yml`

Activate conda environment.

- `conda activate fluto`

### PyASP

- `pip install  pyasp`

### ClingoLP

- `conda install -c sthiele -c potassco -c conda-forge clingolp`

### Cplex

IBM provides a promotional version sufficient to solve the toy example.

- `conda install -c ibmdecisionoptimization cplex`

For the full version follow the [IBM installation procedure](https://www.ibm.com/support/knowledgecenter/SSSA5P_12.10.0/ilog.odms.cplex.help/CPLEX/GettingStarted/topics/set_up/Python_setup.html). e.g.

- `cd /Applications/CPLEX_Studio128/cplex/python/3.6/x86-64_osx/`
- `python setup.py install`

## Usage

```text
$ python fluto.py -h
usage: fluto.py [-h] -m MODEL [-r REPAIRBASE] [-s SEEDS] [-e]
Performs hybrid (topological/flux) gap-filling
optional arguments:
-h, --help            show this help message and exit
-m MODEL, --model MODEL
                    organism metabolic model in SBML format
-r REPAIRBASE, --repairbase REPAIRBASE
                    database of reactions for gap-filling
-s SEEDS, --seeds SEEDS
                    topological seeds to unblock circular dependencies in
                    the graph. Txt file with one seed ID per line
-e, --export          enabling export of compounds to prevent metabolite
                    accumulation
requires Python clingoLP, PyASP and Cplex packages. See README and INSTALL
```

### Example

`python fluto.py -m data/toy/draft.xml -s data/toy/toposeeds.txt -r data/toy/repairdb.xml`

## Publication

- [Hybrid metabolic network completion, Frioux, C., Schaub, T., Schellhorn, S., Siegel, A., Wanko, P. (2019),  TPLP, 19(1), 83–108](https://www.cs.uni-potsdam.de/wv/publications/DBLP_journals/tplp/FriouxSSSW19.pdf)
