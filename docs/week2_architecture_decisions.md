# Architecture Needs - ScamShield AI

| Requirement ID | What does the requirement need? | Architecture Response |
|---|---|---|
| FR1 | Users must be able to submit an email subject and message body. | User input interface |
| FR2 / O2 | Submitted email text must be classified as phishing/spam or legitimate. | Email text classification capability |
| FR3 | The system must display the classification and confidence score where supported. | Prediction result and confidence display |
| FR4 | The system should identify potential warning signs where supported. | Warning sign identification capability |
| FR5 | The system must handle empty or invalid input appropriately. | Input validation control |
| NFR1 | Classification results must be displayed within 3 seconds at the 95th percentile. | Efficient processing flow and response-time measurement |
| NFR2 / O3 | The classifier must achieve a macro F1-score of at least 0.80 on a held-out test dataset. | Model evaluation component and labelled test dataset |
| RAI1 / O3 | The system should minimise phishing emails incorrectly classified as legitimate. | Phishing detection evaluation using false negative rate |
| RAI2 / O3 | The system should minimise legitimate emails incorrectly classified as phishing/spam. | False positive rate evaluation |
| RAI3 | Submitted email content must not be retained after prediction. | Non-persistent input handling and privacy checks |

# Architecture Decisions - ScamShield AI

## 1. Architecture Decision Records (ADR)

| Decision | Requirement / Constraint | Alternatives Considered | Selected Option | Trade-off Accepted |
|---|---|---|---|---|
| ADR1: Use a dedicated email classification capability | FR2, NFR2, O2, O3 | Rule-based detection only; traditional machine learning; deep learning | A dedicated text classification capability | Traditional machine learning is simpler and lighter, but may miss complex phishing patterns that more advanced models can identify. |
| ADR2: Keep model training separate from application use | O1, O2, NFR1 | Train the model every time the application starts; train offline and load the trained model | Train offline and load the trained model for predictions | Model updates require a separate training process, but normal predictions can be faster and more consistent. |
| ADR3: Validate inputs and avoid persistent email storage | FR5, RAI3 | Accept all inputs and retain submitted content; validate inputs and process email content without persistent storage | Validate required input and avoid retaining submitted email content | Less information is available for debugging because email content is not retained, but user privacy is better protected. |
| ADR4: Evaluate model performance using a held-out dataset | NFR2, RAI1, RAI2, O3 | Evaluate using training data only; use a separate labelled test dataset | Use a held-out test dataset | Some labelled data is reserved for testing, reducing the amount available for training, but the evaluation better reflects performance on unseen emails. |

## 2. Initial Requirements Traceability Matrix

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
|---|---|---|---|---|
| O1 | FR2 | Dataset preparation and suitability | Dataset preparation and model training | Dataset summary, label distribution, and preprocessing results |
| O2 | FR1, FR2, FR3 | Input handling and classification result display | Email input interface, classification capability, and result display | Functional tests using valid, empty, and invalid email inputs |
| O3 | NFR2 | Classification performance | Model evaluation component | Held-out test macro F1-score of at least 0.80 |
| O3 | RAI1 | Phishing detection safety | Model evaluation component | False negative rate of no more than 10% |
| O3 | RAI2 | Legitimate email classification | Model evaluation component | False positive rate of no more than 10% |
| O2 | NFR1 | Classification response time | Classification capability and result processing | 95th percentile response time of no more than 3 seconds across 100 test emails |
| O2 | RAI3 | Email privacy | Non-persistent input handling | Privacy tests confirm no submitted email content remains stored after prediction |

## 3. V1 Architecture Review

- The architecture supports the main user interaction: submitting email text and receiving a classification.
- Input validation supports FR5 by handling empty or invalid submissions.
- The classification capability supports FR2 and the model evaluation objectives.
- Result processing supports FR3 and FR4 where confidence scores and warning-sign analysis are available.
- The separate training and evaluation process supports model comparison without slowing down normal predictions through repeated training.
- Privacy controls support RAI3 by avoiding persistent storage of submitted email content.
- The architecture does not include email account integration, automatic link opening, website execution, or website HTML analysis because these are outside the defined project scope.

## 4. Known Trade-offs and Limitations

- A lightweight text classifier may not detect every phishing technique.
- Dataset labels may include general spam rather than phishing alone.
- Confidence scores do not guarantee that a prediction is correct.
- Warning-sign identification must be implemented and tested; it should not be presented as a capability until available.
- The proposed evaluation thresholds are targets and must be verified experimentally.