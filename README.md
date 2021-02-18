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
