## Problem Evidence

1. The Anti-Phishing Working Group (APWG) recorded 989,123 phishing attacks worldwide in the fourth quarter of 2024. This shows that phishing remains a widespread cybersecurity threat and supports the need for tools that help users identify suspicious messages. Source: Anti-Phishing Working Group (2025), *Phishing Activity Trends Report: 4th Quarter 2024*. https://docs.apwg.org/reports/apwg_trends_report_q4_2024.pdf

2. The FBI's Internet Crime Complaint Center (IC3) received 193,407 complaints related to phishing and spoofing in 2024. Phishing and spoofing were the most frequently reported crime categories in the FBI's 2024 Internet Crime Report. This highlights the importance of helping users recognise potentially fraudulent communications before responding to them. Source: Federal Bureau of Investigation (2025), *2024 Internet Crime Report*. https://www.ic3.gov/AnnualReport/Reports/2024_IC3Report.pdf

## Existing Approaches

1. **Novel Interpretable and Robust Web-based AI Platform for Phishing Email Detection (Al-Subaiey et al., 2024):** Develops a web-based machine-learning platform for detecting phishing emails and provides explanations for its predictions. This project will use a simpler implementation with lightweight machine-learning models. Source: https://arxiv.org/abs/2405.11619

2. **Phishing Email Detection Model Using Deep Learning (2023):** Explores deep-learning techniques for classifying phishing emails. This project will instead begin with traditional machine-learning models to reduce implementation complexity and computing requirements. Source: https://www.mdpi.com/2079-9292/12/20/4261

3. **An Improved Transformer-Based Model for Detecting Phishing, Spam and Ham Emails (2024):** Uses transformer-based methods to classify phishing, spam, and legitimate emails. This project will focus on binary classification using TF-IDF, Logistic Regression, and Linear SVM, with a simple web interface. Source: https://doi.org/10.1002/spy2.402

## Project / Engineering Gap

Existing approaches demonstrate that machine learning and deep learning can be used to detect phishing emails. However, there is still a practical need for a simple and accessible application that allows users to check suspicious email content without requiring technical knowledge. This project addresses that need by developing a lightweight web application and comparing traditional machine-learning models to identify a suitable approach for the prototype.

## Objective O1

To design a phishing email detection system by preparing and analysing a publicly available Kaggle dataset and selecting suitable text-processing and machine-learning techniques.

## Objective O2

To develop a web-based phishing email detection application using TF-IDF, Logistic Regression, and Linear Support Vector Machine (Linear SVM) to classify emails as phishing/spam or legitimate.

## Objective O3

To evaluate and compare the performance of Logistic Regression and Linear SVM using precision, recall, macro F1-score, and a confusion matrix.

## Intended Users

University students, office workers, and everyday email users who want assistance identifying potentially suspicious emails.

## Supported Tasks

- Allow users to enter or paste an email subject and body.
- Analyse the email text using a trained machine-learning model.
- Classify the email as phishing/spam or legitimate.
- Display the prediction and a confidence score where supported by the model.
- Highlight potential warning signs in the email text where implemented.

## Information / Knowledge Domain

The project focuses on email-based cybersecurity, phishing detection, natural language processing (NLP), text classification, and supervised machine learning. The system analyses textual patterns in email subjects and message bodies using TF-IDF features and trained classification models.

## Operating Context

The application is intended to run as a web application on a personal computer or laptop through a web browser. Users will manually paste suspicious email content into the application and receive a prediction. The prototype is intended for individual use and educational purposes.

## Important Constraints

- The project must be completed within the available academic project timeframe.
- The system will use publicly available datasets from Kaggle.
- Dataset labels may represent general spam rather than phishing specifically, which may affect classification accuracy.
- Model performance depends on the quality, balance, and representativeness of the training data.
- The application should use lightweight models that can run on a standard personal computer.
- Email content may contain personal or confidential information, so users should avoid submitting sensitive information.
- The system must be developed within the available computing resources and software requirements.

## Explicit Out-of-Scope Tasks

- Automatically accessing or monitoring users' email accounts.
- Sending, deleting, or modifying emails on behalf of users.
- Opening suspicious links or executing websites in a virtual machine.
- Analysing website HTML, website interfaces, or browser behaviour.
- Detecting phishing through image, audio, or video analysis.
- Guaranteeing that an email is safe or making final cybersecurity decisions on behalf of users.
- Replacing professional cybersecurity tools or enterprise email security systems.

## Evaluation Focus

The evaluation will determine how accurately and reliably the application classifies phishing/spam and legitimate emails. Logistic Regression and Linear SVM will be compared using precision, recall, macro F1-score, and a confusion matrix. Particular attention will be given to false negatives, where phishing emails are incorrectly classified as legitimate, and false positives, where legitimate emails are incorrectly flagged as phishing/spam. The evaluation will also consider the application's usability and ability to provide predictions within a practical response time.

# Requirements Specification — ScamShield AI

## Section 1: Functional Requirements

| # | Requirement — The system SHALL | Scope Boundary — SHALL NOT |
|---|---|---|
| FR1 | Allow users to enter or paste an email subject and message body for analysis. | Require users to connect their personal email accounts. |
| FR2 | Analyse the submitted email text and classify it as phishing/spam or legitimate. | Guarantee that every phishing email will be detected correctly or that every legitimate email is safe. |
| FR3 | Display the classification result and a confidence score when supported by the prediction model. | Present the confidence score as a guarantee that the classification is correct. |
| FR4 | Display potential warning signs identified in the submitted email, where supported by the implemented analysis. | Claim that an email is malicious based on warning signs alone without sufficient evidence. |
| FR5 | Inform users when the submitted email cannot be analysed, such as when the required text is empty or invalid. | Automatically open suspicious links, execute website content, or access external email accounts. |

## Section 2: Non-Functional Requirements

| # | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| NFR1 | Performance | The system shall return a classification result within an acceptable response time for normal email inputs. | Measure the time from submission until the result is displayed using 100 test emails. | 95th percentile response time (p95) | ≤ 3 seconds |
| NFR2 | Correctness | The system shall achieve an acceptable classification performance on a held-out test dataset not used for model training. | Compare model predictions against the ground-truth labels in the test dataset. | Macro F1-score | ≥ 0.80 |
| NFR3 | Reliability | The system shall process valid email inputs without unexpected application errors during normal use. | Submit 100 valid test emails and record successful processing and unexpected errors. | Successful processing rate | ≥ 98% |
| NFR4 | Usability | The system shall allow users to submit an email and understand the classification result without requiring technical knowledge. | Conduct a usability test with at least 5 users completing the email submission and result interpretation tasks. | Task completion rate | ≥ 90% |

## Section 3: Responsible AI Requirements

| # | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| RAI1 | False Negatives and Security Risk | The system shall minimise the risk of phishing emails being incorrectly classified as legitimate and shall display a warning that predictions may be incorrect. | Evaluate the model using a labelled test dataset and identify phishing/spam emails predicted as legitimate. | False Negative Rate (FNR) | ≤ 10% |
| RAI2 | False Positives and Unfair Classification | The system shall minimise the risk of legitimate emails being incorrectly classified as phishing/spam. | Evaluate the model using labelled legitimate emails in the test dataset and count incorrect phishing/spam predictions. | False Positive Rate (FPR) | ≤ 10% |
| RAI3 | Privacy and Data Protection | The system shall process only the email text necessary for classification and shall not store submitted email content after the prediction is completed. | Inspect application data handling and test whether submitted email content remains stored after the result is displayed. | Unintentionally retained email submissions | 0 |

## Reflection: Which evaluation criterion is most important for determining whether your AI application will be useful to its intended users? Why?

> The most important evaluation criterion is Phishing Detection Safety, measured by the False Negative Rate (FNR). This is because the main purpose of ScamShield AI is to help users identify phishing emails. If the system classifies a phishing email as legitimate, users may trust the email and expose their personal information. Therefore, keeping the false negative rate at or below 10% is important to make the system more useful and reliable for its intended users.