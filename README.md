# Niyam-IT-PPP-Anomaly-Detection

### Basic Information

* **Person or organization developing model**: Niyam IT; Rohit Bollineni (rbollineni@niyamit.com), GWU MSBA; Rose Hemans (rose.hemans@gwu.edu), Bagya Maduwanthi Widanagamage (bmwidanagamage@gwu.edu), Kaixuan (Kevin) Han (kaixuan.han@gwu.edu), Pavneet Singh (pavneet@gwu.edu)
  
* **Model date**: Nov, 2023
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: (ADD AT END)

### Intended Use
* **Primary intended uses**: This model is an example of an end-to-end anomaly detection modeling process that is intended to be used as a guide for current and future anomaly detection models.
* **Primary intended users**: Niyam IT, Patrick Hall, and students in the GW MSBA DNSC 6317 class.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

* ### Training Data

* Data dictionary: 

| Name                              | Modeling Role | Measurement Level | Description                                                               |
| --------------------------------- | ------------- | ----------------- | ------------------------------------------------------------------------- |
| **LoanNumber**                    | ID            | int               | unique row identifier                                                      |
| **DateApproved**                  | excluded         | date              | date when the loan was approved                                            |
| **SBAOfficeCode**                 | excluded         | categorical       | SBA Origination Office Code                                                |
| **ProcessingMethod**              | input         | categorical       | Loan Delivery Method (PPP for first draw; PPS for second draw)             |
| **BorrowerName**                  | excluded         | text              | Name of the borrower                                                       |
| **BorrowerAddress**               | excluded         | text              | Street address of the borrower                                             |
| **BorrowerCity**                  | input         | categorical       | City of the borrower                                                        |
| **BorrowerState**                 | input         | categorical       | State of the borrower                                                       |
| **BorrowerZip**                   | excluded         | categorical       | Zip code of the borrower                                                   |
| **LoanStatusDate**                | excluded         | date              | Date indicating the loan status                                            |
| **LoanStatus**                    | input         | categorical       | Description of loan status                                                 |
| **Term**                          | input         | int               | Loan Maturity in Months                                                    |
| **SBAGuarantyPercentage**         | excluded         | float             | Percentage of SBA Guaranty                                                 |
| **InitialApprovalAmount**         | input         | float             | Loan Approval Amount (at origination)                                      |
| **CurrentApprovalAmount**         | input         | float             | Loan Approval Amount (current)                                             |
| **UndisbursedAmount**             | excluded         | float             | Amount not yet disbursed                                                   |
| **FranchiseName**                 | excluded         | categorical       | Name of the franchise                                                      |
| **ServicingLenderLocationID**     | input         | categorical       | Lender Location ID                                                         |
| **ServicingLenderName**           | excluded         | categorical       | Name of the servicing lender                                               |
| **ServicingLenderAddress**        | excluded         | text              | Street address of the servicing lender                                     |
| **ServicingLenderCity**           | input         | categorical       | City of the servicing lender                                               |
| **ServicingLenderState**          | input         | categorical       | State of the servicing lender                                              |
| **ServicingLenderZip**            | excluded         | categorical       | Zip code of the servicing lender                                           |
| **RuralUrbanIndicator**           | input         | categorical       | Indicator for rural or urban                                               |
| **HubzoneIndicator**              | input         | categorical       | Indicator for Hubzone (Y/N)                                                |
| **LMIIndicator**                  | input         | categorical       | Indicator for Low to Moderate Income (Y/N)                                 |
| **ProjectCity**                   | input         | categorical       | City of the project                                                        |
| **ProjectCountyName**             | excluded         | categorical       | County Name of the project                                                 |
| **ProjectState**                  | input         | categorical       | State of the project                                                       |
| **ProjectZip**                    | excluded         | categorical       | Zip code of the project                                                    |
| **CD**                            | input         | categorical       | Project Congressional District                                              |
| **NAICSCode**                     | excluded         | categorical       | NAICS 6 digit code                                                         |
| **Race**                          | excluded         | categorical       | Borrower Race Description                                                  |
| **Ethnicity**                     | excluded         | categorical       | Borrower Ethnicity Description                                             |
| **UTILITIES_PROCEED**             | input         | float             | Proceeds for utilities                                                     |
| **PAYROLL_PROCEED**               | input         | float             | Proceeds for payroll                                                       |
| **MORTGAGE_INTEREST_PROCEED**     | input         | float             | Proceeds for mortgage interest                                             |
| **RENT_PROCEED**                  | input         | float             | Proceeds for rent                                                          |
| **REFINANCE_EIDL_PROCEED**        | input         | float             | Proceeds for EIDL refinance                                                |
| **DEBT_INTEREST_PROCEED**         | input         | float             | Proceeds for debt interest                                                 |
| **BusinessType**                  | input         | categorical       | Description of business type                                               |
| **OriginatingLenderLocationID**   | input         | categorical       | Originating Lender ID                                                      |
| **OriginatingLender**             | input         | categorical       | Name of the originating lender                                             |
| **OriginatingLenderCity**         | input         | categorical       | City of the originating lender                                             |
| **OriginatingLenderState**        | input         | categorical       | State of the originating lender                                            |
| **Gender**                        | excluded         | categorical       | Gender Indicator                                                           |
| **Veteran**                       | excluded         | categorical       | Veteran Indicator                                                          |
| **NonProfit**                     | input         | categorical       | 'Yes' if Business Type = Non-Profit Organization or Non-Profit Childcare Center or 501(c) Non Profit |
| **UTILITIES_PROCEED_purpose**     | input         | categorical       | Purpose of utilities proceeds                                              |
| **PAYROLL_PROCEED_purpose**       | input         | categorical       | Purpose of payroll proceeds                                                |
| **MORTGAGE_INTEREST_PROCEED_purpose** | input    | categorical       | Purpose of mortgage interest proceeds                                      |
| **RENT_PROCEED_purpose**          | input         | categorical       | Purpose of rent proceeds                                                   |
| **REFINANCE_EIDL_PROCEED_purpose**| input        | categorical       | Purpose of EIDL refinance proceeds                                         |
| **HEALTH_CARE_PROCEED_purpose**   | input         | categorical       | Purpose of healthcare proceeds                                             |
| **DEBT_INTEREST_PROCEED_purpose** | input         | categorical       | Purpose of debt interest proceeds                                          |
| **NAICS Industry Description**    | input         | categorical       | Description of NAICS industry                                              |
| **Size standards in number of employees** | input | categorical  | Size standards in number of employees                                      |
| **Forgiven**                      | input        | categorical       | Categorical indicator if the loan is forgiven                              |
| **non_forgiven_loan_portion**     | input        | float             | Portion of the loan not forgiven                                           |
| **ApprovalDifference**            | input        | float             | Difference between initial and current approval amount                     |
| **ApprovalDifference_per_employee** | input     | float             | Approval difference per employee                                           |
| **InitialApprovalAmount_per_employee** | input  | float             | Initial approval amount per employee                                       |
| **CurrentApprovalAmount_per_employee** | input  | float             | Current approval amount per employee                                       |
| **UTILITIES_PROCEED_per_employee** | input       | float             | Utilities proceeds per employee                                            |
| **PAYROLL_PROCEED_per_employee**  | input       | float             | Payroll proceeds per employee                                              |
| **MORTGAGE_INTEREST_PROCEED_per_employee** | input | float      | Mortgage interest proceeds per employee                                   |
| **RENT_PROCEED_per_employee**     | input        | float             | Rent proceeds per employee                                                 |
| **REFINANCE_EIDL_PROCEED_per_employee** | input | float           | EIDL refinance proceeds per employee                                       |
| **HEALTH_CARE_PROCEED_per_employee** | input   | float             | Healthcare proceeds per employee                                           |
| **DEBT_INTEREST_PROCEED_per_employee** | input | float           | Debt interest proceeds per employee                                        |
| **ForgivenessAmount_per_employee** | input       | float             | Forgiveness amount per employee                                            |
| **Prior PPP count**               | input         | int               | Count of previous PPP loans                                                |
| **Prior PPS count**               | input         | int               | Count of previous PPS loans                                                |
| **expected_UTILITIES_PROCEED**    | input        | float             | Expected utilities proceeds                                                |
| **expected_PAYROLL_PROCEED**      | input        | float             | Expected payroll proceeds                                                  |
| **expected_MORTGAGE_INTEREST_PROCEED** | input | float           | Expected mortgage interest proceeds                                        |
| **expected_RENT_PROCEED**         | input        | float             | Expected rent proceeds                                                     |
| **expected_REFINANCE_EIDL_PROCEED** | input      | float             | Expected EIDL refinance proceeds                                           |
| **expected_HEALTH_CARE_PROCEED**  | input        | float             | Expected healthcare proceeds                                               |
| **expected_DEBT_INTEREST_PROCEED** | input      | float             | Expected debt interest proceeds                                            |
| **expected_ForgivenessAmount**    | input        | float             | Expected forgiveness amount                                                |
| **expected_ApprovalDifference**   | input        | float             | Expected approval difference                                               |
| **expected_InitialApprovalAmount** | input       | float             | Expected initial approval amount                                            |
| **expected_CurrentApprovalAmount** | input       | float             | Expected current approval amount                                           |
| **deviant_JR**                    | input         | float             | Deviant value for jobs reported                                                      |
| **deviant_JR_risk_score**         | input        | float             | Risk score for deviant jobs reported                                                  |
| **deviant_UTILITIES_PROCEED**     | input         | float             | Deviant value for utilities proceeds                                       |
| **deviant_PAYROLL_PROCEED**       | input         | float             | Deviant value for payroll proceeds                                         |
| **deviant_MORTGAGE_INTEREST_PROCEED** | input   | float             | Deviant value for mortgage interest proceeds                               |
| **deviant_RENT_PROCEED**          | input         | float             | Deviant value for rent proceeds                                            |
| **deviant_HEALTH_CARE_PROCEED**   | input         | float             | Deviant value for healthcare proceeds                                      |
| **deviant_DEBT_INTEREST_PROCEED** | input         | float             | Deviant value for debt interest proceeds                                   |
| **deviant_ForgivenessAmount**     | input         | float             | Deviant value for forgiveness amount                                       |
| **deviant_ApprovalDifference**    | input         | float             | Deviant value for approval difference                                      |
| **deviant_InitialApprovalAmount** | input         | float             | Deviant value for initial approval amount                                  |
| **deviant_CurrentApprovalAmount** | input         | float             | Deviant value for current approval amount                                  |
| **deviant_UTILITIES_PROCEED_risk_score** | input | float           | Risk score for deviant utilities proceeds                                  |
| **deviant_PAYROLL_PROCEED_risk_score** | input   | float           | Risk score for deviant payroll proceeds                                    |
| **deviant_MORTGAGE_INTEREST_PROCEED_risk_score** | input | float   | Risk score for deviant mortgage interest proceeds                          |
| **deviant_RENT_PROCEED_risk_score** | input     | float           | Risk score for deviant rent proceeds                                       |
| **deviant_REFINANCE_EIDL_PROCEED_risk_score** | input | float      | Risk score for deviant EIDL refinance proceeds                             |
| **deviant_HEALTH_CARE_PROCEED_risk_score** | input  | float           | Risk score for deviant healthcare proceeds                                 |
| **deviant_DEBT_INTEREST_PROCEED_risk_score** | input | float        | Risk score for deviant debt interest proceeds                              |
| **deviant_ForgivenessAmount_risk_score** | input | float           | Risk score for deviant forgiveness amount                                  |
| **deviant_ApprovalDifference_risk_score** | input | float          | Risk score for deviant approval difference                                 |
| **deviant_InitialApprovalAmount_risk_score** | input | float        | Risk score for deviant initial approval amount                             |
| **deviant_CurrentApprovalAmount_risk_score** | input | float        | Risk score for deviant current approval amount                             |
| **average_risk_score**            | output        | float             | Average risk score                                                         |



* **Source of training data**:
* Small Business Administration (https://data.sba.gov/dataset/ppp-foia),
* Data.gov (https://catalog.data.gov/dataset/small-business-administration-sba-size-standards-table)
  
* **Number of rows in training data**:
  * Training rows: 965,548
 
### Model details
* **Columns used as inputs in the final model**: 'ProcessingMethod', 'LoanStatus', 'Term',
                  'InitialApprovalAmount', 'CurrentApprovalAmount', 'ForgivenessAmount', 
                  'RuralUrbanIndicator', 'HubzoneIndicator', 'LMIIndicator',
                  'BusinessAgeDescription', 'CD', 'JobsReported', 'NonProfit',
                  'BusinessType', 'NAICS Industry Description', 'Size standards in number of employees',
                  'UTILITIES_PROCEED', 'PAYROLL_PROCEED', 'MORTGAGE_INTEREST_PROCEED',
                  'RENT_PROCEED', 'REFINANCE_EIDL_PROCEED', 'HEALTH_CARE_PROCEED', 'DEBT_INTEREST_PROCEED',
                  'non_forgiven_loan_portion','ApprovalDifference', 'ApprovalDifference_per_employee',
                  'InitialApprovalAmount_per_employee', 'CurrentApprovalAmount_per_employee',
                  'UTILITIES_PROCEED_per_employee', 'PAYROLL_PROCEED_per_employee', 'MORTGAGE_INTEREST_PROCEED_per_employee',
                  'RENT_PROCEED_per_employee', 'REFINANCE_EIDL_PROCEED_per_employee', 'HEALTH_CARE_PROCEED_per_employee',
                  'DEBT_INTEREST_PROCEED_per_employee', 'ForgivenessAmount_per_employee',
                  'BorrowerCity', 'BorrowerState', 'ServicingLenderCity', 'ServicingLenderState',
                  'ServicingLenderLocationID', 'ProjectCity', 'ProjectState',
                  'OriginatingLenderLocationID', 'OriginatingLender', 'OriginatingLenderCity', 'OriginatingLenderState',
                  'deviant_JR', 'deviant_UTILITIES_PROCEED', 'deviant_PAYROLL_PROCEED', 'deviant_MORTGAGE_INTEREST_PROCEED',
                  'deviant_RENT_PROCEED', 'deviant_REFINANCE_EIDL_PROCEED', 'deviant_HEALTH_CARE_PROCEED',
                  'deviant_DEBT_INTEREST_PROCEED', 'deviant_ForgivenessAmount', 'deviant_ApprovalDifference',
                  'deviant_InitialApprovalAmount', 'deviant_CurrentApprovalAmount'
  
* **Type of model**: Unsupervised Average Weighted Ensemble Anomaly Detection
  
### Model Composition**:
The ensemble model comprises three components:

1. Isolation Forest
    * **Software used to implement the model**: Python, scikit-learn
    * **Version of the modeling software**: (ADD AT END)
    * **Hyperparameters or other settings of model**:
```
IsolationForest(n_estimators=50, max_samples = auto, contamination = 0.01, max_features = 1.0, bootstrap = False, n_jobs = None, random_state=12345, verbose = 0, warm_start = False)
```

2. Isolation Forest
    * **Software used to implement the model**: Python, H2O
    * **Version of the modeling software**: (ADD AT END)
    * **Hyperparameters or other settings of model**:
```
hyper_params = {
    'ntrees':list(range(20, 140, 20)),
    'max_depth':list(range(2, 30, 2)),
    'sample_rate':[s/float(10) for s in range(1, 11)],
    'col_sample_rate_per_tree' : [s/float(10) for s in range(1, 11)]}

search_criteria = {
    "strategy": "RandomDiscrete",
    "max_models": 50,
    "seed": 100,
    'max_runtime_secs':3600}

# Set up grid search
grid = H2OGridSearch(
    model=H2OIsolationForestEstimator,
    grid_id='iso_grid1',
    hyper_params=hyper_params,
    search_criteria=search_criteria
)
```
```
train, test = ppp_model.split_frame(ratios = [0.70])
grid.train(x=anomaly_inputs, training_frame=train)
```
```
#selected model: iso_grid1_model_31
isolationForest(ntrees = 40.0, max_depth = 24.0, sample_rate = 0.9, col_sample_rate_per_tree = 1.0)
```

3. Average Risk Score
    * **Software used to implement the model**: Python, pandas
    * **Version of the modeling software**: (ADD AT END)
    * **Calculation of average risk score**: Using industry size standards, we calculated standard 'expected' figures for 'per employee' data for UTILITIES_PROCEED, PAYROLL_PROCEED, MORTGAGE_INTEREST_PROCEED, REFINANCE_EIDL_PROCEED, HEALTH_CARE_PROCEED, DEBT_INTEREST_PROCEED, InitialApprovalAmount, CurrentApprovalAmount, ApprovalDifference, and ForgivenessAmount. We then calculated 'deviant' figures by calculating the difference between actual and 'expected' figures for each loan. Risk scores for each figure were calculated by percentile rank among all loans. The final average risk score is a simple arithmetic mean of risk scores:
  
```
# Calculate Average Risk Score
clean['average_risk_score'] = clean[['deviant_UTILITIES_PROCEED_risk_score',
            'deviant_PAYROLL_PROCEED_risk_score',
            'deviant_MORTGAGE_INTEREST_PROCEED_risk_score',
            'deviant_RENT_PROCEED_risk_score',
            'deviant_REFINANCE_EIDL_PROCEED_risk_score',
            'deviant_HEALTH_CARE_PROCEED_risk_score',
            'deviant_DEBT_INTEREST_PROCEED_risk_score',
            'deviant_ForgivenessAmount_risk_score',
            'deviant_ApprovalDifference_risk_score',
            'deviant_InitialApprovalAmount_risk_score',
            'deviant_CurrentApprovalAmount_risk_score']].mean(axis=1)
```     
 
**Columns as outputs of models**: 'final_anomaly_score', 'final_blended_anomaly_indicator'

### Quantitative Analysis

** Isolation Forest (H2O)**

| Anomaly Score | Normalized Anomaly Score |
| ------------- | ------------------------ |
| 22.913 | 0.006|

| Number of Trees | Number of Internal Trees | Model Size in Bytes | Min Depth | Max Depth | Min Leaves | Max Leaves | Mean Leaves |
| --------------- | ------------------------ | ------------------- | --------- | --------- | ---------- | ---------- | ----------- |
| 40.0 | 40.0 | 9,689,439.0 | 24.0 | 24.0 | 24.0 | 7030.0 | 34,088.0 | 19,211.75 |

### General Exploratory Data Analysis

#### Correlation Heatmap

Initial and Current Approval Amount were both highly correlated with ForgivenessAmount, indicating both in a statistical sense the higher the approval amount, the higher the forgiveness amount but logically of the loans that were forgiven, it would seem that they were mostly, if not completely forgiven, rather than just partially.

Initial and Current Approval Amount were both highly correlated with PAYROLL_PROCEED, indicating that most loans were used to process Payroll rather than utilities, mortgage interest, rent, EIDL refinancing, healthcare, or debt interest. Ranked by correlation: payroll, rent, healthcare, mortgage interest, debt interest, EIDL refinance.

Initial and Current Approval amount were highly correlated with JobsReported, indicating that the SBA and lenders generally approved higher loan amounts for businesses that reported more jobs.

![Correlation Heatmap](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/f5278f20ebba7306cea7cf41ecc59b0bfe839bde/ppp_eda_corr.png)

#### Initial and Current Approval Amount Scatter Plot

The lower the initial and current approval amount, the more likely loans will center around the line of best fit. The distribution of residuals is not constant as initial and current approval amounts rise as we can see points more sporadically plotted further from the line of best fit.

![Init/Current Approval Scatter](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/cc030bf856c35663770c7c412e7cbf63b15af3d6/ppp_eda_intial_current_scatter.png)

#### Applications by Industry

Full service restaurants by far accounted for the most number of loan applications. Professional offices like Offices of Physicians, Offices of Lawyers, Offices of Dentists were also particularly prevalent for industries where loan applications were high.

![Loan Apps by Industry](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/d106ed5d65b20b7452d978c242dae2fdc14b9097/ppp_eda_industries_count.png)

#### Applications by Loan Draw

Roughly 70% of all applications were for First Draw PPP loans, with the remainder representing Second Draw PPS loans. Officially, only those who have fewer than 300 employees, have previously received a First Draw PPP loan or can demonstrate at least a 25% reduction in gross receipts between comparable quarters in 2019 and 2020 were eligible for Second Draw PPP loans.

![Draw Plot](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/796f17f3202385c02922176d58d13288f9a8c37a/ppp_eda_draw_plot.png)

#### Loan Term by Draw

In general, we can say that Second Draw PPS loans on average had a higher loan term than that of First Draw PPP loans. The mean loan term for PPP loans was 24.5 months while for PPS loans it was 52 months.

![Loan Term Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/aeb62f40cfdda3aeeb2e8fd66f58e5c181ee20ff/ppp_eda_term_draw.png)

#### Loans by State

In accordance with population size, California, Texas, New York, and Florida were the top 4 states for the number of applications.

![States](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/aeb62f40cfdda3aeeb2e8fd66f58e5c181ee20ff/ppp_eda_state.png)

#### Current Loan Amount Per Employee by Jobs Reported

We can start to analyze outliers here by observing very large loan amounts borrowed for companies with very low numbers of jobs reported. Many companies reporting less than 10 employees can be seen to have borrowed excessively large loan amounts.

![Current PE by JR](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/raw/aeb62f40cfdda3aeeb2e8fd66f58e5c181ee20ff/ppp_eda_loan_amount_emp.png)

### Average Risk Score Model Exploratory Data Analysis

After calculating the average risk score for each loan, we have prepared the following EDA:

#### Distribution of Average Risk Scores

The mean average risk score for all loans was 0.228 and the threshold for the top 1.5% of risk scores was 0.545. Below are some other notable thresholds:

Threshold for the top 10% of risk scores: 0.394

Threshold for the top 5% of risk scores: 0.442

Threshold for the top 1% of risk scores: 0.586

![Average Risk Score Histogram]([https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/67064ecd54608507a5adf2eba3ecd19343448478/ppp_avr_hist.png](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/49c88b040f210436a14317140f54503d2e1a957b/ppp_avr_score_hist.png))

### Correlation of Numerical Features with Average Risk Score

The deviant amounts for Forgiveness Amount, Initial Approval Amount, Current Approval Amount were most highly correlated with average risk score despite all deviant risk scores being equally weighted in the Average Risk Score calculation (i.e., actual amount - expected amount based on industry size standards).

![Correlation of AVR with Numerical Features](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/67064ecd54608507a5adf2eba3ecd19343448478/ppp_avr_corr.png)

### scikit-learn Isolation Forest Model Exploratory Data Analysis

#### Distribution of sklearn Isolation Forest Anomaly Scores

The mean for anomaly scores from the sklearn Isolation Forest model was 0.0156. The model outputted 1.01% of the dataset as suspected anomalies.

![sklearn Score Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/61572e8a84a1a96af90185bec25449a6c2c364a8/ppp_skl_score_hist.png)

#### Feature Importance for sklearn Isolation Forest

PAYROLL_PROCEED_per_empoyee, Size standards in number of employees, ForgivenessAmount, and JobsReported were the most important features in this model. BorrowerState closely led and was noted for further EDA at the end of the final model.

![sklearn Feature Importance](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/89e8ec4d8e53e19899db6dbed29a83afec2a3834/ppp_sklearn_feature_importance.png)

#### Surrogate Model

We ran a surrogate model to provide a simplified interpretable model that mimics the predictions of our more complex and computationally expensive Isolation Forest model. This surrogate model is an Isolation Forest model with just one tree and the following parameters:

```
global_surrogate_dt = H2OIsolationForestEstimator(model_id = model_id,
                                               ntrees = 1, max_depth = 3,
                                               sample_rate = 1, mtries = 2, seed=12345)
global_surrogate_dt.train(training_frame = train, x = anomaly_inputs, y = "anomaly")
```

* **Model Summary**:

| Number of Trees | Number of Internal Trees | Model Size in Bytes | Min Depth | Max Depth | Min Leaves | Max Leaves | Mean Leaves |
| --------------- | ------------------------ | ------------------- | --------- | --------- | ---------- | ---------- | ----------- |
| 1.0 | 1.0 | 133.0 | 3.0 | 3.0 | 3.0 | 6.0 | 6.0 | 6.0 |

*Since the surrogate isolation forest model has just one decision tree, we have named it a decision tree but we would like to note that the model is still used in the context of anomaly detection and not classification since this is an unsupervised learning task.*

Here we can interpret the rules of the tree where UTILITIES_PROCEED_per_employee, deviant_ApprovalDifference, ServicingLenderCity, JobsReported, HEALTH_CARE_PROCEED and deviant_JR (jobs reported) were some of the most important features for splitting.

![Surrogate Model](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/b8d18791060fc4278ff41eca97645520033fc490/ppp_sklearn_surrogate_dt.png)

### H2O Isolation Forest Model Exploratory Data Analysis

#### Distribution of H2O Isolation Forest Anomaly Scores

The mean anomaly score for this model was 0.005, with the top 2.6% of scores being assigned as suspected anomalies by the model. The score threshold for these top 2.6% suspected anomalies was 0.036.

![H2O IF Anomaly Scores Histogram](https://github.com/rosehemans/Niyam-IT-PPP-Anomaly-Detection/blob/36765a2872df2da1ace34264c4d18af1955b4a10/ppp_h2o_score_hist.png)


