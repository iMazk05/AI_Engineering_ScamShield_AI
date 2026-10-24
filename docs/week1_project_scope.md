# ScamShield AI

## 1. Project Name

| Field | Description |
|---|---|
| Project Name | ScamShield AI: An AI-Powered Phishing Email Detection System |
| Domain | Artificial Intelligence, Natural Language Processing (NLP), and Cybersecurity |

## 2. Problem Statement

Phishing emails are commonly used to deceive recipients into revealing sensitive information, clicking malicious links, or performing fraudulent transactions. Users may struggle to distinguish phishing emails from legitimate messages, particularly when attackers use convincing language and impersonate trusted organisations. ScamShield AI proposes a machine learning-based web application that analyses email text, classifies emails as legitimate or phishing, and highlights potential warning signs to help users assess suspicious emails.

## 3. Evidence of the Problem

| Evidence | Description | Source / Citation |
|---|---|---|
| Evidence 1 | The Anti-Phishing Working Group (APWG) recorded 989,123 phishing attacks during the fourth quarter of 2024. Its report tracks phishing emails, phishing URLs, and phishing campaigns, demonstrating the continuing scale of phishing activity. | Anti-Phishing Working Group. (2025). *Phishing Activity Trends Report: 4th Quarter 2024*. https://docs.apwg.org/reports/apwg_trends_report_q4_2024.pdf |
| Evidence 2 | Al-Subaiey et al. (2024) highlighted the need for accessible phishing email detection solutions and developed a web-based detection platform incorporating interpretable machine learning. Their work demonstrates the relevance of developing practical systems that help users identify phishing emails. | Al-Subaiey, A., Al-Thani, M., Alam, N. A., Antora, K. F., Khandakar, A., & Zaman, S. A. U. (2024). *Novel Interpretable and Robust Web-based AI Platform for Phishing Email Detection*. arXiv. https://arxiv.org/abs/2405.11619 |

## 4. Initial Related Work

| Study / Solution | Source / Citation | Key Limitation |
|---|---|---|
| **Study 1: Novel Interpretable and Robust Web-based AI Platform for Phishing Email Detection.** Al-Subaiey et al. (2024) proposed a web-based phishing email detection platform using machine learning and explainable AI to classify emails and help users understand predictions. | Al-Subaiey, A., Al-Thani, M., Alam, N. A., Antora, K. F., Khandakar, A., & Zaman, S. A. U. (2024). https://arxiv.org/abs/2405.11619 | Although the study demonstrates a practical detection platform, detection performance on one dataset does not necessarily guarantee reliable performance on emails from different sources or newer phishing campaigns. |
| **Study 2: Phishing Email Detection Model Using Deep Learning.** This study investigated deep learning approaches for distinguishing phishing emails from legitimate messages using publicly available email datasets. | *Phishing Email Detection Model Using Deep Learning*. (2023). *Electronics, 12*(20), Article 4261. https://www.mdpi.com/2079-9292/12/20/4261 | Deep learning models may require greater computational resources and more complex implementation than traditional machine learning models. Results can also depend on dataset quality and the evaluation method. |
| **Study 3: An Improved Transformer-Based Model for Detecting Phishing, Spam and Ham Emails: A Large Language Model Approach.** Jamal et al. (2024) investigated transformer-based classification for distinguishing phishing, spam, and legitimate emails. | *An improved transformer-based model for detecting phishing, spam and ham emails: A large language model approach*. (2024). *Security and Privacy*. https://doi.org/10.1002/spy2.402 | Transformer-based approaches can require more computational resources and may be more difficult to deploy than lightweight classifiers. Their performance must also be validated on independent and representative email data. |

## 5. Engineering Gap / Limitation

Existing research demonstrates that machine learning and deep learning can detect phishing emails. However, model performance may vary across datasets, and highly accurate predictions do not necessarily guarantee reliable detection of previously unseen phishing messages. Some approaches also require greater computational resources or provide limited explanations that ordinary users can understand.

ScamShield AI will address this practical gap by developing a lightweight web application that compares traditional machine learning models, classifies email text, and highlights potential warning signs. The system will be evaluated using held-out test data to measure classification performance and identify false positives and false negatives. The initial prototype will focus on English-language email text rather than complete email infrastructure or live email account integration.

## 6. Initial Project Objectives

| Objective | Description |
|---|---|
| O1: Design | To design a machine learning-based phishing email detection system using a publicly available Kaggle email dataset and appropriate natural language processing techniques. |
| O2: Develop | To develop a web-based phishing email detection application using Python, scikit-learn, and Streamlit, incorporating email classification and explanations of potential warning signs. |
| O3: Evaluate | To evaluate and compare Logistic Regression and Linear Support Vector Machine (SVM) models using precision, recall, macro F1-score, and a confusion matrix on held-out test data. |

## 7. Target Users

The primary target users are university students, office workers, and everyday email users who want assistance identifying potentially fraudulent emails. These users may encounter phishing messages that imitate trusted organisations, request sensitive information, or encourage recipients to click suspicious links.

The system will allow users to submit an email's subject and body for analysis and receive a predicted category, confidence score, and explanation of potential warning signs. The initial prototype will focus on English-language emails, with future expansion to other languages and more advanced email security features.

## 8. Data Sources

| Source | Description | URL |
|---|---|---|
| Source 1 | **Phishing Email Dataset by Naser Abdullah Alam.** A public Kaggle dataset combining several email corpora, including Enron, Ling, CEAS, Nazario, Nigerian Fraud, and SpamAssassin. It contains approximately 82,500 emails, including spam/phishing and legitimate messages. This will be the primary dataset for training and evaluating the model. | https://www.kaggle.com/datasets/naserabdullahalam/phishing-email-dataset |
| Source 2 | **Phishing Email Data by Type.** An additional public dataset listed in the literature on deep learning-based phishing email detection. It may be considered for further testing after verifying its current availability, labels, and licence. | https://www.kaggle.com/datasets/charlottehall/phishing-email-data-by-type |

## 9. Similar to EduAdvisor

- Both projects use AI to address a clearly defined user problem.
- Both rely on publicly available data or documents.
- Both provide an application where users submit input and receive useful results.
- Both can be evaluated using measurable criteria.
- Both require appropriate safeguards to reduce misleading outputs.

## 10. Different from EduAdvisor

- ScamShield AI focuses on cybersecurity and phishing email classification rather than academic information retrieval and question answering.
- Its core AI component is a supervised machine learning classifier rather than a retrieval-augmented generation (RAG) system.
- It analyses email text and highlights suspicious wording rather than retrieving answers from official university documents.
- Its evaluation focuses on precision, recall, macro F1-score, false positives, and false negatives rather than answer correctness and document groundedness.

## 11. Responsible AI Risks

| Risk | Description | Mitigation |
|---|---|---|
| Risk 1: False negatives | The system may classify a phishing email as legitimate, causing users to trust a potentially harmful message. | Prioritise phishing recall during evaluation, inspect false negatives, and clearly state that the system cannot guarantee an email is safe. |
| Risk 2: False positives | Legitimate emails may be incorrectly classified as phishing, potentially causing users to ignore important communications. | Measure precision and false-positive rates, compare models, and present predictions as warnings rather than definitive judgements. |
| Risk 3: Dataset bias and privacy | The dataset may not represent newer phishing tactics, all email providers, or messages in languages other than English. Email text may also contain sensitive personal information. | Document dataset limitations, evaluate on unseen data, avoid storing submitted email content by default, and advise users to remove sensitive information before analysis. |

## References

Al-Subaiey, A., Al-Thani, M., Alam, N. A., Antora, K. F., Khandakar, A., & Zaman, S. A. U. (2024). *Novel interpretable and robust web