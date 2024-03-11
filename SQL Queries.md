# BANK LOAN REPORT 

## KPI’s:

### Total Loan Applications

SELECT COUNT(id) AS Total_Applications FROM bank_loan_data

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/a5f4ec13-963f-4c71-acf4-fca321c5b584)

### MTD Loan Applications

SELECT COUNT(id) AS Total_Applications FROM bank_loan_data
WHERE MONTH(issue_date) = 12

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/d5b7a421-1cb0-4def-abe3-318f7bd70279)
 
### PMTD Loan Applications

SELECT COUNT(id) AS Total_Applications FROM bank_loan_data
WHERE MONTH(issue_date) = 11
 
![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/257d7dc5-0ec2-4fea-b887-a91619d39ace)

### Total Funded Amount

SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/abcb2619-633e-4499-a0c1-03c35faaf0dc)
 
### MTD Total Funded Amount

SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data
WHERE MONTH(issue_date) = 12

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/45817a64-7380-4b29-b18c-9ce75f7e0ebb)
 
### Total Amount Received

SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/ab5ff89c-f510-42a3-b4c0-f89e57f2704a)
 
### MTD Total Amount Received

SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data
WHERE MONTH(issue_date) = 12

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/738d0437-ecf0-40bb-9988-bdc93e8a077d)

### Average Interest Rate

SELECT AVG(int_rate)*100 AS Avg_Int_Rate FROM bank_loan_data
 
### MTD Average Interest

SELECT AVG(int_rate)*100 AS MTD_Avg_Int_Rate FROM bank_loan_data
WHERE MONTH(issue_date) = 12
 
![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/6a90caa1-f94b-4959-b04e-ad9521d7ca88)

### Avg DTI
SELECT AVG(dti)*100 AS Avg_DTI FROM bank_loan_data

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/3d478281-c0c2-4555-97df-bb997ab4d940)
 
### MTD Avg DTI
SELECT AVG(dti)*100 AS MTD_Avg_DTI FROM bank_loan_data
WHERE MONTH(issue_date) = 12

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/9ac9994e-b162-4401-bb5e-610b45317c8e)


## GOOD LOAN ISSUED

### Good Loan Percentage

SELECT
    (COUNT(CASE WHEN loan_status = 'Fully Paid' OR loan_status = 'Current' THEN id END) * 100.0) / 
	COUNT(id) AS Good_Loan_Percentage
FROM bank_loan_data

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/d1c8f681-cb63-4e7a-a333-d033986d9f81)
 
### Good Loan Applications

SELECT COUNT(id) AS Good_Loan_Applications FROM bank_loan_data
WHERE loan_status = 'Fully Paid' OR loan_status = 'Current'

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/c1cf6518-597e-4aa2-8d44-8756a31dc1eb)

### Good Loan Funded Amount

SELECT SUM(loan_amount) AS Good_Loan_Funded_amount FROM bank_loan_data
WHERE loan_status = 'Fully Paid' OR loan_status = 'Current'

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/f8291e46-87d8-42e2-90ba-4867a681a600)

### Good Loan Amount Received

SELECT SUM(total_payment) AS Good_Loan_amount_received FROM bank_loan_data
WHERE loan_status = 'Fully Paid' OR loan_status = 'Current'

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/57a587a5-dd47-4592-a7d6-6e7d1f2e3866)



 



