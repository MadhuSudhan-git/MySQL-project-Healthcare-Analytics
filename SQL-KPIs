visualization

🧩 Database & Initial Setup
CREATE DATABASE HealthCare;
USE HealthCare;

SELECT * FROM doctor;
SELECT 'doctor id' FROM doctor;

ALTER TABLE doctor CHANGE `Doctor ID` doctor_id INT;
SELECT `doctor name` FROM doctor;

📊 #1 Total Doctors
CREATE VIEW Total_Doctors AS
SELECT COUNT(`doctor id`) AS Total_Doctors FROM doctor;

SELECT * FROM Total_Doctors;

🧑‍🤝‍🧑 #2 Total Patients
CREATE VIEW Total_Patiens AS 
SELECT COUNT(`patient id`) FROM patient1;

ALTER VIEW Total_Patiens AS 
SELECT COUNT(`patient id`) AS Total_Patients FROM patient1;

SELECT * FROM Total_Patiens;

🏥 #3 Total Visits
CREATE VIEW Total_Visits AS
SELECT COUNT(`visit id`) FROM visit1;

ALTER VIEW Total_Visits AS 
SELECT COUNT(`visit id`) AS Total_Visits FROM visit1;

SELECT * FROM Total_Visits;

👶 #4 Average Age of Patients
CREATE VIEW AvgAgeOfPatients AS
SELECT AVG(age) AS avg_age FROM patient1;

SELECT ROUND(avg_age) FROM AvgAgeOfPatients;

⚕️ #5 Top 5 Diagnoses
CREATE VIEW Top5Diagnosis AS
SELECT diagnosis, COUNT(*) AS Total_Diagnosis 
FROM visit1
GROUP BY diagnosis
ORDER BY Total_Diagnosis DESC
LIMIT 5;

SELECT * FROM Top5Diagnosis;

🔁 #6 Follow-Up Rate
CREATE VIEW Follow_up_Rate AS
SELECT `follow up required`, COUNT(*) AS Follow_Up_Rate 
FROM visit1
GROUP BY `follow up required`;

SELECT * FROM Follow_up_Rate;

💊 #7 Average Treatment Cost
CREATE VIEW Avg_TreatmentCost AS
SELECT ROUND(AVG(`treatment cost`)) AS Avg_TreatmentCost 
FROM treatments;

SELECT * FROM Avg_TreatmentCost;

🧪 #8 Lab Tests Conducted
CREATE VIEW Lab_Tests_Conducted AS
SELECT COUNT(`lab result id`) AS Lab_Tests_Conducted 
FROM `lab result1`;

SELECT * FROM Lab_Tests_Conducted;

📈 #9 Result Rate
DROP VIEW IF EXISTS Result_Rate;

CREATE VIEW Result_Rate AS 
SELECT `test result`, 
CONCAT(ROUND(COUNT(*)/100,2),'%') AS Result_Rate 
FROM `lab result1`
GROUP BY `test result`;

SELECT * FROM Result_Rate;

👨‍⚕️ #10 Doctor Per Patient Ratio
CREATE VIEW Doctor_Per_Patient AS
SELECT ROUND(COUNT(DISTINCT v.`visit id`) / COUNT(DISTINCT d.`doctor id`)) AS Doctor_Per_Patient
FROM visit1 v
INNER JOIN doctor d
ON v.`doctor id` = d.`doctor id`;

SELECT * FROM Doctor_Per_Patient;

💵 #11 Total Revenue (Dynamic Format: K / M / B)
CREATE VIEW Total_Revenue AS
SELECT 
 CASE
  WHEN SUM(`treatment cost` + `cost`) >= 1000000000 THEN
   CONCAT(ROUND(SUM(`treatment cost` + `cost`) / 1000000000, 2), 'B')
  WHEN SUM(`treatment cost` + `cost`) >= 1000000 THEN
   CONCAT(ROUND(SUM(`treatment cost` + `cost`) / 1000000, 2), 'M')
  WHEN SUM(`treatment cost` + `cost`) >= 1000 THEN
   CONCAT(ROUND(SUM(`treatment cost` + `cost`) / 1000, 2), 'K')
  ELSE ROUND(SUM(`treatment cost` + `cost`), 2)
 END AS Total_Revenue
FROM treatments;

SELECT * FROM Total_Revenue;

📍 Key Insights from Queries

Quickly access KPIs through SQL Views.

Understand healthcare performance: total patients, visits, revenue, and follow-up rates.

Data-ready for visualization in Power BI dashboards.

Simplifies reporting and enhances decision-making for healthcare administrators.
