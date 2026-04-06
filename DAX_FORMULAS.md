Contains ALL DAX FORMULAS  USED IN THIS PROJECT
------------------------------
1. Total Patients:
----------------------------------------------
Total Patients = SUM(PatientData[Patients_Count])
---------------------
Total Doctors:
Total Doctors = SUM(DoctorData[Doctors_Count])
----------------------
Patients per Doctor:
----------------------
Patients per Doctor = 
DIVIDE(
    SUM(PatientData[Patients_Count]),
    SUM(DoctorData[Doctors_Count]),
    0
)

---------------------------
Average Wait Time
---------------------------
Avg Wait Time = 
DIVIDE(
    SUM(PatientData[WaitTime]),
    COUNT(PatientData[Patient_ID]),
    0
)

-----------------------
Bed Utilization
-------------------------
Bed Utilization = 
DIVIDE(
    SUM(HospitalData[OccupiedBeds]),
    SUM(HospitalData[TotalBeds]),
    0
)
====================================
Location-Based Metrics
=====================================
6. Patients by Location
-----------------------

Patients by Location = 
CALCULATE(
    SUM(PatientData[Patients_Count]),
    ALLEXCEPT(PatientData, PatientData[Location])
)
--------------------------------------
7. Doctors by Location
----------------------------------
Doctors by Location = 
CALCULATE(
    SUM(DoctorData[Doctors_Count]),
    ALLEXCEPT(DoctorData, DoctorData[Location])
)
==================================================
🏥 Department Insights
====================================
8. Patients by Department
----------------------------------------

Patients by Department = 
CALCULATE(
    SUM(PatientData[Patients_Count]),
    ALLEXCEPT(PatientData, PatientData[Department])
)
----------------------------------------
9. Avg Wait Time by Department
-------------------------------------

Avg Wait Time by Department = 
CALCULATE(
    AVERAGE(PatientData[WaitTime]),
    ALLEXCEPT(PatientData, PatientData[Department])
)
=====================================
⏱️ Trend Analysis
===================================
10. Patient Trends by Day
---------------------------------------
Patients by Day = 
CALCULATE(
    SUM(PatientData[Patients_Count]),
    ALLEXCEPT(PatientData, PatientData[Date])
)
