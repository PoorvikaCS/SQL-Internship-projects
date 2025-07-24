Crime Investigation Database System (CIDB)

This project simulates a simplified crime investigation database using SQLite. It includes structured tables for managing criminal cases, officers, suspects, evidence, and their relationships. 
It also provides useful analytical views for understanding investigative progress.

Database Schema Overview

The system includes the following core entities:

* Cases: Registered crimes with their statuses and types.
* Officers: Law enforcement personnel involved in investigations.
* Suspects: People under investigation.
* CaseAssignments: Which officer is handling which case.
* SuspectCaseLink: Links suspects to the cases they are involved in.
* Evidence: Items collected as proof or material clues.
* Views: Readable summaries for analysis.

Lists each officer and the number of cases they are assigned.

| OfficerName | TotalCases |
| :---------- | ---------: |
| John Carter |          2 |
| Riya Sharma |          1 |
| Karan Das   |          1 |
| Maya Pillai |          1 |
| Arjun Roy   |          1 |

-------

CaseStatusByType

Counts how many cases are solved or unsolved, grouped by crime type.

| CrimeType | Status   | Total |
| :-------- | :------- | ----: |
| Fraud     | Unsolved |     1 |
| Murder    | Unsolved |     1 |
| Narcotics | Solved   |     1 |
| Robbery   | Solved   |     1 |

---

 EvidenceSummary

Summarizes how many pieces of evidence exist for each case.

| CaseName         | TotalEvidence |
| :--------------- | ------------: |
| ATM Robbery      |             2 |
| Online Scam      |             1 |
| Drug Bust        |             1 |
| Homicide in Park |             1 |

---

 Table Snapshots

 Evidence

All recorded items linked to cases and the officers who collected them.

| EvidenceID | CaseID | Description           | CollectedBy | ChainOfCustody           | Timestamp           |
| ---------: | -----: | :-------------------- | ----------: | :----------------------- | :------------------ |
|          1 |      1 | CCTV footage from ATM |           1 | Collected by OfficerID 1 | 2025-07-20 15:44:55 |
|          2 |      1 | Gloves left behind    |           5 | Collected by OfficerID 5 | 2025-07-20 15:44:55 |
|          3 |      2 | Email trace logs      |           2 | Collected by OfficerID 2 | 2025-07-20 15:44:55 |
|          4 |      3 | Drug samples          |           3 | Collected by OfficerID 3 | 2025-07-20 15:44:55 |
|          5 |      4 | Knife found in bushes |           1 | Collected by OfficerID 1 | 2025-07-20 15:44:55 |

---

CaseAssignments

Shows which officers are assigned to which cases.

| OfficerID | CaseID |
| --------: | -----: |
|         1 |      1 |
|         2 |      2 |
|         3 |      3 |
|         4 |      2 |
|         5 |      1 |
|         1 |      4 |

---

 SuspectCaseLink

Details of which suspects are linked to which cases.

| CaseID | SuspectID |
| -----: | --------: |
|      1 |         1 |
|      2 |         2 |
|      3 |         3 |
|      4 |         4 |

---

Officers

List of all officers in the system.

| OfficerID | Name        | Rank          | Department  |
| --------: | :---------- | :------------ | :---------- |
|         1 | John Carter | Inspector     | Homicide    |
|         2 | Riya Sharma | Sergeant      | Cyber Crime |
|         3 | Karan Das   | Constable     | Narcotics   |
|         4 | Maya Pillai | Detective     | Fraud Unit  |
|         5 | Arjun Roy   | Sub-Inspector | Theft       |

---

Cases

Complete list of cases filed, with type and status.

| CaseID | CaseName         | DateFiled  | Status   | CrimeType |
| -----: | :--------------- | :--------- | :------- | :-------- |
|      1 | ATM Robbery      | 2023-05-01 | Solved   | Robbery   |
|      2 | Online Scam      | 2023-06-15 | Unsolved | Fraud     |
|      3 | Drug Bust        | 2023-04-20 | Solved   | Narcotics |
|      4 | Homicide in Park | 2023-03-12 | Unsolved | Murder    |

---

Suspects

All individuals identified as suspects.

| SuspectID | Name         | Age | Gender | Address   |
| --------: | :----------- | --: | :----- | :-------- |
|         1 | Rahul Singh  |  35 | Male   | Mumbai    |
|         2 | Anita Verma  |  28 | Female | Delhi     |
|         3 | Sameer Khan  |  40 | Male   | Hyderabad |
|         4 | Preeti Rao   |  30 | Female | Chennai   |
|         5 | Vikram Sethi |  45 | Male   | Kolkata   |

---

 Key Features

* SQLite-backed relational database
* Enforced `FOREIGN KEY` constraints for integrity
* Support for `ON DELETE CASCADE` to maintain referential integrity
* Pre-populated sample data for practical testing
* Analytical `VIEWS` for case monitoring and workload summaries

---

Interview Questions & Answers – Crime Investigation SQL Project
1. What is the objective of your SQL project?
Answer:
The objective is to build a relational Crime Investigation Database that helps analyze cases, officers, suspects, and evidence, allowing us to generate meaningful reports such as officer workloads, case types, and suspect involvements.

2. How many tables did you create, and what are they?
Answer:
There are 9 tables:

Cases

Officers

Suspects

Evidence

CaseAssignments

SuspectCaseLink

CaseStatusByType (View)

OfficerWorkload (View)

EvidenceSummary (View)

3. What is normalization, and did you apply it?
Answer:
Normalization is the process of organizing data to reduce redundancy. Yes, I applied normalization up to 3NF. For example, officer and suspect information are kept in separate tables and linked using foreign keys.

4. Explain the relationship between Cases and Officers.
Answer:
The relationship is many-to-many. One case can have multiple officers, and one officer can be assigned to multiple cases. This is handled through the CaseAssignments junction table.

5. What kind of JOINs did you use in your queries?
Answer:
I used INNER JOIN to fetch related records across multiple tables like officer assignments, case evidence, and suspect links. Example: joining Officers with CaseAssignments.

6. How did you calculate the officer workload?
Answer:
Using a view called OfficerWorkload, I grouped the CaseAssignments table by OfficerID and counted the number of distinct CaseIDs assigned to each officer.

7. What are the key columns used for joining tables?
Answer:
Some key columns are:

CaseID (joins Cases with CaseAssignments, Evidence, and SuspectCaseLink)

OfficerID (joins Officers with CaseAssignments)

SuspectID (joins Suspects with SuspectCaseLink)

8. What is a view in SQL and how did you use it?
Answer:
A view is a virtual table based on a SQL query. I used views like OfficerWorkload, CaseStatusByType, and EvidenceSummary to simplify recurring queries and improve readability.

9. How do you ensure data integrity in your project?
Answer:
By using primary keys and foreign key constraints. For example, OfficerID in CaseAssignments references OfficerID in Officers.

10. What does your CaseStatusByType view show?
Answer:
It displays how many cases of each type (e.g., Robbery, Murder) are Open or Closed using a GROUP BY on CaseType and Status.

11. How did you link suspects to cases?
Answer:
Using the SuspectCaseLink table, which maps each suspect to one or more cases using their SuspectID and CaseID.

12. What kind of data analysis did you do using SQL?
Answer:
I analyzed:

Officer workload

Case resolution status

Evidence count per case

Number of suspects per case

Case distribution by type

13. How did you handle many-to-many relationships?
Answer:
I created bridge tables such as:

CaseAssignments for Officer-Case

SuspectCaseLink for Suspect-Case

14. What challenges did you face during this project?
Answer:
Handling foreign key constraints and ensuring consistent sample data for meaningful query outputs. Also, managing multiple joins across normalized tables.

15. If you had more time, what would you improve?
Answer: