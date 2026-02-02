# Invoice Payment Prediction

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

Machine learning model for predicting late invoice payments to optimize cash flow management and improve accounts receivable operations.

## Dataset

- Source: IBM Watson Analytics - Accounts Receivable Sample
- Size: 2,586 invoices
- Time Period: 2012-2013
- Target: Binary classification (Late vs On-Time payment)

## Installation and Usage

**Prerequisites:**
- Python 3.8 or higher
- Jupyter Notebook

**Setup:**
```bash
# Clone this repository
git clone https://github.com/wdmartin45/invoice-payment-prediction.git
cd invoice-payment-prediction

# Install required packages
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook
```

Open `notebooks/IBM_Invoice_Final.ipynb` and run all cells.

## Project Structure

```
invoice-payment-prediction/
│
├── notebooks/
│   └── IBM_Invoice_Final.ipynb
├── data/
│   └── WA_Fn-UseC_-Accounts-Receivable_with_missing
├── requirements.txt
└── README.md
```

## Executive Summary

The goal of this project was to create a model capable of predicting invoice payments that would arrive late. Three models were trained and evaluated, with Logistic Regression and Random Forest with SMOTE emerging as the most effective approaches. Based on comparative analysis, Logistic Regression is the recommended model due to its slightly higher accuracy, precision, and F1-score, as well as its easier interpretability compared to Random Forest.

### Final Model Performance
- **Accuracy:** ~87%
- **F1-Score:** 0.81
- **AUC:** 0.92

These are impressive metrics that indicate the model should perform well in a production environment.

## Model Comparison

| Model | Accuracy | Precision | Recall | F1-Score | AUC |
|-------|----------|-----------|--------|----------|-----|
| Logistic Regression | 87% | 0.85 | 0.78 | 0.81 | 0.92 |
| Random Forest (SMOTE) | 86% | 0.83 | 0.79 | 0.81 | 0.91 |
| Gradient Boosting | 85% | 0.82 | 0.77 | 0.79 | 0.90 |
<img width="846" height="701" alt="image" src="https://github.com/user-attachments/assets/99cdd3e7-c599-4686-86ea-bf4082e6766e" />


## Methodology Highlights

The model's main success came from its ability to leverage historical customer data to predict late payments. By splitting the data and calculating aggregated customer statistics, we significantly boosted the model's predictive power without introducing data leakage. This approach ensures that the model should perform similarly on new data outside the test set, maintaining its reliability in real-world applications.
<img width="909" height="547" alt="image" src="https://github.com/user-attachments/assets/d3d109da-7079-448e-8a0d-8551c9747186" />

## Limitations & Considerations

### New Customer Challenge
When encountering new customers without historical data, the model may not be as effective at predicting late payment rates. This is an inherent limitation of the customer-history-based approach.

### Trend Analysis
An important consideration for implementation is the observed trend of decreasing late payment rates over time. If this trend continues, it may be worth re-evaluating the model to ensure it doesn't rely too heavily on historical data that no longer reflects current payment behaviors. Regular model retraining should be considered to maintain optimal performance.
<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/db3ab0bd-0e4d-46ad-b3fb-e3b50828119b" />

## Business Applications & Future Work

### Primary Use Case: Cash Flow Optimization
The immediate benefit of implementing this model is improved cash flow forecasting. By accurately predicting which invoices are likely to be paid late, the company can:
- Better manage working capital
- Make more informed decisions about credit extensions
- Optimize collection efforts by prioritizing high-risk accounts

### Extended Application: Bad Debt Prediction
This model framework could be adapted for additional use cases. A particularly valuable extension would be predicting which invoices are likely not just to be late, but to ultimately be written off as uncollectible. This enhanced model could:
- Improve accuracy of the allowance for doubtful accounts
- Optimize bad debt write-offs for tax purposes
- Enhance financial reporting accuracy
- Enable more proactive account management

### Future Enhancements
With additional time and data, this model could be further developed to:
- Incorporate real-time payment behavior updates
- Add industry-specific risk factors
- Develop customer segmentation strategies
- Create automated intervention triggers for at-risk accounts

## Conclusion

The invoice payment prediction model demonstrates strong performance and practical business value. While limitations exist around new customer predictions and evolving payment trends, the model provides a solid foundation for improved financial planning and risk management. With thoughtful implementation and periodic refinement, this tool can deliver significant value to the organization's financial operations.
