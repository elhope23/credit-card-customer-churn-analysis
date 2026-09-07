# Project XYZ

This project aims to analyse the factors contributing to whether a bank's credit card customer will churn or not. Beyond that, this project aims to present ethical considerations as a key component of this analysis.

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)

## Dataset Content

* The dataset I have chosen is [Credit Card Customers - Predicting Churning Customers](https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers/data) - a **CC0: Public Domain** dataset sourced from Kaggle. 

* The data includes the following columns:

| **Column Name** | **Description** |
| --------------- | ---------------- |
| `CLIENTNUM` | Unique client number identifier for the customer holding the account |
| `Attrition_Flag` | Whether the customer is an `Existing Customer` or an `Attrited Customer` |
| `Customer_Age` | Customer age in years |
| `Gender` | The customer's gender |
| `Dependent_count` | Number of dependents the customer has |
| `Education_Level` | The highest level of education a customer holds |
| `Marital_Status` | A customer's marital status |
| `Income_Category` | Annual income of a customer broken down into categories |
| `Card_Category` | The card product the customer holds |
| `Months_on_book` | The number of months the customer has been with the bank |
| `Total_Relationship_Count` | The total number of products held by the customer |
| `Months_Inactive_12_mon` | The number of months the customer has been inactive over the past 12 months |
| `Contacts_Count_12_mon` | The number of contacts with the bank in the last 12 months |
| `Credit_Limit` | The credit limit on a customer's credit card |
| `Total_Revolving_Bal` | The total revolving balance a customer has on their credit card |
| `Avg_Open_To_Buy` | The mean amount of unused or available credit a customer has on their credit card or revolving credit account over a one-year period |
| `Total_Amt_Chng_Q4_Q1` | The change in transaction amount (Q4 over Q1) |
| `Total_Trans_Amt` | The total transaction amount over the last 12 months |
| `Total_Trans_Ct` | The total number of transactions over the last 12 months |
| `Total_Ct_Chng_Q4_Q1` | The change in the number of transactions (Q4 over Q1) |
| `Avg_Utilization_Ratio` | The credit card utilisation ratio, which is the percentage of a customer's revolving credit that they use |

## Business Requirements

* This project addresses the following business problem: a bank manager has observed a rising rate of customers leaving their credit card services and wants to identify at-risk customers before they leave, so that the bank can proactively intervene with improved service and hopefully prevent the customers leaving.

* The aim of this project is to is to:
    * Identify which customer characteristics and behaviours are most strongly linked to attrition.
    * Evaluate whether a predictive model can flag at-risk customers in advance.

* The business requirements are as follows (each linked to a hypothesis tested as part of this project):

| **Business Requirement** | **Description** | **How is it addressed in the project?** |
| ------------------------ | --------------- | --------------------- |
| **Understand customer spending and engagement behaviour** | The bank will need to understand customer spending and engagement habits in order to identify any customers who are disengaged (which could be linked to attrition) | This is addressed in **Hypothesis 1**, which tests the correlation of transaction amount and transaction count, alongside exploratory data analysis, which identifies different patterns for existing and attrited customers |
| **Determine whether financial factors influence attrition** | The bank needs to know whether customer attrition is linked to broader factors like a customer's income bracket to understand who might be at risk | This is addressed in **Hypothesis 2** |
| **Identify behavioural warning signs that precede attrition** | The bank needs to know if there are indicators in how a customer acts that might suggest they are likely to leave - for instance, the amount owed on a credit card that is unpaid at the end of the billing cyclce (Revolving Balance) | This is addressed in **Hypothesis 3** |

## Hypotheses

* The hypotheses that will be examined are:

| **Hypothesis** | **Hypothesis Description** |
| -------------- | -------------------------- |
| **H1** | Customers who make more transactions tend to spend more |
| **H2** | Annual income category is linked to whether a customer leaves the bank |
| **H3** | Customers who leave the bank have a different revolving balance than those who remain |

* They will be validated as follows:

| **Hypothesis** | **How to Validate** |
| ---- | -----|
| **H1** | Test for Normality: Shapiro-Wilk Test, Q-Q Plot<br>Correlation Tests: Spearman and Pearson<br>Visualisation: Seaborn Regplot with Linear Regression Line and LOWESS Regression Line |
| **H2** | Visualisation: Countplot<br>Statistical Test: Chi-Squared Test of Independence |
| **H3** | Preliminary Descriptive Statistics: Mean and Median<br><br>Test for Normality: Q-Q Plot <br><br>Statistical Test: Mann-Whitney U Test |

## Project Plan

* Outline the high-level steps taken for the analysis.
* How was the data managed throughout the collection, processing, analysis and interpretation steps?
* Why did you choose the research methodologies you used?

## The rationale to map the business requirements to the Data Visualisations

* List your business requirements and a rationale for mapping them to the Data Visualisations

## Analysis techniques used

* List the data analysis methods used and explain limitations or alternative approaches.
* How did you structure the data analysis techniques? Justify your response.
* Did the data limit you, and did you use an alternative approach to meet these challenges?
* How did you use generative AI tools to help with ideation, design thinking and code optimisation?

## Generative AI

* I very much wanted to solidify what I'd learned myself when completing this project, so treated AI as an "assistant" to support specific troubleshooting issues or processes I was unfamiliar with. Examples of when I did this are outlined in my project under *"Troubleshooting Issues"* and *"Notes on Process"*.

## Ethical Considerations

* Any ethical considerations I made at key instances in my project have been clearly outlined in Markdown cells labelled as *Ethical Considerations*.

### Data Privacy and Anonymisation
* Customer-identifying information was anonymised at the beginning of this project (in **Stage 1 - Anonymisation**) with salting and hashing applied to the `CLIENTNUM` values before any analysis took place. This meant that no individual customer could be re-identified from the dataset used in this project, particularly given the additional step I made to `.gitignore` the original, non-anonymised file.

### Protected Characteristics and Direct Discrimination Risk
* The original dataset included several protected characteristics under the UK Equality Act 2010. I chose to deliberately exclude these from the list of features used to train the predictive models in **Stage 4 - Machine Learning**. Even though, as I outlined in a *Ethical Considerations* section in this notebook, this predictive model is for educational purposes only and should not be used on real customer data, I felt that it was important that we should not be using legally protected characteristics for any model used to determine which customers should receive differentiated treatment.

### Proxy Bias
* This is a major topic within banking machine learning. Even if you exclude protected characteristics from a model, there might be correlations that allow a model to essentially develop biases without explicitly being trained with these characteristics as features.
* In my project, I have acknowledged this limitation but have not been able to deliver a full audit: for instance, I know that I could perform disparate impact testing on different demographic subgroups - however, this felt out of reach as a possibility given the timeframe and also where my current skill levels sit, particularly with regards to machine learning. It would be very much something I'd like to learn about in the future. 

### Encoding Choices
* In **Stage 4 - Machine Learning**, I made the decision *not* to ordinally encode features like `Education_Level` and `Income_Category`. The reason I did this (and simply one-hot encoded them) is because I thought that to do so would impose biases around education attainment and income. I didn't think it was right to introduce a ranking that suggested that being in one category was "better" than another.

## Legal and Social Implications

### GDPR and Data Protection
* As I already mentioned in my **Ethical Considerations** section above, I already chose to analyse the dataset for PII and to anonymise the `CLIENTNUM` values to ensure that any customer could not be re-identified. 
* Under **Recital 26** of GDPR, data is classed as anonymous if re-identification is not "reasonably likely" and the transformation of the data from personal to anonymous must be permanent and irreversible - I hope that within the context of my project I have done this by ensuring the original raw dataset is excluded from my GitHub repository and cannot be called by running any of the Jupyter Notebooks. In reality, the raw dataset *is* available on Kaggle, but I wanted to ensure that my project handled the data as sensitively as possible.

### Social Implications
* Attrition models risk compounding existing financial vulnerabilities rather than just identifying them. Customers that have lower incomes or higher revolving balances may be more likely to be flagged by a model. However, these are the customers who most need access to banking services, support and fair treatment. The real-world impact of "model optimising" might be deprioritising customers that a bank has the strongest social responsibility towards. 
* How a prediction is used matters. For example, offering a customer a helpful retention benefit is very different from reducing their services, increasing fees, or restricting access because a model predicts they are likely to leave. Targeting vulnerable customers with aggressive marketing, higher-cost products, or incentives that encourage additional borrowing can cause harm.

### Scope and Limitations
* This project is explicitly educational in nature.
* **It has not been validated for, nor is it intended for, real-world deployment**. 
* Any real-world application of a similar predictor would need formal fairness auditing, legal review under UK GDPR and also the UK Equality Act 2010 and oversight mechanisms that have not been implemented as part of this educational project.

## Dashboard Design (optional)

* Feel free to delete this section if this is a data visualisation only (unit 1 or 2) project submission.
* List all dashboard pages and their content, either blocks of information or widgets, like buttons, checkboxes, images, or any other item that your dashboard library supports.
* Later, during project development, you may revisit your dashboard plan to update a feature (for example, at the beginning of the project, you were confident you would use a given plot to display an insight, but later you used another plot type).
* How were data insights communicated to technical and non-technical audiences?
* Explain how the dashboard was designed to communicate complex data insights to different audiences. 

![Dashboard Wireframe](images/dashboard-wireframe-bank-churners.png)

## Unfixed Bugs

* Please list any unfixed bugs and explain why they were not fixed. This section should include shortcomings of the frameworks or technologies used. Although time can be a significant variable to consider, paucity of time and difficulty understanding implementation are not valid reasons to leave bugs unfixed.
* Did you recognise gaps in your knowledge, and how did you address them?
* If applicable, include evidence of feedback received (from peers or instructors) and how it improved your approach or understanding.

## Development Roadmap

* What challenges did you face, and what strategies were used to overcome these challenges?
* What new skills or tools do you plan to learn next based on your project experience? 

## Deployment (optional)

* If this is a Unit 3 Streamlit, Power BI or Tableau Public project, then you can include a link here and explain how you hosted the dashboard.

### Heroku (optional)

* This section is necessary only if you are deploying a Streamlit app to Heroku as part of your submission for units 2 and 3. 
* The App live link is: https://YOUR_APP_NAME.herokuapp.com/ 
* Set the `.python-version` Python version to a [Heroku-22](https://devcenter.heroku.com/articles/python-support#supported-runtimes) stack currently supported version.
* The project was deployed to Heroku using the following steps.

1. Log in to Heroku and create an App
2. From the Deploy tab, select GitHub as the deployment method.
3. Select your repository name and click Search. Once it is found, click Connect.
4. Select the branch you want to deploy, then click Deploy Branch.
5. The deployment process should happen smoothly if all deployment files are fully functional. Click the button Open App at the top of the page to access your App.
6. If the slug size is too large, then add large files not required for the app to the `.slugignore` file.

## Main Data Analysis Libraries

* Here you should list the libraries you used in the project and provide an example(s) of how you used these libraries.

## Credits

* In this section, you need to reference where you got your content, media and extra help from. It is common practice to use code from other repositories and tutorials; however, it is important to be very specific about these sources to avoid plagiarism. 
* You can break the credits section into Content and Media, depending on what you include in your project. 

### Content 

- The text for the Home page was taken from the Wikipedia Article A
- Instructions on how to implement form validation were taken from a [Specific YouTube Tutorial](https://www.youtube.com/)
- The icons in the footer were taken from [Font Awesome](https://fontawesome.com/)

### Media

- The photos used on the home and sign-up page are from This Open-Source site
- The images used for the gallery page were taken from this other open-source site



## Acknowledgements (optional)

* Thank the people who supported this project.
