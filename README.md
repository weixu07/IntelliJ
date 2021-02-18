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
  >b. Be able to either save the job offer details or cancel.
  >c. Be able to (1) enter another offer, (2) return to the main menu, or (3) compare the offer with the current job details (if present).
