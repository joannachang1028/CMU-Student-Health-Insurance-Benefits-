# <span style="font-family: Arial, sans-serif;">Students Health Insurance Benefits at CMU</span>

## <span style="font-family: 'Arial', serif; font-size: 20px;">• Objectives and Use Case:</span>

<p style="font-family: Arial, sans-serif;">
As a CMU student paying $2,300 annually for Highmark insurance, I want to easily understand which services are covered and any associated out-of-pocket costs, so that I can make informed decisions about my healthcare. The program could fulfill this need by prompting students to input the specific health services they are inquiring about. It would then display relevant information on coverage, co-pays, and a list of available service providers within the Highmark network.
</p>

## <span style="font-family: 'Arial', serif; font-size: 20px;">• Description:</span>

<p style="font-family: Arial, sans-serif;">
Due to overwhelming information, complex rules, or simply being too lazy to deal with it, many students are unaware of what their insurance covers and how to use it.
</p>
<p style="font-family: Arial, sans-serif;">
We aim to address this by integrating information about CMU Highmark insurance coverage with local healthcare service pricing into a program, allowing students to quickly find out if a particular service is covered by Highmark and understand any associated costs, as well as important considerations related to their healthcare decisions.
</p>
<p style="font-family: Arial, sans-serif; font-weight: bold;">Example Questions the Program Will Answer:</p>
<ul style="font-family: Arial, sans-serif;">
    <li>If a student calls an ambulance after an accident, what portion of the cost is covered by Highmark?</li>
    <li>For sports injuries requiring physical therapy, what treatments are covered, and to what extent?</li>
    <li>Are counseling sessions available under the plan for students with mental health concerns? How many are free before out-of-pocket costs apply?</li>
</ul>

## <span style="font-family: 'Arial', serif; font-size: 20px;">• Project Components:</span>

### <span style="font-family: 'Arial', serif; font-size: 18px;">Part 1: Overview of Student Insurance Enrollment (Zarina)</span>

<p style="font-family: Arial, sans-serif; font-weight: bold;">Goal:</p>
<p style="font-family: Arial, sans-serif;">Analyze the enrollment status of CMU students in the Student Health Insurance Plan (SHIP) provided by Highmark.</p>
<ul style="font-family: Arial, sans-serif;">
    <li>Correlate the number of domestic and international students enrolled in SHIP.</li>
    <li>Identify differences between domestic and international students’ enrollment.</li>
    <li>Investigate alternative insurance plans that students might choose and compare their costs.</li>
</ul>
<p style="font-family: Arial, sans-serif; font-weight: bold;">Data Sources:</p>
<ul style="font-family: Arial, sans-serif;">
    <li>Request student insurance enrollment number from CMU’s UHS Executive Director, Christine Andrews (csv or pdf).</li>
    <ul>
        <li>Status: Emailed University Health Services to request data; awaiting approval from Christine Andrews - <strong>PENDING</strong></li>
    </ul>
    <li>The total number of students enrolled in the school’s health insurance plan.</li>
    <li>The number of students using their own health insurance.</li>
    <li>If available, the number of international students enrolled in the school’s health insurance plan.</li>
</ul>

### <span style="font-family: 'Arial', serif; font-size: 18px;">Part 2: Cost for Different Injuries (Zhuoyuan and Joanna)</span>

<p style="font-family: Arial, sans-serif; font-weight: bold;">Goal:</p>
<p style="font-family: Arial, sans-serif;">Build a section that calculates and displays costs for various injuries or health concerns and the associated co-pay percentages.</p>
<p style="font-family: Arial, sans-serif; font-weight: bold;">Data Sources:</p>
<ul style="font-family: Arial, sans-serif;">
    <li>Hospital prices dataset for typical injury costs:</li>
    <ul>
        <li>CMS dataset for Medicare Physician & Other Practitioners - by Provider and Service</li>
        <li><a href="https://data.cms.gov/provider-summary-by-type-of-service/medicare-physician-other-practitioners">CMS Dataset</a></li>
    </ul>
    <li>Highmark coverage information:</li>
    <ul>
        <li>Utilize tables from CMU’s SHIP Medical Grid:</li>
        <li><a href="https://www.cmu.edu/health-services/student-insurance/pdfs/24-25-ship-medical-grid.pdf">SHIP Medical Grid PDF</a></li>
    </ul>
</ul>

### <span style="font-family: 'Arial', serif; font-size: 18px;">Part 3: Frequently Asked Questions (Vashishth)</span>

<p style="font-family: Arial, sans-serif; font-weight: bold;">Goal:</p>
<p style="font-family: Arial, sans-serif;">Create a program that answers FAQs about insurance coverage.</p>
<p style="font-family: Arial, sans-serif; font-weight: bold;">Example Options Provided by the Program:</p>
<ul style="font-family: Arial, sans-serif;">
    <li>Do you want to enroll in SHIP?</li>
    <ul>
        <li>Each section of this question menu will fork into another menu with further details based on user needs.</li>
        <li>Final helpful information about the insurance will be displayed at every stage.</li>
    </ul>
    <li>Waive the SHIP</li>
    <li>Change or Cancel the SHIP</li>
    <li>Using the SHIP</li>
    <li>International or Exchange Students</li>
    <li>Insurance Literacy</li>
    <li>Contacts</li>
    <li>Other Common Questions</li>
    <li>Leaving CMU</li>
    <li>SHIP benefits and plan documents</li>
    <li>SHIP rates and billing</li>
</ul>
<p style="font-family: Arial, sans-serif; font-weight: bold;">Data Source:</p>
<p style="font-family: Arial, sans-serif;">Extract information from SHIP’s website.</p>
