# Loan Qualifier Application
As the name suggests, this application produces a list of qualified bank loans based upon applicant's credit score, current monthly debt, present monthly income, loan amount sought for and the value of the home s/he wants to buy.

The Starter code was supplied and the additional functionality listed below in the User Story was developed as part of this application.

---
# User Story
As a user, I need the ability to save the qualifying loans to a CSV file so that I can share the results as a spreadsheet.

---

# Acceptance Criteria

When there are no qualifying loans the program should notify the user and exit.     
When there is a list of qualifying loans:

- prompt the user to save the results as a CSV file. 
- when prompted to save the results, then should be able to opt out of saving the file.         
- when chose to save the loans, it should prompt for a file path to save the file
- when chose to save the loans, then it should save the results as a CSV file.

---

# The Application

The application **app.py** uses the following logic to accomplish the User Story and its Acceptance Criteria. Its run() function is the main function driving the application.

The run() function calls the following functions in sequence:

* load_bank_data()  
prompts the user for the bank rate file and then uses it to extract the daily bank rates  

* get_applicant_info()  
prompts the user for credit score, monthly debt, monthly income, loan amount sought for and home value

* find_qualifying_loans():   
        uses the applicant information to calculate DTI and LTV ratios. It then uses the bank rate data extracted above and the filter functions for credit score, loan size, DTI and LTV to obtain the qualifying bank loans   
* save_qualifying_loans()  
        if there are no qualifying loans, it displays a message and exits.
        if there are qualifying loans, then it prompts the user if s/he wants to save the information. If so, s/he is prompted for a file name to save it in and performs the save.

The program ends here

---

# Technologies
The application is developed using:  
* Language: Python 3.7,   
* Packages: fire 0.3.1 for CLI and questionary 1.5.2 for prompts  
* Development Environment: VS Code and Terminal, Anaconda 2.1.1 with conda 4.11.0, Jupyterlab 3.2.9  
* OS: Mac OS 12.1

---

# Installation Guide

Following are the instructions to install the application from its Github respository.

## Clone the application code from Github as follows:
1. copy the URL link of the application from its Github repository    
2. open the Terminal window and clone as follows:
    * $cd to_your_preferred_directory_where_you want_to_store_this_application
    * $git clone URL_link_that_was_copied_in_step_1_above

At this point you will have the the entire application files in the current directory as follows:

* README.md                   (this file that you are reading)
* app.py                      (the loan qualifier application)
* data                        (folder)
    - daily_rate_sheet.csv   (Bank loan rate sheet)

* qualifier                   (folder)
    - filters                (folder)
        - debt_to_income.py	(DTI filter)
        - max_loan_size.py    (Max Loan size filter)
        - credit_score.py		(Credit score filter)
        - loan_to_value.py    (LTV filter)
    - utils                  (folder)
        - calculators.py	    (financial calculators)
        - fileio.py           (file io operations)


---
 
# Usage

The following details the instructions on how to run the application.

## Setup the environment to run the application
Setup the environment using conda as follows:

3. $conda create dev -python=3.7 anaconda
4. $conda activate dev  
    if the required versions of 'fire' and 'questionary' are not installed yet, then install them using the following-
5.  $pip install ./requirements.txt 

Now you can run the application from the $ prompt

**NOTE**:
>Your $ prompt will look like __(dev) ashokpandey@Ashoks-MBP loan_qualifier_app$__ ,  with:  
    - '(dev)' indicating the activated 'dev' environment,   
    - ' ashokpandey@Ashoks-MBP ' will be different for you as per your environment, and   
    - 'loan_qualifier_app' directory is where app.py is located.  
    - '$' sign is the dollar prompt  


## Run the application
Make sure you are in the directory containing the app.py script. If not, then cd to the directory containing it. 

The following is a sample run of the application, you will use the numbers and filenames depending upon your choice. The 'data/daily_rate_sheet.csv' is the daily rate sheet file located in the data folder. This can be updated with the current rates replacing the existing values. You can have a different file but the format MUST remain identical to this file.

6.  **(dev) ashokpandey@Ashoks-MBP loan_qualifier_app$** python app.py
7.  **Enter a file path to a rate-sheet (.csv):** data/daily_rate_sheet.csv
8.  **What's your credit score?** 750
9.  **What's your current amount of monthly debt?** 200
10. **What's your total monthly income?** 4000
11. **What's your desired loan amount?** 100000
12. **What's your home value?** 200000  
    The monthly debt to income ratio is 0.05  
    The loan to value ratio is 0.50.  
    Found 15 qualifying loans  
13. **Do you want to save the Qualified Loans to a file (Default is Yes)** Yes
14. **Enter a file name to save the Qualified Loans (.csv):** qualified_loans.csv
15. **(dev) ashokpandey@Ashoks-MBP loan_qualifier_app$**

At this point, 'qualified_loans.csv' is created in the current directory with the bank loans that the applicant is qualified for. You can view it using 'excel' or any other spreadhseet accepting the 'csv' format.

---

# Contributors

Ashok Pandey - ashok.pragati@gmail.com   
www.linkedin.com/in/ashok-pandey-a7201237

---

# License

The source code is the property of the developer. The users can copy and use the code freely but the developer is not responsible for any liability arising out of the code and its derivatives.

Free individual licenses to use Anaconda, fire, questionary, VS Code, Jupyterlab, Gitlab, Github, Git

---