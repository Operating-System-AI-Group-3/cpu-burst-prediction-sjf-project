# cpu-burst-prediction-sjf-project

```text
cpu-burst-prediction-sjf/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── __init__.py                  # + needed so imports work from tests and main.py
│   ├── data/
│   │   ├── __init__.py
│   │   ├── generate_workload.py     # + synthetic arrivals/bursts, seeded, predictability knob
│   │   ├── extract.py
│   │   └── preprocess.py            # unit conversion, dedupe, missing values, history features
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   ├── base.py                  # + fit(train) / predict(history) contract
│   │   ├── exponential_averaging.py
│   │   ├── linear_regression.py
│   │   └── random_forest.py
│   │
│   ├── scheduling/
│   │   ├── __init__.py
│   │   ├── process.py               # + Process record (arrival, true_burst, history)
│   │   ├── simulator.py             # + the single event loop, context-switch counting
│   │   ├── fcfs.py                  # policies only
│   │   ├── round_robin.py
│   │   └── sjf.py                   # ideal + predicted: key = true burst or injected predictor
│   │
│   └── evaluation/
│       ├── __init__.py
│       ├── metrics.py               # waiting, turnaround, MAE, long-wait tail, ordering inversions
│       └── overhead.py              # + prediction timing, CPU/memory, charges time to sim clock
│
├── configs/
│   └── experiment.yaml              # + seeds, n_trials=10, quantum, alpha, train/test split
│
├── tests/
│   ├── test_schedulers.py           # hand-computed cases from your guide (8/3/5 ms)
│   ├── test_no_leakage.py           # predictor never sees the burst it predicts
│   └── test_determinism.py          # same seed, identical output
│
├── results/
│   ├── tables/                      # + aggregated mean ± std
│   └── figures/
│
├── docs/                            # + proposal PDF, course template, notes
├── main.py                          # thin entry point: load config, run grid, write results
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```
