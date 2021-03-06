# Data generation scripts and libraries

This directory contains scripts and libraries for the generation of data.

## Players used in this work

```
$ python players.py  # Lists the number of players for which data was generated
175
```

Also contains a function `generate_players` which returns a list of `axelrod`
player instances.

## Abbreviations

The `abbreviations.py` file contains a dictionary with some abbreviations for
player names.

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
$ python moran.py 4 2 ../data/outcomes.csv ../data/sims_n_over_2/ sims_4.csv
```

This will run the Moran process for all pairs of players in a population of size
4 and 2 players of the first type. A cached outcome of match results if read
from `../data/outcomes.csv` and the output is `..data/sims_4.csv`.

## Preprocessing of the raw data

The file `clean_raw_moran.py` is used to clean all the data generated from
`moran.py`. Creates one data file `..data/sims_summary.csv` of the form:

```
Noise, P1, P2, N, repetitions, P1_fixation, P2_fixation
```

The file `preproces.py` is used to write the fixation probabilities and
relative fitness for each strategy pair to `..data/main.csv`:

```
player, opponent, N, noise, p_1, p_{N/2}, p_{N-1}
```

Where:

- `p_1`: is relative fitness of 1 player with N - 1 opponents
- `p_{N/2}`: is relative fitness of N/2 players with N/2 opponents
- `p_{N-1}`: is relative fitness of N-1 players with 1 opponent.

**This is automatically re written when running `clean_raw_moran.py`**.

`main.csv` is the main file used for all the analysis.
