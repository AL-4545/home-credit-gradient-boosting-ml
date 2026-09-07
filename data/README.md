# Data

The raw data used in this project come from the Kaggle Home Credit Default Risk dataset and are not included in this repository.

To rerun the notebook locally, download the Kaggle dataset and place the required files in this folder. The main expected files are:

- `application_train.csv`
- `application_test.csv`
- `bureau.csv`
- `bureau_balance.csv`
- `previous_application.csv`
- `installments_payments.csv`

The final notebook may also expect locally generated aggregate files:

- `bureau_agg_v3.pkl`
- `previous_agg_v3.pkl`
- `installments_agg_v3.pkl`

These generated files are excluded from the public repository because they are derived from the raw data.