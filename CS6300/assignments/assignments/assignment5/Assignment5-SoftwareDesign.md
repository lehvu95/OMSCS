# Assignment 5: Software Design

# Background

A fellow classmate, George P. Burdell, is looking for a new job in the US after graduation. As it can be complicated to compare job offers with benefits, in different locations, and other aspects beyond salary, he would like an app to help with this process and has asked for your assistance in creating a simple, single-user job offer comparison app.  As a first step, he would like you to create an initial design for the app, expressed in UML, based on a set of requirements he provided. **This deliverable thus consists of (1) a UML design document and (2) a design description document**. 
 
**Important:** Please note that, although this assignment is only worth a small percentage of your overall grade, it is an important one because it will be used as the basis for your first group deliverable, which consists of sharing and discussing your design with your teammates. Therefore, doing a poor job in this assignment will likely penalize your group performance and ultimately hurt your collaboration grade.
# Requirements

1. When the app is started, the user is presented with the main menu, which allows the user to (1) enter or edit current job details, (2) enter job offers, (3) adjust the comparison settings, or (4) compare job offers (disabled if no job offers were entered yet).
2. When choosing to *enter current job details, *a user will:
  1. Be shown a user interface to enter (if it is the first time) or edit all the details of their current job, which consists of:
    1. Title
    2. Company
    3. Location (entered as city and state)
    4. Cost of living in the location (expressed as an [index](https://www.expatistan.com/cost-of-living/index/north-america))
    5. Yearly salary
    6. Yearly bonus
    7. Stock Option Shares (Whole number, assumes 3-year vesting period and $1 stock value)
    8. Wellness Stipend ($0-$1200 Inclusive annually)
    9. ***Life Insurance (Percentage of Yearly Salary as an integer: 0 – 10 inclusive)***
    10. Personal Development Fund ($0 to $6000 inclusive annually)

  2. Be able to either save the job details or cancel and exit without saving, returning in both cases to the main menu.
3. When choosing to *enter job offers, *a user will:
  1. Be shown a user interface to enter all the details of the offer, which are the same ones listed above for the current job.
  2. Be able to either save the job offer details or cancel.
  3. Be able to (1) enter another offer, (2) return to the main menu, or (3) compare the offer (if they saved it) with the current job details (if present).
4. When *adjusting the comparison settings, *the user can assign integer *weights *to:
  1. Yearly salary
  2. Yearly bonus
  3. Stock Option Shares
  4. Wellness Stipend
  5. ***Life Insurance ***
  6. Personal Development Fund
NOTE: These factors should be integer-based from 0 (no interest/don’t care) to 9 (highest interest). Default value for all weights: 1
- If no weights are assigned, all factors are considered equal.
- The user must be able to either save the comparison settings or cancel; both will return the user to the main menu.
5. When choosing to *compare job offers, *a user will:
  1. Be shown a list of job offers, displayed as Title and Company, ranked from best to worst (see below for details), and including the current job (if present), clearly indicated.
  2. Select two jobs to compare and trigger the comparison.
  3. Be shown a table comparing the two jobs, displaying, for each job:
    1. Title
    2. Company
    3. Location
    4. Yearly salary adjusted for cost of living
    5. Yearly bonus adjusted for cost of living
    6. Stock Option Shares (SOS)
    7. Wellness Stipend (WS)
    8. Life Insurance (LI)
    9. Personal Development Fund (PDF)
    10. Job Score - (JS) Calculation shown in Requirement #6
  4. Be offered to perform another comparison or go back to the main menu.
6. When ranking jobs, a job’s score is computed as the **weighted** average of:
 AYS + AYB + (SOS/3) + WS + ***(LI/100 * YS)*** + PDF
where:AYS = Yearly Salary Adjusted for cost of livingAYB = Yearly Bonus Adjusted for cost of livingSOS = Stock Option Shares (Whole number, assumes 3-year vesting period and $1 stock value) 
WS = Wellness Stipend ($0-$1200 Inclusive annually) 
LI = Life Insurance (Percentage of Yearly Salary expressed as an integer: 0 – 10 inclusive)  
PDF = Personal Development Fund ($0 to $6000 inclusive annually)
For example, if the weights are 2 for the adjusted yearly salary, 2 for the adjusted yearly bonus, 2 for SOS, and 1 for all other factors, the score would be computed as:
JS = 2/9 * AYS + 2/9 * AYB + 2/9 * (SOS/3) + 1/9 * WS + 1/9 * ***(LI/100 * YS)*** + 1/9 * PDF

For example, if the weights are 3 for the adjusted yearly salary, 3 for the adjusted yearly bonus, 4 for SOS, and 1 for all other factors, the score would be computed as:
JS = 3/13 * AYS + 3/13 * AYB + 4/13 * (SOS/3) + 1/13 * WS + 1/13 * ***(LI/100 * YS)*** + 1/13 * PDF

7. The user interface must be intuitive and responsive.
8. For simplicity, you may assume there is a *single system* running the app (no communication or saving between devices is necessary).
# Details

To create your design, you should follow the same approach that we present in the P3L2 lesson. That is, analyze the requirements (provided above) to identify and refine **(1) classes, (2) attributes, (3) operations, and (4) relationships** in your design. Just to be completely clear, **your task is to design the system, not to implement it**. At this stage, the design should be implementation neutral, and not involve constructs specific to a language or framework. For example, we are not looking for Android Activity classes.

Please note that not every requirement must be fully and directly represented in your design. For instance, at this level of detail, you do not have to show any purely GUI-specific classes. Similarly, any database support layer may be left out if it is purely doing persistence tasks (simple CRUD only) on **data and collections already fully represented in the design**. 
 
**Please also note that we are expecting to see, in your design, a class that represents the entry point to the system, and that ties the various pieces together.**

Your design should be expressed using a UML class diagram, and the level of detail of the design should be analogous to the level of detail we used throughout the **whole **P3L2 lesson. That is, do not limit your design to only the elements shown in the final video, where some of the elements shown earlier (e.g., methods) are elided for space. Specifically, **you must provide enough details for the design to be self-contained and for us to be able to assess whether the design suitably realizes all system requirements**. 

To help to make your design self-contained, you must also provide a “design description” document, in which you concisely describe, **for each of the requirements listed above**, either (1) how that requirement is realized in your design, or (2) why it does not directly affect the design and is therefore not shown. To produce this document, you must **copy the list of requirements and add your explanation for each one of them**. For example, using some partial requirements for a cash register app:

…

2. After starting the cash register, the cashier enters her name, and the total amount of money available in the till.

    To realize this requirement, I added a ‘currentCashier’ to the register class to track the signed-in cashier, and a float ‘till’ to represent the money in the till. These values are entered by the startup() method, after prompts are handled within the GUI.

…<additional requirements reflected in example UML diagram>...

16. The User Interface (UI) must be intuitive and responsive.

    This is not represented in my design, as it will be handled entirely within the GUI implementation.

The explanation in the design description should be clear enough to allow us to follow the rationale behind your design and **how it will fulfill each specified requirement, including any that are not directly depicted in your class diagram.** You can also provide in the document additional information about your design, such as assumptions or rationale for some design decisions. Use the document to review your design and ensure you have included everything necessary for your app to fill the list of requirements.

**NOTE:** A requirement that constrains application behavior cannot be completely handled by the GUI. For example, a GUI may implement the display of output, but the application determines what data to display. The design document should contain a description of the application-specific behavior.

# Submission Instructions

To submit your assignment, you should do the following:
1. Create a directory called `Assignment5` in the usual **personal GitHub repository we assigned to you**. This is an **individual assignment**; do **not** use your new team repositories.
2. Save your UML class diagram in the `Assignment5` directory as a PDF file named “`design.pdf`”.  You can use any UML tool of your choice to create your UML design, but please **do not hand draw the design**.
**Important:** Make sure to open your PDF after generating it and double-check it, as we have had a number of cases of students not realizing that the conversion to PDF had not worked as expected.  
3. Save the “design description” document in the same directory, in markdown format, and named  “`design-description.md`”.
4. Commit and push your file(s) to your remote repository.
5. On Gradescope, submit a file called `submission.txt` that contains, in two separate lines (1) yotur GT username and (2) the commit ID for your submission.  For example, the content of file `submission`.txt for George P. Burdell could look something like the following:
| `gpburdell1` |
| --- |
| `81b2f59` |

**Important:**  **As soon as you submit, your assignment will be checked** by making sure that you have the required directory structure and documents. However, we cannot automatically check your design, so **a positive response from Gradescope only indicates that we will be able to grade your assignment, and the grade you will receive is only a placeholder.You can resubmit as many times as you want before the deadline**, so you have a chance to address issues with your assignments if Gradescope finds any problem with your submission.
## PLAGIARISM

As for all other assignments, we check for plagiarism. Unfortunately, there are plagiarism cases every semester. Please keep in mind that the tools we use to identify cases of plagiarism have access to the same online resources that are available to you.
