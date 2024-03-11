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

## BAD LOAN ISSUED

### Bad Loan Percentage

SELECT
    (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / 
	COUNT(id) AS Bad_Loan_Percentage
FROM bank_loan_data

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/3231de61-7557-4d7f-a8c7-629669f4108e)
 
### Bad Loan Applications

SELECT COUNT(id) AS Bad_Loan_Applications FROM bank_loan_data
WHERE loan_status = 'Charged Off'

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/2c817ff4-80b3-4ca7-a409-edf52c99a8a0)
 
### Bad Loan Funded Amount

SELECT SUM(loan_amount) AS Bad_Loan_Funded_amount FROM bank_loan_data
WHERE loan_status = 'Charged Off'

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/063b5aed-d866-4469-9c22-0c26dfd88a58)
 
### Bad Loan Amount Received

SELECT SUM(total_payment) AS Bad_Loan_amount_received FROM bank_loan_data
WHERE loan_status = 'Charged Off'
 
![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/069fbc62-ba2a-42dc-9e1b-8f11e15b8761)

## LOAN STATUS
	SELECT
        loan_status,
        COUNT(id) AS LoanCount,
        SUM(total_payment) AS Total_Amount_Received,
        SUM(loan_amount) AS Total_Funded_Amount,
        AVG(int_rate * 100) AS Interest_Rate,
        AVG(dti * 100) AS DTI
    FROM
        bank_loan_data
    GROUP BY
        loan_status

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/91c30d77-086a-4637-b670-99d1e20bea09)

SELECT 
	loan_status, 
	SUM(total_payment) AS MTD_Total_Amount_Received, 
	SUM(loan_amount) AS MTD_Total_Funded_Amount 
FROM bank_loan_data
WHERE MONTH(issue_date) = 12 
GROUP BY loan_status

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/2ea2785d-2935-489b-91a5-b8ca5bf2def0)


# BANK LOAN REPORT | OVERVIEW

## MONTH

SELECT 
	MONTH(issue_date) AS Month_Munber, 
	DATENAME(MONTH, issue_date) AS Month_name, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY MONTH(issue_date), DATENAME(MONTH, issue_date)
ORDER BY MONTH(issue_date)

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/ab3d098b-f637-44df-9758-29950dec1561)

## STATE

SELECT 
	address_state AS State, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY address_state
ORDER BY address_state

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/995b411e-1601-4e78-b715-01bdb113cdf2)

## TERM

SELECT 
	term AS Term, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY term
ORDER BY term

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/1bcf40c8-38ca-4521-8d5f-66607f616cc2)

## EMPLOYEE LENGTH

SELECT 
	emp_length AS Employee_Length, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY emp_length
ORDER BY emp_length

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/578217a6-0130-4a2d-aff9-2cd0c391be23)

## PURPOSE

SELECT 
	purpose AS PURPOSE, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY purpose
ORDER BY purpose

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/3d854168-bb64-4e38-b03d-09f5de7afa37)

## HOME OWNERSHIP

SELECT 
	home_ownership AS Home_Ownership, 
	COUNT(id) AS Total_Loan_Applications,
	SUM(loan_amount) AS Total_Funded_Amount,
	SUM(total_payment) AS Total_Amount_Received
FROM bank_loan_data
GROUP BY home_ownership
ORDER BY home_ownership

![image](https://github.com/mohitjaisinghani10/Bank-Domain/assets/85800857/2de9e437-826c-4d82-b213-5579f90178bc)




