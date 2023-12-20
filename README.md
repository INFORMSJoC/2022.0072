[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# Identifying Socially Optimal Equilibria using Combinatorial Properties of Nash Equilibria in Bimatrix Games

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository are a snapshot of the software and data
that were used in the research reported on in the [paper](https://doi.org/10.1287/ijoc.2022.0072) by Amin Dehghanian, Yujia Xie, and Nicoleta Serban.
The snapshot is based on 
[this SHA](https://github.com/yujiaxie000/GameTheory/commit/6db33484782012d837cc731d8c3c00616bcf6d9a) 
in the development repository. 

**Important: This code is being developed on an on-going basis at 
https://github.com/yujiaxie000/GameTheory. Please go there if you would like to
get a more recent version or would like support**

## Cite

To cite the contents of this repository, please cite both the paper and this repo, using their respective DOIs.

https://doi.org/10.1287/ijoc.2022.0072

https://doi.org/10.1287/ijoc.2022.0072.cd

Below is the BibTex for citing this snapshot of the respoitory.

```
@article{Dehghanian2023,
  author =        {Dehghanian, Amin and Xie, Yujia and Serban, Nicoleta},
  publisher =     {INFORMS Journal on Computing},
  title =         {{Identifying Socially Optimal Equilibria using Combinatorial Properties of Nash Equilibria in Bimatrix Games}},
  year =          {2023},
  doi =           {10.1287/ijoc.2022.0072.cd},
  url =           {https://github.com/INFORMSJoC/2022.0072},
}  
```

## Description

The goal of this software is to demonstrate different algorithms for identifying socially optimal Nash equilibria in bimatrix games.

This repository is made of the following directories and subdirectories

1. `src`: python implementations of different solver algorithms as well as other necessary utility scripts
2. `results`: figures and tables reported in the paper
3. `data`: instances used to generate results in the paper

## Building
### Requirements
1. Python 3.7+
2. Gambit and Gambit Python Extension: https://gambitproject.readthedocs.io/en/latest/index.html
3. CPLEX in Python
4. numpy, itertools

### Solver Remarks
We implemented our novel solver based on our proposed algorithms in `src/Solver_EnhancedHeuristic.py` (with warm-start solution) and `src/Solver_EnhancedNoHeuristic.py` (without warm-start solution). We additionally implemented various other solvers based on literature for comparison, including `src/Solver_GambitLemkeHowson.py` (solved by enumerating Lemke-Howson algorithm using Gambit), `src/Solver_Benders.py` (solved based on Benders decomposition), and `src/Solver_MIP.py` (solved based on MIP formulation).

The parameters used for all solvers include
1. `xAction`: number of actions for player 1
2. `yAction`: number of actions for player 2
3. `xMin`: minimum utility for player 1
4. `yMin`: minimum utility for player 2
5. `xMaX`: maximum utility for player 1
6. `yMaX`: maximum utility for player 2
7. `create`: create new instances or not (1: create; 0: no create)
8. `total`: total number of new instances creating
9. `timelimit`: time limit for the solver
10. `threadsNum`: number of threads for CPLEX solvers

Parameter specifically used in `src/Solver_EnhancedHeuristic.py` and `src/Solver_EnhancedNoHeuristic.py` 
1. `masterResult`: output filename for enhanced solver result

Parameter specifically used in `src/Solver_GambitLemkeHowson.py`
1. `insNum`: instance index to run specific instances (separated using comma)

Parameter specifically used in `src/Solver_Benders.py`
1. `bendersResult`: output filename for benders result

Parameter specifically used in `src/Solver_MIP.py`
1. `mipResult`: output filename for MIP result

## Results
### Instance Mapping
In `data`, we include six sets of generated instances with `(xAction, yAction) = (100, 100), (105, 105), (110, 110), (120, 120), (125, 125), (130, 130)` that we used to prepare our tabular results in `Table 2` and `Table 3`. All instances were initiated with `xMin=yMin=100` and `xMax=yMax=200`

The mapping between instances in `data` and the that in the table is illustrated below. `Name` and `# of action` corresponds to `Name` and `# of action` in computational results in `Table 2` and `Table 3`.  `Instance Name` corresponds to the name of instances in the `data` folder.

| Name | Instance Name | # of action || Name | Instance Name | # of action |
|------|---------------|-------------|-----|------|---------------|-------------|
| a1   | ins4          | 100         || b1   | ins1          | 120         |
| a2   | ins3          | 100         || b2   | ins6          | 120         |
| a3   | ins2          | 100         || b3   | ins8          | 120         |
| a4   | ins5          | 100         || b4   | ins9          | 120         |
| a5   | ins8          | 100         || b5   | ins7          | 120         |
| a6   | ins6          | 100         || b6   | ins0          | 120         |
| a7   | ins1          | 100         || b7   | ins3          | 120         |
| a8   | ins0          | 100         || b8   | ins4          | 120         |
| a9   | ins7          | 100         || b9   | ins5          | 120         |
| a10  | ins9          | 100         || b10  | ins2          | 120         |
| a11  | ins3          | 105         || b11  | ins4          | 125         |
| a12  | ins4          | 105         || b12  | ins3          | 125         |
| a13  | ins5          | 105         || b13  | ins2          | 125         |
| a14  | ins2          | 105         || b14  | ins5          | 125         |
| a15  | ins8          | 105         || b15  | ins6          | 125         |
| a16  | ins1          | 105         || b16  | ins1          | 125         |
| a17  | ins6          | 105         || b17  | ins8          | 125         |
| a18  | ins7          | 105         || b18  | ins9          | 125         |
| a19  | ins0          | 105         || b19  | ins0          | 125         |
| a20  | ins9          | 105         || b20  | ins7          | 125         |
| a21  | ins9          | 110         || b21  | ins4          | 130         |
| a22  | ins0          | 110         || b22  | ins3          | 130         |
| a23  | ins7          | 110         || b23  | ins2          | 130         |
| a24  | ins6          | 110         || b24  | ins5          | 130         |
| a25  | ins1          | 110         || b25  | ins8          | 130         |
| a26  | ins8          | 110         || b26  | ins6          | 130         |
| a27  | ins2          | 110         || b27  | ins1          | 130         |
| a28  | ins5          | 110         || b28  | ins0          | 130         |
| a29  | ins4          | 110         || b29  | ins7          | 130         |
| a30  | ins3          | 110         || b30  | ins9          | 130         |

## Replicating

`Table 2` and `Table 3` in the paper compare and contrast different statistics collected from running `src/Solver_EnhancedHeuristic.py`, `src/Solver_EnhancedNoHeuristic.py`, `src/Solver_Benders.py`, and `src/Solver_MIP.py` against all instances presented in `data`. For example, to run all existing `10` instances located in `data/100-100/100-200-100-200` using `src/Solver_EnhancedHeuristic.py` with maximum running time cutoff at `21600` seconds and results output to `results/enhancedHeuristicResult.csv`:

```python
python Solver_EnhancedHeuristic.py --xAction=100 --yAction=100 --xMin=100.0 --xMax=200.0 --yMin=100.0 --yMax=20    0.0 --create=0 --total=10 --threadsNum=1 --timelimit=21600.0 --masterResult=enhancedHeuristicResult.csv
```

Replace `Solver_EnhancedHeuristic.py` with other solver scripts in `src` as well as other input parameters to produce the remaining outputs.

## Ongoing Development

This code is being developed on an on-going basis at the author's
[Github site](https://github.com/yujiaxie000/GameTheory).

## Support

For support in using this software, submit an
[issue](https://github.com/INFORMSJoC/2022.0072/issues/new).
