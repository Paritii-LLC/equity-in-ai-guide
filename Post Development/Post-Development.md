<h1>Post Development</h1>
The post-development phase of a machine learning project is where the focus shifts from initial development and deployment to ongoing maintenance, optimization, and evaluation. 

For complete information, practical guides and resources on post development please visit our website(link).

# Testing
Thorough testing supports the development of accurate, reliable, and robust models in real-world scenarios. This section covers strategies, recommendations, and guidelines for evaluating algorithms and outputs for bias, dealing with bias, and conducting impact assessments.

## Ensure Model is Human Interpretable
The simplest way to ensure models are interpretable is to use models that, by their design, are interpretable[^1].  This type of model refers to a machine learning model that produces results or predictions that can be easily understood, explained, and interpreted by humans, particularly those without a deep technical background in machine learning or artificial intelligence. These models are designed to provide transparency and clarity regarding how they make predictions or decisions, which is essential for gaining trust, identifying potential biases, and ensuring accountability in AI systems.
[^1]: Molnar, C. (2023, August 21). Chapter 5 Interpretable Models | Interpretable Machine Learning. Github.io. https://christophm.github.io/interpretable-ml-book/simple.html

Interpretable models, such as linear regression, logistic regression, and decision trees, provide visibility into the factors influencing predictions, enabling stakeholders, including those affected by the model's outcomes, to understand the reasoning behind decisions. While neural network models commonly used in deep learning may lack inherent interpretability, techniques exist to enhance their transparency, thereby improving understanding and promoting equitable outcomes. Developers can apply intrinsic analysis to interpret low-complexity models (simple relationships between the input variables and the predictions). They can apply post-hoc analysis to interpret simpler and more complex models, such as neural networks, which can capture non-linear interactions[^2]. These methods are often model-agnostic and provide mechanisms to interpret a trained model based on the inputs and output predictions. Post-hoc analysis can be performed at a local or global level.[^3]
[^2]: Model interpretability - Machine Learning Best Practices in Healthcare and Life Sciences. (2024). Amazon.com. https://docs.aws.amazon.com/whitepapers/latest/ml-best-practices-healthcare-life-sciences/model-interpretability.html
[^3]: Ibid.


## Evaluate Algorithms and Output for Bias
Algorithmic bias occurs when AI/ML model design, data, and sampling result in measurably different model performance for different subgroups[^4]. The two major courses of algorithmic bias are subgroup invalidity and label choice bias. Subgroup invalidity occurs when AI/ML predicts an appropriate outcome or measure, but the model performs poorly for a particular subgroup. The underlying cause is when AI/ML models are trained on non-diverse populations or with data that underrepresents the subgroup or fails to include specific risk factors affecting them. Label choice bias occurs when the algorithm’s predicted outcome is a proxy variable for the actual outcome it should be predicting[^5]. There are a few steps that can be implemented:
[^4]:  Tuck, B. (2022, April 26). Four Steps to Measure and Mitigate Algorithmic Bias in Healthcare - ClosedLoop. ClosedLoop. https://www.closedloop.ai/blog/four-steps-to-measure-and-mitigate-algorithmic-bias-in-healthcare/
[^5]: Closing the AI accountability gap: defining an end-to-end framework for internal algorithmic auditing. Proceedings of the 2020 Conference on Fairness, Accountability, and Transparency. (2020). ACM Conferences. https://dl.acm.org/doi/10.1145/3351095.3372873
[^6]:  4 Steps to Mitigate Algorithmic Bias | AHA. (2024, January 29). American Hospital Association. https://www.aha.org/aha-center-health-innovation-market-scan/2021-10-05-4-steps-mitigate-algorithmic-bias
* Inventory of algorithms - Maintain a detailed inventory of all algorithms being used or developed. Include information such as the purpose, functionality, development stage, and key components. Form a diverse committee comprising internal and external stakeholders, including subject matter experts, data scientists, legal experts, and ethicists. This committee should meet regularly to discuss algorithmic developments, ethical considerations, and potential impacts.
* Screen each algorithm for bias - Clearly define what bias means in the context of the application. Bias can manifest in various ways, such as racial, gender, or socioeconomic bias.
* On the technical side, Python libraries like Aequitas (http://aequitas.dssg.io/) can be used to test for bias in the features and output of the algorithm. Aequitas is an open-source bias audit toolkit for machine learning developers, analysts, and policymakers to audit machine learning models for discrimination and bias, and make informed and equitable decisions around developing and deploying predictive risk-assessment tools[^7].
[^7]:  Aequitas - The Bias Report. (2018). Dssg.io. http://aequitas.dssg.io/

## Mitigating Biases Between vs. Within Groups
Mitigating biases between groups and within groups involves addressing systemic biases affecting different demographic or user groups and biases arising within specific subgroups. Here are strategies for mitigating biases at both levels:
Biases Between Groups:
* Diverse Representation in Data: Ensure the training data includes diverse samples from all relevant demographic groups to avoid under-representation or marginalization.
Fair Sampling: Use techniques such as stratified sampling to ensure that each subgroup is adequately represented in the training data, preventing biases related to group size.
* Demographic-Aware Features: Develop features sensitive to demographic differences, ensuring that the algorithm considers and appropriately adjusts for variations between groups.
* Equalized Odds: Implement fairness metrics like equalized odds to ensure that the algorithm's predictions are equally accurate across different demographic groups.
* Fair Pre-Processing: Apply pre-processing techniques to the data to mitigate biases before training the algorithm, addressing disparities between groups.
* Bias-Aware Algorithms: Use algorithms specifically designed to detect and mitigate biases. Fairness-aware machine learning models incorporate fairness constraints during training. For example, developers can add a fairness regularization term to the loss function or modify the optimization algorithm to ensure fairness. 

Biases Within Groups:
* Subgroup Analysis: Conduct subgroup analysis to identify biases within specific groups. This analysis involves examining how the algorithm's performance varies across subpopulations.
* Fine-Grained Fairness Metrics: Define and use fine-grained fairness metrics that assess performance within subgroups, preventing the perpetuation of biases.
* Customized Mitigation Strategies: Develop targeted mitigation strategies for specific subgroups if biases are identified. These strategies could involve adjusting model parameters or implementing custom fairness interventions.
* Localized Training Data: Consider using localized or customized training data for certain subgroups to address specific cultural or contextual nuances.
* Sensitivity Analysis: Conduct sensitivity analyses to understand how changes in input features affect outcomes within different subgroups. These analyses can help identify and address biases at a granular level.
* User Feedback Loops: Establish feedback mechanisms that allow users to report biases or issues specific to their subgroup. Use this feedback to improve the algorithm continuously.
* Inclusive Design Principles: Incorporate inclusive design principles, involving users from diverse backgrounds in the development process to ensure that the algorithm meets the needs of all user groups.
* Regular Audits: Implement regular audits and evaluations of the algorithm's performance, focusing on both overall fairness and fairness within specific subgroups. 

## Thresholds in Post Development
In machine learning, thresholds play a significant role in various post-development activities, especially in model deployment, monitoring, and decision-making processes. Thresholds are established to manage risk exposure and mitigate potential negative consequences of model predictions[^8]. Risk thresholds determine acceptable levels of false positives or false negatives based on the application's specific context and risk tolerance.
[^8]:  Introduction to Operating Thresholds. (2018, January 22). The Official Blog of BigML.com. Retrieved February 21, 2024, from https://blog.bigml.com/2018/01/22/introduction-to-operating-thresholds/
1. Model Deployment:
* Thresholding for Classification: In classification tasks, thresholds are used to determine the class assignment of model predictions. For example, in binary classification, a threshold is applied to convert probability scores into binary outcomes (e.g., class 1 if probability > 0.5, class 0 otherwise).
* Threshold Optimization: Thresholds may be optimized during deployment to achieve specific performance objectives, such as maximizing accuracy, precision, recall, or minimizing false positives or false negatives.
2. Model Monitoring:
* Anomaly Detection: Thresholds are set to detect anomalies or deviations in model predictions or performance metrics. For example, thresholds on prediction probabilities or residuals may trigger alerts when values exceed predefined limits, indicating potential issues or changes in data patterns.
* Data Drift Monitoring: Thresholds are used to detect data drift by comparing current data distributions or statistical properties with baseline or historical data. Deviations beyond threshold values may signal shifts in data characteristics requiring model retraining or recalibration.
3. Decision-Making Processes:
* Actionable Thresholds: Thresholds define decision boundaries for taking specific actions based on model predictions. For instance, in risk assessment applications, thresholds determine whether to approve or deny a loan application, initiate medical interventions, or escalate security alerts.
* Ethical Thresholds: Thresholds can be set to enforce ethical considerations and regulatory requirements, such as fairness, privacy, or non-discrimination. Models may be designed to comply with predefined thresholds for fairness metrics or privacy constraints.

## Impact Assessment of Synthetic Data
Before deploying the model to end users, developers should conduct impact assessments through simulated tests on synthetic data. By simulating various scenarios and testing the model's performance on synthetic data that reflects the diversity of the population it will impact, developers can identify and address inequities or adverse outcomes before deployment[^9]. The following blueprint can be useful in conducting such an assessment.
[^9]:  Zhang, X., Pérez-Stable, E. J., Bourne, P. E., Peprah, E., Duru, O. K., Breen, N., Berrigan, D., Wood, F., Jackson, J. S., Wong, D. W. S., & Denny, J. (2017). Big Data Science: Opportunities and Challenges to Address Minority Health and Health Disparities in the 21st Century. Ethnicity & disease, 27(2), 95–106. https://doi.org/10.18865/ed.27.2.95
1. Define Objectives and Scenarios:
* Objective Setting: Clearly define the objectives of the impact assessment, such as evaluating model performance in the context of fairness and impact on underrepresented demographic groups, identifying potential biases, or assessing business impact on underrepresented demographic groups.
* Scenario Generation: Develop a set of realistic scenarios that represent different use cases, edge cases, and potential challenges the model may encounter in production. 
2. Synthetic Data Generation:
* Data Synthesis: Generate synthetic datasets that mimic the characteristics and distributions of real-world data. Ensure that synthetic data covers a wide range of scenarios, has ample representation of various demographic groups, and includes relevant features and patterns observed in actual data.
3. Model Evaluation:
* Model Testing: Apply the model to synthetic data to simulate real-world predictions and outcomes. Evaluate model performance using predefined metrics and benchmarks.
* Bias Detection: Assess potential biases in model predictions by analyzing outcomes across different demographic groups or sensitive attributes. Use fairness metrics and techniques to identify and mitigate biases.
4. Risk Assessment:
* Risk Identification: Identify potential risks or vulnerabilities associated with model predictions and decision-making processes. Consider ethical, legal, and operational risks that may arise from model deployment.
* Impact Analysis: Assess the potential impact of model errors or failures on stakeholders, customers, and the organization. Quantify risks and prioritize mitigation strategies based on severity and likelihood.
5. Sensitivity Analysis:
* Parameter Variation: Conduct sensitivity analysis by varying model parameters, hyperparameters, or input features to understand their impact on model predictions. Adopt a more granular approach by conducting sensitivity analysis on racial and demographic subgroups to understand how model predictions change for such groups. Identify robustness thresholds and determine how changes in parameters affect model performance and stability.
6. Validation and Iteration:
* Cross-Validation: Validate model performance on synthetic data using cross-validation techniques to ensure robustness and generalization.
* Iterative Refinement: Iterate on model development based on insights gained from impact assessment. Refine model architecture, feature engineering, or training strategies to address identified risks and improve performance.
7. Documentation and Reporting:
* Results Documentation: Document findings from the impact assessment, including model evaluation results, risk assessments, and mitigation strategies.
* Recommendations: Provide recommendations for model improvement, risk mitigation, and deployment strategies based on assessment outcomes.
* Communication: Communicate assessment results and recommendations to relevant stakeholders, including data scientists, business leaders, and compliance officers.
8. Continuous Learning and Improvement:
* Feedback Incorporation: Incorporate feedback from the impact assessment into the model development process. Continuously monitor model performance in production and refine strategies based on real-world feedback and data.

# Model Deployment and Modeling
Deploying a model validates the feasibility and effectiveness of the developer's solution, enabling them to make a tangible impact by solving practical problems and delivering value to users or stakeholders. Developers must consider equity throughout the deployment process, from initial training to final implementation in production environments. Deploying equitable machine learning models involves validating the solution's feasibility and effectiveness and assessing its potential impact on diverse user groups. 

## Ethical Infrastructure
Deployment platforms can support an ethical infrastructure with a Responsible AI dashboard that helps analyze algorithms and data for bias and solutions to mitigate them. 
Of widely used deployment platforms  (listed below), some, such as Microsoft Azure Machine Learning and Hugging Face, support ethical deployment by integrating a responsible AI toolkit to address fairness and transparency:
1. TensorFlow Serving: TensorFlow Serving is designed for serving machine learning models in production environments. It allows developers to deploy models trained with TensorFlow, ensuring a seamless transition from development to deployment. TensorFlow Serving supports versioning and can handle multiple model versions simultaneously, facilitating model management and updates.
2. TensorFlow Extended (TFX): TFX is an end-to-end platform for deploying production-ready machine learning models. It provides components for every stage of the machine learning lifecycle, including data validation, model training, and serving. TFX supports model versioning and allows for integrating fairness and explainability tools.
3. AWS SageMaker: Amazon SageMaker is a comprehensive machine learning platform offered by AWS. It streamlines the entire machine learning workflow, from model development to deployment. SageMaker allows for easy model versioning, A/B testing, and monitoring. It also provides tools for model explainability, which is essential for understanding and mitigating biases.
4. Microsoft Azure Machine Learning: Azure Machine Learning is a cloud-based service that facilitates the end-to-end machine learning lifecycle. It supports deploying models as web services and provides tools for monitoring, versioning, and managing models. Azure also includes responsible AI capabilities to address fairness, interpretability, and transparency.
5. Google AI Platform: Google AI Platform is a cloud-based service for building, deploying, and managing machine learning models on Google Cloud. It supports the deployment of models trained with TensorFlow, scikit-learn, and other frameworks. It facilitates model versioning, monitoring, and model explainability.
6. Hugging Face Transformers: Hugging Face provides the Transformers library, which allows for easy deployment of pre-trained models for natural language processing tasks. The platform supports model versioning and has become popular for its simplicity and extensive model repository.
7. Docker and Kubernetes: Containerization tools like Docker and orchestration platforms like Kubernetes can provide flexibility and scalability in deploying machine learning models. Containers encapsulate models and dependencies, simplifying deployment across different environments.
When choosing a deployment platform for ethical model management, development teams should consider factors such as ease of use, integration with ethical AI tools, support for model explainability, and the ability to monitor and audit model performance. 

## Alerts and Monitoring:
Automated alerts, data drift monitoring, periodic audits, and performance metric monitoring are critical components of maintaining the effectiveness, reliability, and fairness of machine learning models in production environments. Below is a detailed guide on each aspect.
* Automated Alerts: The purpose of automated alerts is to quickly identify and address issues with model performance or unexpected behavior[^10]. Set up automated alerts for significant changes in key metrics (e.g., accuracy, precision, recall) or model outputs. Monitor input data for anomalies or unexpected patterns. Integrate alerts into communication channels for immediate attention.
[^10]:  Cohen, O. (n.d.). A Comprehensive Guide on How to Monitor Your Models in Production. Neptune.ai. Retrieved February 19, 2024, from https://neptune.ai/blog/how-to-monitor-your-models-in-production-guide
* Data Drift Monitoring: The purpose of data drift monitoring is to detect changes in the distribution of input data over time, which can impact model performance[^11]. Regularly compare new data distributions with the training data distribution. Use statistical methods or machine learning techniques to detect data drift. When significant drift is identified, trigger alerts or retraining processes.
[^11]:  Detect data drift on datasets (preview) - Azure Machine Learning. (2023, August 8). Microsoft Learn. Retrieved February 19, 2024, from https://learn.microsoft.com/en-us/azure/machine-learning/how-to-monitor-datasets
* Periodic Audits: The purpose of periodic audits is to systematically review and evaluate model behavior against ethical and performance standards. Conduct regular audits of model outputs and predictions. Assess fairness, interpretability, and compliance with ethical guidelines. Involve diverse stakeholders, including ethicists, in the audit process.
* Performance Metric Monitoring: Performance metric monitoring aims to track the model's performance over time and identify degradation or improvements. Continuously monitor key performance metrics based on business objectives. Set up dashboards to visualize and analyze model performance metrics. Establish thresholds for acceptable performance and trigger alerts when thresholds are breached.

# Model Explanation
Model explanation, also known as model interpretability or explainability, refers to understanding and interpreting how a machine learning model makes predictions or classifications; it is a way to gain insights into model behavior, identify important features, and build trust in the model's predictions. By understanding how a model makes predictions or classifications, stakeholders can gain insights into its behavior and identify potential biases or disparities. 

## Document the Decisions in Model Development
Documenting potential biases and diagnosing where they arise supports fairness and ethics goals for machine learning models by making the decisions and limitations of the algorithm more transparent. The following structured approach to document potential biases can be applied:
* Document preprocessing steps that may inadvertently introduce biases (e.g., normalization, imputation techniques)
* Identify features that may be proxies for sensitive attributes (e.g., gender, race) and prone to introducing biases. Document decisions related to the inclusion or exclusion of such features in the model.
* Document the choice of algorithms and their potential biases (e.g., models trained on biased datasets, biased loss functions) and note any hyperparameter settings that may amplify or mitigate biases.
* Document efforts to address class imbalances and potential impacts on model fairness and note any techniques used to mitigate biases during training.
* Document the choice of evaluation metrics, consider whether they are appropriate for all relevant groups, and be aware of metrics that may mask disparities or unfairly advantage certain groups.
* Document potential biases that may arise in the deployment environment (e.g., changes in user behavior, evolving data distributions). Consider any biases introduced during the deployment of models in specific applications
* Document biases that may arise in user feedback and consider their potential impact on model improvement efforts
* Document how the model aligns with ethical guidelines and principles established by the organization and identify ethical concerns and potential societal impacts.

Transparent feature selection processes enable users and data scientists to validate the model's inputs and challenge any unjust or discriminatory patterns that may emerge. Some feature importance techniques are:
* Permutation Importance: Assess the impact of shuffling individual features on model performance. If shuffling a feature significantly reduces model performance, that feature is considered important.
* Feature Importance from Tree-Based Models: Tree-based models (e.g., decision trees, random forests, gradient boosting) naturally provide feature importance scores based on the contribution of each feature to the model's splits.
* LASSO (L1 Regularization) Coefficients: In linear models with L1 regularization, the magnitude of the coefficients represents feature importance. Non-zero coefficients indicate important features.
* Recursive Feature Elimination (RFE): This method iteratively removes the least important features until the desired number is reached, providing a feature importance ranking.

## Document the Training Dataset:
The documentation of the characteristics of the training dataset can uncover potential biases and help stakeholders, including data scientists, policymakers, and users, gain insights into the representation of different demographic groups in the data

Document the following attributes of the training dataset[^12]:
[^12]:  Model Cards for Model Reporting. Proceedings of the Conference on Fairness, Accountability, and Transparency. (2019). ACM Conferences. https://dl.acm.org/doi/10.1145/3287560.3287596
* Composition of relevant demographic characteristics such as age, gender, race and ethnicity, geographic location, income level, and education level.
* Data Collection Methods:
  - Sampling Strategies: Document the methods used for sampling data, including any oversampling or undersampling techniques.
  - Data Sources: Specify the data sources, such as surveys, public records, or online platforms, and assess the representativeness of these sources.
* Potential Biases in Data Collection:
  - Underrepresentation: Identify any groups that may be underrepresented in the dataset and consider the implications for model generalization[^13].
  [^13]:  Norori N, Hu Q, Aellen FM, Faraci FD, Tzovara A. Addressing bias in big data and AI for health care: A call for open science. Patterns (N Y). 2021 Oct 8;2(10):100347. doi: 10.1016/j.patter.2021.100347. PMID: 34693373; PMCID: PMC8515002.(https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8515002/)
  - Sampling Bias: Document any biases introduced during the sampling process and assess their impact on the training data.
* Imbalances and Disparities:
  - Class Imbalances: Note if there are imbalances in the distribution of demographic classes, especially this is relevant for classification tasks.
  - Disparities: Assess if there are disparities in the quantity of data available for different demographic groups.
* Data Privacy and Ethics:
  - Privacy Considerations: Ensure compliance with privacy regulations and document any steps taken to protect sensitive demographic information.
  - Ethical Considerations: Document ethical considerations related to using demographic data, particularly when dealing with vulnerable or marginalized groups.
Developers should adopt the following practices as they work with the dataset to ensure clear documentation as it evolves:
* Documentation Format:
  - Metadata: Include metadata that summarizes the training dataset's demographic composition.
  - Visualizations: Use visualization techniques such as bar charts, pie charts, or heatmaps to illustrate the distribution of demographics.
  - Textual Description: Provide a written description of key findings and considerations related to the demographics of the dataset.
* Adopt Version Control: Implement version control for demographic documentation to track changes over time. Update documentation as the dataset evolves or as new information becomes available.
* Stakeholder Involvement: Seek input from diverse stakeholders, including ethicists, domain experts, and community representatives, in the discussion and documentation process. Communicate findings and potential biases to relevant parties.

## Explain How the Machine Learning Model Works:
To convey to end users how the model works, developers can follow the guidelines below[^14]. Transparent communication about the workings of a machine learning model is crucial from an equity perspective to build trust and accountability among end users and stakeholders. Developers can achieve this by clearly explaining the model's decision-making process using non-technical language and visual aids, while being transparent about the data used, including biases and limitations. 
[^14]:  Mastitsky, S. (2020, November 4). So, your stakeholders want an interpretable Machine Learning model? Towards Data Science. Retrieved February 19, 2024, from https://towardsdatascience.com/so-your-stakeholders-want-an-interpretable-machine-learning-model-6b13928892de
Document the following attributes to document how the machine learning model works:
* Model Architecture: Briefly describe the type of machine learning model employed (e.g., regression, classification, neural network).
* Training Process: Explain how the model was trained using historical data to learn patterns and relationships.
* Input Features:
  * Identification: List and describe the input features used by the model. Specify which features the model considers as significant for predictions.
  * Data Representation: Explain how input data is represented and processed by the model (e.g., encoding, scaling).
* Prediction Mechanism: Describe how the model makes predictions based on new input data.
* Key Components:
  * Feature Importance: If applicable, discuss which features the model considers most important in making predictions.
  * Weights and Coefficients: If relevant (e.g., linear models), discuss the weights or coefficients assigned to each feature.
* Explainability Techniques:
  * Model Interpretability: Describe any techniques used to enhance the interpretability of the model (e.g., SHAP values, LIME).
  * Visualization Tools: If applicable, mention any visualizations or tools used to explain the model's decisions.
* Learning from Data: Explain whether the model is capable of learning and adapting to changes in input data.

* Limitations and Assumptions:
  * Domain Constraints: Highlight any limitations or constraints within the problem domain the model may encounter.
  * Assumptions: Clearly state the model's assumptions during the prediction process.
* Ethical Considerations:
  * Bias Mitigation: Describe measures taken to mitigate biases in the model's predictions.
  * Fairness and Accountability: Address ethical considerations related to fairness and accountability in model predictions.
  * Feedback Loops: Explain how user feedback is incorporated to improve model performance.
  * User-Friendly Outputs: Detail efforts made to present model outputs in a user-friendly and understandable manner.
* Continuous Improvement: Explain how the model's performance is monitored and outline plans for iterative improvements and updates based on ongoing evaluations.

## Explain AI Product Use Cases:
An AI product is only as good as its usability and the ease with which users can interact with it[^15]. Developers can use the following guidelines to ease users' adoption.
1. User Onboarding: Provide a user-friendly setup process, guiding users through the initial steps to use the AI product. Offer tutorials or guides explaining key features and functionalities and provide customer support for end users.
2. Input Data Preparation: Specify the required format for input data, ensuring users understand how to structure the data. Implement validation mechanisms to catch errors in input data.
3. Parameter Tuning: Identify and communicate parameters that users can tune based on their needs. Provide default settings but allow customization for diverse use cases.
4. Feedback Mechanisms: Establish channels for users to provide feedback on the AI product's performance. Encourage users to report issues or suggest improvements. Stay attuned to evolving user needs and adapt the product accordingly.
5. Monitoring and Analytics: Provide users with dashboards displaying key performance metrics. Enable users to monitor the AI product's performance over time.
6. Adaptability to Data Changes: Implement mechanisms to detect and alert users to changes in the input data distribution. Provide guidance on adapting the model to new data.
7. Scaling and Resource Management: Offer guidelines for scaling the AI product as user demands grow. Provide recommendations for resource allocation and optimization.
8. Integration with Existing Systems: Provide clear documentation and APIs for seamless integration with other systems. Ensure compatibility with common data formats and protocols.
9. Security and Privacy Considerations: Outline security measures in place to protect user data and maintain privacy. Educate users on best practices for secure usage. 
10. Version Control and Updates: Implement a versioning system for the AI product to manage updates. Communicate changes, improvements, and potential impacts with each version.

## Model Retraining
Model retraining is updating a machine learning model with new data or refining its parameters to ensure that it remains accurate and effective over time. Equity-aware practices must drive this process. 

### Bias Detection Monitoring in New Data Sets and Features
Monitoring bias detection in new datasets or features is essential for maintaining fairness and transparency in AI systems. The steps outlined below serve as a useful framework for monitoring bias detection[^16]:
* Model Comparison with Prior Versions: Continuously track performance metrics (e.g., accuracy, precision, recall) for each model version. Compare the performance of new models with previous versions to assess improvements or regressions.
* Versioning:
  * Unique Identifiers: Assign unique identifiers to each model version to facilitate tracking and management.
  * Version Control Systems: Utilize version control systems (e.g., Git) to manage changes to model code, configurations, and data preprocessing steps.
  * Model Metadata: Store metadata for each model version, including training data, hyperparameters, and evaluation results.
* Rollback Mechanisms:
  * Automated Rollback: Implement automated rollback mechanisms triggered by performance degradation or validation failures. Rollback to the previous stable version to ensure uninterrupted service and mitigate risks associated with model regressions.
  * Manual Intervention: Provide the option for manual intervention to initiate rollbacks based on human judgment or specific criteria.
* Incremental Training:
  * Data Accumulation: Accumulate new data continuously or periodically to update models with the latest information. Retraining Strategies: Develop strategies for incremental training, such as online learning or mini-batch updates, to incorporate new data while minimizing computational resources.
  * Transfer Learning: Leverage transfer learning techniques to efficiently adapt pre-trained models to new data domains or tasks.
* A/B Testing and Experimentation: Conduct A/B tests to compare the performance of new model versions against baseline or existing models. Use experimentation frameworks to systematically evaluate changes and iterate on model improvements.
* Automated Pipelines: Set up Continuous Integration and Deployment (CI/CD) pipelines to automate model training, testing, and deployment processes. Ensure that each code commit triggers automated tests and validation checks before deployment.
* Monitoring and Alerting:
  * Performance Monitoring: Continuously monitor model performance in production, including latency, throughput, and accuracy.
  * Anomaly Detection: Implement anomaly detection mechanisms to detect deviations from expected behavior and trigger alerts for potential issues.
* Documentation and Communication:
  * Change Logs: Maintain detailed change logs documenting modifications made to each model version.
  * Communication Channels: Establish communication channels for notifying stakeholders about model updates, rollbacks, and performance changes.
* Stakeholder Involvement: Involve diverse stakeholders, including data scientists, engineers, product managers, and business analysts, in the model management process. Foster collaboration and knowledge sharing to ensure alignment with business goals and user needs.

## Output Adjustment and Interpretation
Output adjustment and interpretation in machine learning refer to techniques used to modify or interpret model predictions to make them more equity-focused, less biased, meaningful, actionable, and understandable. This section covers the potential impact assessment of the output before human interpretation and contextualization of results using an equity-driven framework.

### Potential Impact Assessment of Output
This testing phase allows developers to evaluate the model's performance in real-world scenarios and identify any biases, disparities, or unintended consequences that may arise. Three testing methods can be used [^17]:

* The invariance test defines input changes that are expected to leave model outputs unaffected. A common method for testing invariance is related to data augmentation. It involves pairing up modified and unmodified input examples and seeing how much this affects the model output.
* A directional expectation test is run to check how a change in the input distribution changes the expected output. An example is testing assumptions about the number of bathrooms or property size when predicting house prices. A higher number of bathrooms should mean a higher price prediction. Seeing a different result might reveal wrong assumptions about the relationship between our input and output or the distribution of our dataset.
* The minimum functionality test helps developers decide whether individual model components behave as expected. Overall, output-based performance can conceal critical upcoming issues in the model; therefore, developers must run this test to reveal this issue. A few ways to do this are:
  * create samples that are “very easy” for the model to predict to see if they consistently deliver these types of predictions; 
  * test data segments and subsets that meet specific criteria; and
  * test for failure modes identified during manual error analysis.

### Monitor Results and Contextualize Results
Continuous monitoring allows organizations to track the model's performance over time and detect any changes or deviations from expected outcomes. This contextualization helps ensure that the model's outputs are interpreted and acted upon in a manner that upholds equity [^18]. The following blueprint can be used to guide this stage of the ML development and production process:
* Define key performance indicators (KPIs) based on project goals and objectives, such as accuracy, precision, recall, F1 score, or business-specific metrics. Identify additional metrics that provide context to model performance, such as fairness metrics (e.g., disparate impact) or interpretability metrics (e.g., feature importance).
* Set baseline values and acceptable ranges or thresholds for KPIs based on business requirements, regulatory constraints, or industry standards; then use them to compare against model performance.
* Implement automated processes to monitor model performance in real-time or at regular intervals. Set up alerts or notifications for deviations from expected performance or when thresholds are breached.
* Interpret model performance in the context of broader business objectives and strategies. Relate model outcomes to business impact, such as revenue, customer satisfaction, or operational efficiency. Involve domain experts to provide insights and interpret results based on their domain knowledge. 
* Conduct comparative analyses. Analyze trends in model performance over time to identify patterns or changes. Compare current results with historical data to assess progress or detect anomalies. Benchmark model performance against industry standards, competitor models, or state-of-the-art approaches. 
* Undertake a root cause analysis.  Investigate potential factors contributing to changes or deviations in model performance. Consider data quality issues, changes in the input data distribution, or model drift. Debug model predictions to understand the reasoning behind specific outcomes. Evaluate model behavior under different conditions or edge cases.
* Incorporate user feedback and stakeholder input to assess model performance and relevance. Use feedback loops to improve model outcomes based on user experiences iteratively. Translate feedback into actionable improvements or adjustments to the model architecture, features, or training data.
* Document monitoring results, contextual analysis, and actions taken in a transparent and accessible manner. Communicate findings to relevant stakeholders through regular reports or dashboards.

## Maintenance

### Avoid Bias Evolving in the Learning Model Over Time
Bias in machine learning models refers to systematic errors introduced by algorithms or training data that lead to unfair or disproportionate predictions for specific groups or individuals. Such biases can arise due to historical imbalances in the training data, algorithm design, or data collection. To prevent bias from evolving in the ML model over time, use several bias assessment metrics and methodologies, including:
* Disparate Impact Analysis: This technique examines the disparate impact of an AI model's decisions on different demographic groups. It measures the difference in model outcomes for various groups and highlights potential biases.
* Fairness Metrics: Researchers and practitioners have developed different fairness metrics to measure bias in machine learning models, including Equal Opportunity Difference, Disparate Misclassification Rate, and Treatment Equality [^19]. These metrics help assess how fairly the model treats different groups.
* Post-hoc Analysis: This involves examining an AI system’s decisions after deployment to identify instances of bias and understand its impact on users and society. [^20]

### Data Retention and Deletion Strategy for Handling Ethical and Privacy Issues
Data retention is the storing of information for a specific period, and it helps businesses reduce costs, legal risks, and security threats to users and organizations. To successfully implement a data retention policy, incoming and existing data must be properly classified and organized based on risk level and intended use.
Privacy regulations require two types of data deletion processes: 
* Request-based deletion responds to individual requests.
* Data retention and purge are focused on deleting data according to an organization’s schedules and internal process guidelines. These processes require organizations to operate a dedicated data retention governance team to provide data retention and purge oversight to address ethical and privacy issues. 

### Continuous Fairness Monitoring of Machine Learning Models
Continuous fairness monitoring is increasingly becoming a key focus in machine learning due to demands for equity and diversity in AI products. ML practitioners generally regard monitoring for drift as an early warning system for performance issues and evaluating models with fairness metrics as a solution for assessing bias in a trained model. A trained model that is fair can become unfair after deployment due to the same model drift that causes performance issues[^21]. 

Quantile Demographic Drift (QDD) is a method to measure and monitor fairness in machine learning models over the model lifecycle[^22]. This method involves a novel model bias quantification metric that uses quantile binning to measure differences in the overall prediction distributions over subgroups. QDD is incorporated into a continuous model monitoring system called FairCanary, that reuses existing explanations computed for each prediction to compute explanations for the QDD bias metrics quickly.

### Practical Ways of Mitigating Biases in the Use of the Output
To mitigate biases in the output, AI developers can include a “model facts label” (a 1-page of relevant and actionable information) for front-line users that indicates how, how not, and when to use the output.

Another practical technical way to mitigate bias is to use equalized odds post-processing. This technique solves a linear program to find probabilities of changing output labels to optimize equalized odds[^23].

[^23]:  aif360.algorithms.postprocessing — aif360 0.1.0 documentation. (n.d.). aif360. Retrieved February 19, 2024, from https://aif360.readthedocs.io/en/v0.2.3/modules/postprocessing.html
[^22]:  Avijit Ghosh, Aalok Shanbhag, Christo Wilson.FairCanary: Rapid Continuous Explainable Fairness. (2021, June 13). arXiv. Retrieved February 19, 2024, from https://arxiv.org/abs/2106.07057
[^21]:  Paka, A. (2022, August 5). FairCanary: Rapid Continuous Explainable Fairness. Fiddler AI. Retrieved February 19, 2024, from https://www.fiddler.ai/blog/faircanary-rapid-continuous-explainable-fairness
[^20]:  Buhl, N. (2023, August 8). Mitigating Model Bias in Machine Learning. Encord. Retrieved February 19, 2024, from https://encord.com/blog/reducing-bias-machine-learning/
[^19]:  Tutorial #1: bias and fairness in AI. (2019, August 19). Borealis AI. Retrieved February 21, 2024, from https://www.borealisai.com/research-blogs/tutorial1-bias-and-fairness-ai/
[^18]:  Cohen, O. (n.d.). A Comprehensive Guide on How to Monitor Your Models in Production. Neptune.ai. Retrieved February 19, 2024, from https://neptune.ai/blog/how-to-monitor-your-models-in-production-guide
[^17]:  How to Test Machine Learning Models. (2022, December 7). Deepchecks. Retrieved February 19, 2024, from https://deepchecks.com/how-to-test-machine-learning-models/
[^16]:  McKenna, M. (n.d.). Bias in AI: How to Mitigate Bias in AI Systems. Toptal. Retrieved February 29, 2024, from https://www.toptal.com/artificial-intelligence/mitigating-ai-bias
[^15]:  How to Show the Value of Your AI Project to Stakeholders. (2023, August 16). LinkedIn. Retrieved February 19, 2024, from https://www.linkedin.com/advice/0/how-do-you-show-value-your-ai-stakeholders

For complete information, practical guides and resources on post development please visit our website(link).
