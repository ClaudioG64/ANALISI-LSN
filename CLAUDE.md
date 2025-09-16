# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains coursework for the **Numerical Simulation Laboratory (NSL)** course. It's organized as a series of lessons (Lezione01-12) covering various computational physics and Monte Carlo simulation topics.

## Repository Structure

The project follows a lesson-based organization:

```
ANALISI-LSN/
├── Lezione01/          # Random number generation, Central Limit Theorem
│   ├── 1.1/, 1.2/, 1.3/ # Individual exercises
│   └── LSN_Exercises_01.ipynb
├── Lezione02/          # Monte Carlo integration
├── Lezione03/          # Financial modeling (Black-Scholes option pricing)
├── Lezione04/          # Molecular Dynamics, Maxwell-Boltzmann distribution
├── Lezione05/          # Quantum mechanics (hydrogen atom wavefunctions)
├── Lezione06/          # MCMC methods (Metropolis, Gibbs sampling)
├── Lezione07/          # Monte Carlo vs Molecular Dynamics comparison
├── Lezione11/          # Advanced topics
└── Lezione12/          # Advanced topics
```

Each lesson directory contains:
- `LSN_Exercises_XX.ipynb` - Main exercise notebook with theoretical background
- Individual exercise subdirectories (e.g., `1.1/`, `1.2/`)
- Data files (`.dat` format) for analysis and plotting
- Analysis notebooks for specific topics

## Key Topics Covered

1. **Random Number Generation & Statistical Testing** (Lesson 1)
   - Pseudo-random number generator validation
   - Chi-square tests for uniformity
   - Central Limit Theorem demonstrations

2. **Monte Carlo Methods** (Lessons 2-3)
   - Integration techniques
   - Financial modeling (Black-Scholes option pricing)
   - Variance reduction methods

3. **Molecular Dynamics** (Lesson 4)
   - Lennard-Jones potential simulations
   - Maxwell-Boltzmann distribution verification
   - Equilibration and time-reversal studies

4. **Quantum Mechanics Simulations** (Lesson 5)
   - Hydrogen atom wavefunction sampling
   - Variational Monte Carlo methods

5. **Advanced MCMC** (Lesson 6)
   - Metropolis algorithm implementation
   - Gibbs sampling techniques

6. **Comparative Studies** (Lesson 7)
   - Monte Carlo vs Molecular Dynamics performance analysis

## Development Environment

**Requirements:**
- Python 3.x with Jupyter notebook support
- NumPy for numerical computations
- Matplotlib for plotting and visualization
- Standard scientific Python stack

**Note:** Python and Jupyter are not currently installed in this environment. To work with the notebooks, you'll need to:
```bash
# Install Python and required packages
pip install jupyter numpy matplotlib scipy
```

## Common Development Tasks

**Working with Notebooks:**
```bash
# Start Jupyter server
jupyter notebook

# Run specific notebook
jupyter nbconvert --execute LSN_Exercises_01.ipynb
```

**Data Analysis:**
- Most exercises generate `.dat` files with numerical results
- Use numpy.loadtxt() to read data files
- Results typically include block averages, progressive estimates, and statistical uncertainties

## Code Architecture & Patterns

**Statistical Uncertainty Estimation:**
All Monte Carlo calculations use the **blocking method** for error estimation:
- Divide M total samples into N blocks
- Calculate block averages and progressive uncertainties
- Standard pattern: `error(AV, AV2, n)` function for uncertainty calculation

**Common Computational Patterns:**
1. **Block averaging** - Standard across all exercises for uncertainty quantification
2. **Progressive estimation** - Running averages and errors as function of sample size  
3. **Histogram analysis** - For distribution comparisons and chi-square tests
4. **Equilibration monitoring** - For MD simulations and MCMC methods

**Data Output Format:**
- Text files with columnar data (space-separated)
- Headers indicating block number, estimates, and uncertainties
- Consistent naming: `output*.dat`, `*_mean.dat`, etc.

## Important Implementation Notes

- **Never use π to calculate π** - Use geometric methods for Buffon's needle experiment
- **Statistical validation is mandatory** - All MC results must include uncertainty estimates
- **Visualization requirements** - Each exercise requires specific plots showing convergence
- **Physical units** - MD simulations use Lennard-Jones reduced units (σ, ε, m basis)
- **Reproducibility** - Use fixed random seeds for consistent results: `np.random.seed(1)`

## Exercise Validation

Each exercise notebook includes specific validation requirements:
- Comparison with analytical results (e.g., Black-Scholes pricing)
- Convergence plots showing estimate ± uncertainty vs. sample size
- Chi-square tests for distribution validation
- Physical interpretation of simulation results