# FraudShield — Explainable Fraud Detection

FraudShield is a machine-learning project that identifies potentially fraudulent financial transactions and helps users inspect model predictions. The application supports transaction-data upload, model training, evaluation, individual predictions, error analysis, and exporting results through an interactive Gradio interface.

> **Disclaimer:** This is an educational/demo project. Predictions are estimates, not proof of fraud. Do not use the model as the sole basis for real financial decisions.

## Features

- Upload transaction data from a CSV file.
- Try the application with a sample dataset.
- Train classification models such as Logistic Regression, Random Forest, and XGBoost (depending on the options enabled in your notebook).
- Evaluate models using accuracy, precision, recall, F1-score, a classification report, and a confusion matrix.
- Adjust the fraud decision threshold.
- Inspect feature importance.
- Review false positives and false negatives.
- Predict whether an individual transaction may be fraudulent.
- Export prediction results as a CSV file.

## Technology Stack

- Python
- pandas and NumPy
- scikit-learn
- Gradio
- XGBoost (if enabled)
- Google Colab / Jupyter Notebook

## Suggested Repository Structure

```text
FraudShield/
├── FraudShield.ipynb
├── data/
│   └── transactions.csv
├── README.md
└── requirements.txt
```

The `data/` folder is optional if you upload a CSV through the interface or load data from Google Drive.

## Getting Started

### Run in Google Colab

1. Upload `FraudShield.ipynb` to Google Colab, or open it from your GitHub repository.
2. Run the notebook cells in order. If your code is in one cell, run that cell.
3. Install any dependencies requested by the notebook.
4. Upload a transaction CSV or choose the sample dataset.
5. Select a model and train it.
6. Review the evaluation metrics and confusion matrix.
7. Adjust the threshold, test individual transactions, and export predictions as needed.

### Run locally

Use a Python version supported by the packages.

1. Clone your repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/FraudShield.git
   cd FraudShield
   ```

2. Create and activate a virtual environment (recommended).

   **Windows**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```

   **macOS/Linux**
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install the main dependencies:

   ```bash
   pip install pandas numpy scikit-learn gradio xgboost
   ```

4. Launch Jupyter:

   ```bash
   pip install notebook
   jupyter notebook
   ```

Open the notebook and run its cells. The exact dependencies may vary depending on which optional features are enabled.

## Dataset

The example dataset uses a target column named `Class`:

- `0` = legitimate transaction
- `1` = fraudulent transaction

The enhanced sample dataset may contain columns such as:

| Column | Description |
|---|---|
| `TransactionID` | Transaction identifier |
| `TransactionDateTime` | Transaction date and time |
| `Amount` | Transaction amount |
| `Hour` | Hour of the transaction |
| `DistanceFromUsualKM` | Distance from the usual location |
| `FailedAttempts24h` | Failed attempts in the previous 24 hours |
| `AccountAgeDays` | Account age in days |
| `Channel` | Transaction channel |
| `MerchantCategory` | Merchant category |
| `TransactionType` | Transaction type |
| `DeviceType` | Device used |
| `Country` | Transaction country |
| `IsInternational` | Whether the transaction is international |
| `CardPresent` | Whether the card was present |
| `TransactionsLast24h` | Number of recent transactions |
| `AverageSpend30d` | Average spending over 30 days |
| `AmountToAverageSpendRatio` | Transaction amount relative to average spending |
| `PreviousChargebacks` | Previous chargeback count |
| `Class` | Target label: fraud (`1`) or legitimate (`0`) |

Your CSV must contain the target column expected by the notebook. If your dataset uses a different target-column name, update the relevant setting in the code.

### Data preparation tips

- Check missing values, duplicates, invalid amounts, and inconsistent labels.
- Exclude identifiers such as transaction IDs from model features when they do not provide meaningful predictive information.
- Avoid features that would only be known after a transaction has been investigated.
- Consider a time-based train/test split when evaluating future transaction performance.
- Fraud datasets are often imbalanced, so do not rely on accuracy alone.

## How It Works

1. **Load data:** Upload a CSV or select the sample dataset.
2. **Prepare features:** Clean data and process categorical and numerical columns.
3. **Split data:** Separate training and testing records.
4. **Train:** Fit the selected classification model.
5. **Evaluate:** Compare predictions with the test labels.
6. **Explain and inspect:** Review feature importance and prediction errors.
7. **Predict and export:** Score transactions and save the results.

## Evaluation Metrics

- **Precision:** Among transactions flagged as fraud, the fraction that are actually fraud.
- **Recall:** Among all fraudulent transactions, the fraction detected by the model.
- **F1-score:** A combined measure of precision and recall.
- **Confusion matrix:** Summarizes true positives, true negatives, false positives, and false negatives.
- **Accuracy:** The fraction of predictions that are correct. It can be misleading when fraud is rare.

## Limitations

- Synthetic sample data cannot demonstrate real-world fraud-detection performance.
- Results depend on data quality, feature selection, class balance, and the evaluation method.
- Feature importance shows model associations; it does not establish causation.
- Changing the threshold changes the trade-off between missed fraud and false alarms.
- A production system would require security, privacy safeguards, monitoring, and validation on representative data.

## Future Improvements

- Add time-based validation and cross-validation.
- Tune hyperparameters and compare models consistently.
- Include precision-recall curves and ROC-AUC where appropriate.
- Add SHAP explanations for individual predictions.
- Monitor model drift and retraining performance.
- Add authentication, audit logs, and secure data handling.

## Contributing

Suggestions and contributions are welcome. Open an issue to report a bug or propose an improvement, or submit a pull request.

## License

Choose a license before publishing. If you select an open-source license, include its full text in a `LICENSE` file.

## Author

**Your Name**  
GitHub: [@YOUR-USERNAME](https://github.com/YOUR-USERNAME)
