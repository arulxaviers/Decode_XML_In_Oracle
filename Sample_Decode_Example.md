# Decode EXM IN Oracle Database

CREATE TABLE EMP_XML (XML_ID NUMBER,XML_DATA XMLTYPE);
--------------------------------------------------
INSERT INTO EMP_XML VALUES(100000,'<?xml version="1.0" encoding="UTF-8"?>
<DETAILS>
  <EMP_ID>101</EMP_ID>
  <EMP_NAME>Arul</EMP_NAME>
  <EMP_SALARY>10000</EMP_SALARY>
  <EMP_DEPT>100</EMP_DEPT>
  <EMP_JOB_ID>IT001</EMP_JOB_ID>
</DETAILS>');


INSERT INTO EMP_XML VALUES(200000,'<?xml version="1.0" encoding="UTF-8"?>
<DETAILS>
  <EMP_ID>102</EMP_ID>
  <EMP_NAME>Xavier</EMP_NAME>
  <EMP_SALARY>15000</EMP_SALARY>
  <EMP_DEPT>200</EMP_DEPT>
  <EMP_JOB_ID>CSE01</EMP_JOB_ID>
</DETAILS>');

INSERT INTO EMP_XML VALUES(300000,'<?xml version="1.0" encoding="UTF-8"?>
<DETAILS>
  <EMP_ID>103</EMP_ID>
  <EMP_NAME>Agastin</EMP_NAME>
  <EMP_SALARY>18000</EMP_SALARY>
  <EMP_DEPT>300</EMP_DEPT>
  <EMP_JOB_ID>ECE01</EMP_JOB_ID>
</DETAILS>');

INSERT INTO EMP_XML VALUES(400000,'<?xml version="1.0" encoding="UTF-8"?>
<DETAILS>
  <EMP_ID>104</EMP_ID>
  <EMP_NAME>John</EMP_NAME>
  <EMP_SALARY>21000</EMP_SALARY>
  <EMP_DEPT>400</EMP_DEPT>
  <EMP_JOB_ID>IT001</EMP_JOB_ID>
</DETAILS>');

INSERT INTO EMP_XML VALUES(500000,'<?xml version="1.0" encoding="UTF-8"?>
<DETAILS>
  <EMP_ID>105</EMP_ID>
  <EMP_NAME>Raja</EMP_NAME>
  <EMP_SALARY>25000</EMP_SALARY>
  <EMP_DEPT>500</EMP_DEPT>
  <EMP_JOB_ID>CSE01</EMP_JOB_ID>
</DETAILS>');



-------------------------------------------------------------------------------------------------------------------------------------

Select Emp.*
               FROM EMP_XML x,
                    XMLTABLE (
                       '/DETAILS'
                       Passing X.Xml_Data
                       COLUMNS "EMP_ID"  VARCHAR2 (30 BYTE)
                                  Path 'EMP_ID',
                               "EMP_NAME"  VARCHAR2 (70 BYTE)
                                  Path 'EMP_NAME',
                               "EMP_SALARY"  NUMBER (5, 0)
                                  Path 'EMP_SALARY',
                               "EMP_DEPT"  VARCHAR2 (20 BYTE)
                                  Path 'EMP_DEPT',
                               "EMP_JOB_ID"  VARCHAR2 (50 BYTE)
                                  PATH 'EMP_JOB_ID') Emp
--------------------------------------------------------------------------------------------------------------------------------------------                                  
CREATE TABLE EMPLOYEE (EMP_ID VARCHAR2(30),EMP_NAME VARCHAR2(70),EMP_SALARY NUMBER,EMP_DEPT VARCHAR2(20),EMP_JOB_ID VARCHAr2(50));
---------------------------------------------------------------------------------------------------------------------------------------------
Insert Into Employee (Emp_Id,Emp_Name,Emp_Salary,Emp_Dept,Emp_Job_Id)
Select Emp.*
               FROM EMP_XML x,
                    XMLTABLE (
                       '/DETAILS'
                       Passing X.Xml_Data
                       COLUMNS "EMP_ID"  VARCHAR2 (30 BYTE)
                                  Path 'EMP_ID',
                               "EMP_NAME"  VARCHAR2 (70 BYTE)
                                  Path 'EMP_NAME',
                               "EMP_SALARY"  NUMBER (5, 0)
                                  Path 'EMP_SALARY',
                               "EMP_DEPT"  VARCHAR2 (20 BYTE)
                                  Path 'EMP_DEPT',
                               "EMP_JOB_ID"  Varchar2 (50 Byte)
                                  PATH 'EMP_JOB_ID') Emp;
								  
------------------------------------------------------------------------------------------------------------------------------------------------








