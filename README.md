Students Health Insurance Benefits at CMU

•	Objectives and Use Case:
As a CMU student paying $2,300 annually for Highmark insurance, I want to easily understand which services are covered and any associated out-of-pocket costs, so that I can make informed decisions about my healthcare. The program could fulfill this need by prompting students to input the specific health services they are inquiring about. It would then display relevant information on coverage, co-pays, and a list of available service providers within the Highmark network.

•	Description:
Due to overwhelming information, complex rules, or simply being too lazy to deal with it, many students are unaware of what their insurance covers and how to use it. 
We aim to address this by integrating information about CMU Highmark insurance coverage with local healthcare service pricing into a program, allowing students to quickly find out if a particular service is covered by Highmark and understand any associated costs, as well as important considerations related to their healthcare decisions.
Here are some possible example questions that students might have and can be answered by our program.
	If a student calls an ambulance after an accident, what portion of the cost is covered by Highmark?
	For sports injuries requiring physical therapy, what treatments are covered, and to what extent?
	Are counseling sessions available under the plan for students with mental health concerns? How many are free before out-of-pocket costs apply?

•	Project Components:
Part 1: Overview of Student Insurance Enrollment (Zarina)
Goal: Analyze the enrollment status of CMU students in the Student Health Insurance 
Plan (SHIP) provided by Highmark.
	Correlate the number of domestic and international students enrolled in SHIP.
	Identify differences between domestic and international students’ enrollment.
	Investigate alternative insurance plans that students might choose and compare their costs.
	Data Source: Request student insurance enrollment number from CMU’s UHS Executive Director, Christine Andrews(csv or pdf)
	We emailed University Health Services to request data if possible, and we are waiting on approval from UHS Executive Director, Christine Andrews - PENDING
	Data Source:
(1) The total number of students enrolled in the school’s health insurance plan.
(2) The number of students using their own health insurance.
(3) If available, the number of international students enrolled in the school’s health insurance plan.

Part 2: Cost for Different Injuries:  (Zhuoyuan and Joanna)
Build a section that calculates and displays costs for various injuries or health concerns and the associated co-pay percentages.
	Data Source 1: 
•	Hospital prices dataset for typical injury costs: 
CMS dataset for Medicare Physician & Other Practitioners - by Provider and Service
https://data.cms.gov/provider-summary-by-type-of-service/medicare-physician-other-practitioners

	Data Source 2: 
Highmark coverage information to show co-pays information and coverage limits:  
There are several tables in the two insurance PDF documents that can be utilized for designing the program
https://www.cmu.edu/health-services/student-insurance/pdfs/24-25-ship-medical-grid.pdf

Part 3: Frequently Asked Questions: (Vashishth)
Create a program that answers frequently asked questions (FAQs) about insurance coverage.
The program plans to give options to the user in the following form:
Forking out of initial questions to the user, if they point out that they have questions about student insurance, then the program will lead into the following:
•	Do you want to enroll into SHIP
o	Each section of this question menu will further fork into another menu - with further details about the requirement of the user. Depending on the user’s selections in the menu - final helpful information about the insurance will be the output at every satge.
•	Waive the SHIP
•	Change or Cancel the SHIP
•	Using the SHIP
•	International or Exchange Students
•	Insurance Literacy
•	Contacts
•	Other Common Questions
•	Leaving CMU
•	SHIP benefits and plan documents (from where the next part of of the program under Section 3 - cost of different injuries will start)
•	SHIP rates and billing (from where the next part of of the program under Section 3 - cost of different injuries will start)

	Data Source: Extract information from SHIP’s website 
