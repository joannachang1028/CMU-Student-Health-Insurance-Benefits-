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
	Data requested:
(1) The total number of students enrolled in the school’s health insurance plan.
(2) The number of students using their own health insurance.
(3) If available, the number of international students enrolled in the school’s health insurance plan.

Part 2: Programming Development 
Goal: Provide an interactive tool for students to check their Highmark insurance benefits.
1.	Interactive Window:  (Zhuoyuan and Joanna)
Topmost layer of the program to ask the user for the information and point to different sub-programs, ‘FAQ’ and ‘Cost Info‘.
Data Source: none

2.	Cost for Different Injuries:  (Zhuoyuan and Joanna)
Build a section that calculates and displays costs for various injuries or health concerns and the associated co-pay percentages.
	Data Source 1: 
•	Hospital prices dataset for typical injury costs: 
CMS dataset for Medicare Physician & Other Practitioners - by Provider and Service
https://data.cms.gov/provider-summary-by-type-of-service/medicare-physician-other-practitioners

- Coulmns from the Dataset
State Abbreviation of the Provider
Variable name：Rndrng_Prvdr_State_Abrvtn
The state where the provider is located, as reported in NPPES. The fifty U.S. states and the District of Columbia are reported by the state postal abbreviation. 

Country Code of the Provider
Variable name：Rndrng_Prvdr_Cntry
The country where the provider is located, as reported in NPPES. The country code will be ‘US’ for any state or U.S. possession. 

HCPCS Code
Variable name：HCPCS_Cd
HCPCS code used to identify the specific medical service furnished by the provider. HCPCS codes include two levels. Level I codes are the Current Procedural Terminology (CPT) codes that are maintained by the American Medical Association and Level II codes are created by CMS to identify products, supplies and services not covered by the CPT codes (such as ambulance services). CPT codes, descriptions and other data only are copyright 2016 American Medical Association. All rights reserved. CPT is a registered trademark of the American Medical Association (AMA). Please review the complete CMS AMA CPT License agreement which is presented to users when accessing the data. For additional information on HCPCS codes, visit the HCPCS general information page. 

Average Submitted Charge Amount
Variable name：Avg_Sbmtd_Chrg
Average of the charges that the provider submitted for the service.

Average Medicare Allowed Amount
Variable name：Avg_Mdcr_Alowd_Amt
Average of the Medicare allowed amount for the service; this figure is the sum of the amount Medicare pays, the deductible and coinsurance amounts that the beneficiary is responsible for paying, and any amounts that a third party is responsible for paying.

*** HCPCS code
Based on the health benefits listed in the provided PDF document, here are some HCPCS (Healthcare Common Procedure Coding System) Level II codes that could relate to the benefits mentioned. These codes correspond to items or services commonly covered by HCPCS Level II:
Example Benefits and Corresponding HCPCS Codes:
1.	Ambulance Services:
o	HCPCS Code: A0428 (Ambulance service, basic life support, non-emergency transport, no advanced life support level of service provided)
o	HCPCS Code: A0430 (Ambulance service, air transport, one way - fixed wing)
2.	Durable Medical Equipment (DME):
o	HCPCS Code: E0110 (Crutches, underarm, wood, adjustable or fixed, pair, with pads, tips)
o	HCPCS Code: E0424 (Stationary liquid oxygen system, rental; includes container, contents, regulator, flowmeter, humidifier, cannula or mask, and tubing)
3.	Home Health Care:
o	HCPCS Code: G0154 (Services of skilled nurse in home health setting, each 15 minutes)
4.	Emergency Room Services:
o	HCPCS Code: G0380 (Level 1 hospital emergency department visit)
o	HCPCS Code: G0381 (Level 2 hospital emergency department visit)
5.	Preventive Care Services (Immunizations):
o	HCPCS Code: 90658 (Influenza virus vaccine, trivalent, split virus, when administered to individuals 3 years of age and older, for intramuscular use)
o	HCPCS Code: 90746 (Hepatitis B vaccine, adult dosage, 3 dose schedule, for intramuscular use)
6.	Physical Therapy:
o	HCPCS Code: G0151 (Services performed by a qualified physical therapist in the home health or hospice setting, each 15 minutes)
o	HCPCS Code: G0283 (Electrical stimulation, unattended, for wound care, not otherwise covered)
7.	Spinal Manipulations:
o	HCPCS Code: S8990 (Physical or manipulative therapy performed for maintenance rather than restoration)
8.	Surgical Services:
o	HCPCS Code: S2900 (Surgical techniques requiring use of robotic surgical system)
9.	Diagnostic Services (CT, MRI, PET, etc.):
o	HCPCS Code: G0219 (PET imaging whole body; melanoma for non-covered indications)
o	HCPCS Code: G0379 (Direct referral for hospital observation care)

- Data Extracting Process
Filters: Country-US, state-PA 
Python list of HCPCS codes:
hcpcs_codes = [
    # Ambulance Services
    "A0428",  # Ambulance service, basic life support, non-emergency
    "A0430",  # Ambulance service, air transport, one way - fixed wing

    # Durable Medical Equipment (DME)
    "E0110",  # Crutches, underarm, wood, adjustable or fixed, pair
    "E0424",  # Stationary liquid oxygen system, rental

    # Home Health Care
    "G0154",  # Services of skilled nurse in home health setting, each 15 minutes

    # Emergency Room Services
    "G0380",  # Level 1 hospital emergency department visit
    "G0381",  # Level 2 hospital emergency department visit

    # Preventive Care Services (Immunizations)
    "90658",  # Influenza virus vaccine
    "90746",  # Hepatitis B vaccine, adult dosage

    # Physical Therapy
    "G0151",  # Physical therapy in home health setting
    "G0283",  # Electrical stimulation, unattended, for wound care

    # Spinal Manipulations
    "S8990",  # Physical or manipulative therapy for maintenance

    # Surgical Services
    "S2900",  # Surgical techniques requiring robotic system

    # Diagnostic Services (CT, MRI, PET, etc.)
    "G0219",  # PET imaging whole body; melanoma for non-covered indications
    "G0379"   # Direct referral for hospital observation care

After filtering the codes above, we got 1,115 rows from 9,755,427.
overview of the data: https://data.cms.gov/provider-summary-by-type-of-service/medicare-physician-other-practitioners/medicare-physician-other-practitioners-by-provider-and-service/data?query=%7B%22filters%22%3A%7B%22list%22%3A%5B%7B%22conjunction%22%3A%7B%22value%22%3A%22AND%22%7D%2C%22conditions%22%3A%5B%7B%22column%22%3A%7B%22value%22%3A%22Rndrng_Prvdr_Cntry%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22US%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22Rndrng_Prvdr_State_Abrvtn%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22PA%22%5D%7D%5D%7D%2C%7B%22conjunction%22%3A%7B%22value%22%3A%22OR%22%7D%2C%22conditions%22%3A%5B%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22A0430%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22A0428%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22E0110%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22E0424%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0154%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0380%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0381%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%2290658%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%2290746%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0151%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0283%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22S8990%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22S2900%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0219%22%5D%7D%2C%7B%22column%22%3A%7B%22value%22%3A%22HCPCS_Cd%22%7D%2C%22comparator%22%3A%7B%22value%22%3A%22%3D%22%7D%2C%22filterValue%22%3A%5B%22G0379%22%5D%7D%5D%7D%5D%2C%22rootConjunction%22%3A%7B%22value%22%3A%22AND%22%7D%7D%2C%22keywords%22%3A%22%22%2C%22offset%22%3A0%2C%22limit%22%3A10%2C%22sort%22%3A%7B%22sortBy%22%3A%22HCPCS_Desc%22%2C%22sortOrder%22%3A%22ASC%22%7D%2C%22columns%22%3A%5B%22Rndrng_Prvdr_State_Abrvtn%22%2C%22Rndrng_Prvdr_Cntry%22%2C%22HCPCS_Cd%22%2C%22HCPCS_Desc%22%2C%22Avg_Sbmtd_Chrg%22%2C%22Avg_Mdcr_Alowd_Amt%22%5D%7D

	Data Source 2: 
•	Highmark coverage information to show co-pays information and coverage limits:
https://www.cmu.edu/health-services/student-insurance/pdfs/24-25-ship-medical-grid.pdf
https://www.cmu.edu/health-services/student-insurance/pdfs/24-25-ship-medical-sbc.pdf 

3. Frequently Asked Questions: (Vashishth)
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






