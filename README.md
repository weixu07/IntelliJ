
### Design-Description


1. When the app is started, the user is presented with the main menu, which allows the user to (1) enter or edit current job details, (2) enter job offers, (3) adjust the comparison settings, or (4) compare job offers (disabled if no job offers were entered yet1).

*To realize this requirement, I designed the "MainMenu" class which has corresponding operations as "enterCurrentJob", "enterJobOffers", "assignComparisonSetting", "compareJobOffers". Each operation will start up the GUIs handling the corresponding event class as "EnterCurrentJob", "EnterJobOffers", "AssignComparisonSetting", "CompareJobOffers".*

2. When choosing to enter current job details, a user will: 
  >a. Be shown a user interface to enter (if it is the first time) or edit all of the details of their current job, which consist of:
  >>i. Title
  >>ii. Company
  >>iii. Location (entered as city and state)
  >>iv. Cost of living in the location (expressed as an index )
  >>v. Yearly salary
  >>vi. Yearly bonus
  >>vii. Allowed weekly telework days (expressed as the number of days per week allowed for remote work, inclusively between 0 and 5)
  >>viii. Retirement benefits (as percentage matched)
  >>ix. Leave time (vacation days and holiday and/or sick leave, as a single overall number of days)

*To achieve this requirement, I designed the "EnterCurrentJob" which has an attribute "currentJob" as a type of "Job". The "Job" class contains the properties/attributes of job details. The "Job" has been saperated since it is common and can be used by different other class. I used compositon relationship to connect the "EnterCurrentJob" since it represent the "uses" relationship between them.*   

  >b. Be able to either save the job details or cancel and exit without saving, returning in both cases to the main menu.

*To achieve this requirement, I added two operations 'save' and 'cancel' in "EnterCurrentJob". They are going to either save the job details and return to main menu, or exit without saving and return to main menu.*


3. When choosing to enter job offers, a user will:
  >a. Be shown a user interface to enter all of the details of the offer, which are the same ones listed above for the current job.
  >
  >b. Be able to either save the job offer details or cancel.
  >
  >c. Be able to (1) enter another offer, (2) return to the main menu, or (3) compare the offer with the current job details (if present).

*To realize this requirement, I designed the "EnterJobOffers" class which responses the "enterJobOffers" operation in main menu and starts up a enter job offers GUI. It uses "Job" class to capture the details of the offer, so the relationship between them is composition as well. I added an attribute 'jobOffers' to store the entered details of job offers. Since user is able to enter more than one job offers, I used ArrayList to store them. The 'save' and 'cancel' operations are going to either save the job details or cancel without saving. The 'return' operation simply return to the main menu GUI. The 'enterAnother' operation simply replicate the user interface to enter the details of another job offer as the first job offer. Once user wants to compare job offers, it will transfer the GUI and contents to be "CompareJobOffers" class likely by clicking a naming button. The current job and job offers will be into jobOfferList: ArrayList<Job> for rank computation.*   

4. When adjusting the comparison settings, the user can assign integer weights to:
  >a. Yearly salary
  >
  >b. Yearly bonus
  >
  >c. Allowed weekly telework days
  >
  >d. Retirement benefits
  >
  >e. Leave time

*To realize this requirement, I designed the "AssignComparisonSetting" class having attributes which can store weights of Yearly salary, Yearly bonus, Allowed weekly telework days, Retirement benefits and leave time. For next step GUI design, the slide bar of each one will be friendly for users.* 

5. When choosing to compare job offers, a user will:
  >a. Be shown a list of job offers, displayed as Title and Company, ranked from best to worst (see below for details), and including the current job (if present), clearly indicated.

*To achieve this requirement, I added 'jobOffersList: ArrayList<Job>' to store all job offers include the current job and job offers entered from "EnterCurrentJob" and "EnterJobOffers" and other job contents from database. The contents and operations of "CompareJobOffers" will be in a GUI under main menu. And a 'display' method is going to list the job offers in the table format in a new GUI. Before that, 'computeRank' method calcuates the rank from best to worst using the weight inputs from "AssignComparisonSetting".*  

  >b. Select two jobs to compare and trigger the comparison.
  >
  >c. Be shown a table comparing the two jobs, displaying, for each job:
  >>i. Title
  >>ii. Company
  >>iii. Location
  >>iv. Yearly salary adjusted for cost of living
  >>v. Yearly bonus adjusted for cost of living
  >>vi. Allowed weekly telework days
  >>vii. Retirement benefits (as percentage matched)
  >>viii. Leave time

*To achieve this requirement, a 'compareTwo' method having parameters of 'jobA: Job' and 'jobB: Job' give the output of details in the table format in a new GUI. Before user choosing two jobs the 'compareTwo' mothod is inactive.*

  >d.Be offered to perform another comparison or go back to the main menu.

*To realize this requirement, I added operations 'compareAgain' and 'return'. 'compareAgain()' return from the GUI displaying the details of two jobs to GUI showing a list of job offers, so user can choose other comparsion pairs. 'Return' simply goes back to main menu.*


6. When ranking jobs, a job’s score is computed as the weighted sum of:

  >AYS + AYB + (RBP * AYS) + (LT * AYS / 260) - ((260 - 52 * RWT) * (AYS / 260) / 8)

*The computation of ranking jobs is carried over in the method 'computeRank' which inputs 'jobOffersList' including current job, job offers, other related job offers being provided from database, and weights stored in 'AssignComparisonSetting'. The return of 'computeRank' is a rankedOffersList: ArrayList<Job> for displaying. In order to use the weight from 'AssignComparisonSetting', a dependency relationship connecting "CompareJobOffers" clas and "AssignComparisonSetting" class.*


7. The user interface must be intuitive and responsive.

*This is not represented in my design, as it will be handled entirely within the GUI implementation.*

8. For simplicity, you may assume there is a single system running the app (no communication or saving between devices is necessary).

*Since no communication, the data sets of other job offers are not avabliable through wifi network or threads. The saved doc files containing the data sets can act as database providing all other job details other than the user entered current job and job offers.*


