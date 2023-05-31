# Final Thesis Project
This GitHub repository contains the data and code I have used in my Final Thesis Project for the MSc in Applied Data Science (Utrecht University), titled "Using artificial neural networks to improve hydrological streamflow predictions from PCR-GLOBWB". The final version of the thesis can be found at https://studenttheses.uu.nl/handle/20.500.12932/42499.

To be able to run the code, the paths should be changed to your own when it says in the comments. The following folder structure, starting from the same level as the code, should be created for the code to work out-of-the-box:

```
└── output
└── temp
    ├── formatted_data
    │   ├── basel
    │   └── lobith
    └── predictions
        ├── basel
        │   ├── lag
        │   │   ├── fcn
        │   │   ├── mlr
        │   │   ├── pcr
        │   │   └── tcn
        │   └── no_lag
        │       ├── fcn
        │       ├── mlr
        │       └── pcr
        └── lobith
            └── (same structure as basel)
```

The data_formatting.ipynb should be the first script to be run, since it formats the data (located in the data folder of this repositoy) to be used later by the other files. There, one must choose the amount of time steps added as lagged variables, the train-test split fraction and the location of the data to be formatted.

PCR_MLR.ipynb takes the results from PCR-GLOBWB and makes the predictions using multiple linear regression in the given location, with or without lag. The number of runs should equal the amount of possible train-test splits (5 by default, for a 80% train split).

FCNN.ipynb and TCNN.ipynb make the predictions for their respective models, for a user-defined number of runs, on different test sets or not, for the specified location and either whether using lagged variables or not (FCNN) or for the given time window (TCNN).

Finally, analysis_and_visualization.ipynb can be run to obtain all the figures showcased in the thesis, as well as some analysis of the results.
