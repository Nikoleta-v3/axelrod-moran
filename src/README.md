# Data generation scripts and libraries

This directory contains scripts and libraries for the generation of data.

## Players used in this work

```
$ python moran.py  # Lists the number of players used
172
```

Also contains a function `generate_players` which returns a list of `axelrod`
player instances.

## Theoretic results

The file `theoretic.py` contains a number of functions used for the calculation
of analytic results for Moran processes.

## Generate the cache.

```
$ python generate_cache.py
```

This generates two data files in `../data`:

- `outcomes.csv`
- `outcomes_noise.csv`

These files are of the format:

```csv
player1_name, player2_name, player1_score, player2_score, count
```

where `count` is the number of times that particular score pair occurs.

Also contains a function `read_csv` which reads in the file to give nested
dictionaries of match outcomes.

## Run the Moran processes

The file `moran.py` is used to generate data files for the Moran process.

```
$ python moran.py 4 2 ../data/outcomes.csv ../data/sims_4.csv
```

This will run the Moran process for all pairs of players in a population of size
4 and 2 players of the first type. A cached outcome of match results if read
from `../data/outcomes.csv` and the output is `..data/sims_4.csv`.