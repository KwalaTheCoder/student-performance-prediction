# Audit and refactor

Supports continuous-score regression by default and four-band classification with --task classification. Removes both Performance Index and Performance Index Cat from all predictors, fixing direct target leakage. Bands are low [0,25], fair (25,50], good (50,75], high (75,100]. Preserves all available legitimate study inputs; model selection never uses the final holdout.

Original algorithms and historical outputs remain in legacy/. No production dataset was available during refactoring; new real-data metrics remain unmeasured. See README.md for the reproducible evaluation protocol.
