# ScamShield AI: An AI-Powered Phishing Email Detection System

AI Engineering

> ScamShield AI is a web application that helps users identify potentially phishing emails by analysing their text and displaying a prediction, confidence score, and possible warning signs.

## Problem Statement

Phishing emails imitate trusted people or organisations to trick users into revealing sensitive information, clicking unsafe links, or making payments. University students, office workers, and everyday email users may find these messages difficult to recognise, especially when the wording looks convincing. AI-based text classification can help identify suspicious language patterns and provide users with an accessible way to check potentially dangerous emails.

## Evidence of the Problem

- The Anti-Phishing Working Group (APWG) recorded 989,123 phishing attacks in the fourth quarter of 2024, showing that phishing remains a widespread cybersecurity threat. Source: APWG, *Phishing Activity Trends Report: 4th Quarter 2024*. https://docs.apwg.org/reports/apwg_trends_report_q4_2024.pdf
- The Kaggle *Phishing Email Dataset* contains approximately 82,500 emails from several sources, including emails labelled as spam and legitimate. This provides a starting point for training and evaluating an email classification model. Source: Naser Abdullah Alam, *Phishing Email Dataset*. https://www.kaggle.com/datasets/naserabdullahalam/phishing-email-dataset

## Initial Related Work / Existing Approaches

- **Al-Subaiey et al. (2024), "Novel Interpretable and Robust Web-based AI Platform for Phishing Email Detection."** This study presents a machine-learning-based web platform for phishing email detection with explainable AI features. This project will focus on a simpler implementation using lightweight models suitable for a student project. Source: https://arxiv.org/abs/2405.11619
- **"Phishing Email Detection Model Using Deep Learning" (2023).** This study explores deep-learning methods for detecting phishing emails. Deep-learning approaches may require more computing resources and implementation effort, so this project will begin with traditional machine-learning models. Source: https://www.mdpi.com/2079-9292/12/20/4261
- **"An improved transformer-based model for detecting phishing, spam and ham emails: A large language model approach" (2024).** This study explores transformer-based methods for classifying phishing, spam, and legitimate emails. In comparison, this project will focus on binary classification and a straightforward web interface. Source: https://doi.org/10.1002/spy2.402

## Project Objectives

- **O1:** To prepare and analyse a publicly available Kaggle phishing email dataset for binary classification of phishing/spam and legitimate emails.
- **O2:** To develop a web-based phishing email detection application using TF-IDF text features and machine-learning classifiers, specifically Logistic Regression and Linear Support Vector Machine (Linear SVM).
- **O3:** To evaluate and compare the classifiers using precision, recall, macro F1-score, and a confusion matrix, with particular attention to missed phishing emails and false alarms.

## Target Users

The target users are university students, office workers, and everyday email users who want help checking suspicious emails. Users will be able to paste an email subject and body into the application and view the predicted category, confidence score where supported, and possible warning signs. The system is intended as a decision-support tool and not a replacement for email security software.

## Data Sources

- **Phishing Email Dataset — Naser Abdullah Alam (Kaggle):** https://www.kaggle.com/datasets/naserabdullahalam/phishing-email-dataset  
  This dataset combines email collections from several sources and includes spam/phishing and legitimate labels. Since the labels may include general spam rather than phishing alone, this limitation will be considered during data preparation and evaluation.

- **Email Spam Classification Competition (Kaggle):** https://www.kaggle.com/competitions/email-spam-classify/overview  
  This dataset may be considered as a secondary source for additional experiments. However, spam classification does not necessarily mean phishing detection, so the dataset's labels and format must be checked before use.

## Project Scope

- Focus on email text, including the subject and message body.
- Classify emails into two categories: phishing/spam and legitimate, based on the available dataset labels.
- Use TF-IDF to convert email text into numerical features.
- Train and compare Logistic Regression and Linear SVM classifiers.
- Develop a simple web application using Streamlit.
- Evaluate model performance using precision, recall, macro F1-score, and a confusion matrix.
- The prototype will not connect to users' email accounts, open links, or execute websites in a virtual machine.
- The system may make incorrect predictions and cannot guarantee that an email is safe.

## Weekly Progress

| Week | Focus | Deliverable | Status |
|------|-------|-------------|--------|
| W1 | System map + project scope | README + project documentation | In progress |