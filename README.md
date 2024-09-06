# Using-SQL-to-investigate-a-security-issue

## Project description
[I used SQL to filter data to retrieve records of employee machines and login attempts from a database to investigate a security issue. I applied the WHERE, LIKE, AND, OR, and NOT filters for this activity.]

## Environment/Labs used
- Linux
- SQL/MariaDB
- Qwiklab

## Walkthrough:

### Open terminal
![Screenshot 2024-09-05 011534](https://github.com/user-attachments/assets/2b1b2c12-32ba-4c5a-9737-bb305543390b)

### Retrieve after hours failed login attempts
[As we investigate the security issues of the organization, we need to filter and retrieve information about failed login attempts after business hours to check for suspicious activity. To do this, we will run this query:
![Screenshot 2024-09-05 011830](https://github.com/user-attachments/assets/d39a49da-405d-4f31-8a70-dcff723f6a81)


The query above will display a list of failed login attempts after business hours. In the first line, SELECT indicates which column to return from a table and * means all columns. The second line, FROM indicates the table to query, in this case,  log_in_attempts. In the third line, the WHERE clause with an AND operator is used for filtering columns for strings of data, login_time and success is the column we are filtering.  The > operator in the query will filter for login_time after ‘18:00’, and the = operator filters the success column for failed login attempts results. <b>success = 0</b> means we are filtering for false [failed] login. 0 means false [failed], while 1 means true [successful]. ]

### Retrieve login attempts on specific dates

[We discovered that a suspicious activity occurred on the 9th of may, 2022, so we decided to retrieve data of login attempts on that day and the day before. We did that by running this query:
![Screenshot 2024-09-05 013621](https://github.com/user-attachments/assets/fd45102a-b01e-4a5c-a1e0-6510682f8362)


The first line indicates to select all columns on the table. Second line indicates the table to query from . In the third line, the WHERE clause and OR operator will filter the login_date column to retrieve login dates for either 8th may, 2022 or 9th may, 2022. ]

### Retrieve login attempts outside of Mexico
[The team confirmed that mexico was not a country that had failed login attempts. With that information, we had to filter out mexico from the data being returned. To do that, we ran this query:
![Screenshot 2024-09-05 013958](https://github.com/user-attachments/assets/90f6f38b-33c1-4091-8432-ea28c92745f9)

In the query, the first line indicates to select all columns on the table. The second line indicates to return information from the ‘login_in_ attempts’ table. The third line is a filter that indicates the country not to include in the output, which is Mexico in this case. I used LIKE with 'mex%' as the pattern to match because the dataset represents Mexico as 'mex' and 'MEXICO'. In  ‘mex%’, the percentage sign substitutes for any number of other characters after ‘mex’. ]

### Retrieve employees in Marketing
[The security team also wants to perform security updates on specific machines of employees in the marketing department for all offices in the east building. 
Firstly, we’ll retrieve all the columns in the employees table by running this query:
![Screenshot 2024-09-05 014326](https://github.com/user-attachments/assets/b995a350-132f-4c4c-a342-6381d83da063)


We discovered that they are a lot of data to read through to get the specific information we need, so we'll filter this information by running this query:

![Screenshot 2024-09-05 014846](https://github.com/user-attachments/assets/61b7ab88-b30e-431b-91ec-24c4f6bfd102)


The first and second lines indicates to select all columns in the employees table. In the  third line,
WHERE clause is used to filter the department column for employees in Marketing, and the office column for offices in the the east building. AND is an inclusive filter, it specifies that  both conditions must be met simultaneously. Note as lIKE and = are used interchangeably.] 

### Retrieve employees in Finance or Sales
[Next we ran a security update check on employees' machines in the finance and sales department. This was done by typing this query:
![Screenshot 2024-09-05 015223](https://github.com/user-attachments/assets/31d8d3dd-7c02-471a-9755-efb796033d0b)


In the query above, the first and second line indicate to select all columns on the employees table. In the third line, the WHERE clause and OR operator are used to filter the department column for 'Finance' or 'Sales'. The = [equal to] operator is used to match the conditions stated.]

### Retrieve all employees not in IT
[Then we wanted to run one more security update to employees machines in all departments except the Information Technology department, because they already had it. We had to filter them out of the data being returned, so we ran this query:
![Screenshot 2024-09-05 015605](https://github.com/user-attachments/assets/d0895268-3130-4e0f-95b5-74bf24cc7bf4)


The first two lines of the query will return all columns on the employee table. In the third line, the WHERE clause and NOT operator is used to filter out the information not needed. In this case, ‘Information Technology’ on the department column.]

## Summary
[In the event of this potential security issue involving login attempts and employee machines
that was discovered, i decided to look into data from the organization’s database to investigate the incident. I completed the investigation with the use of the SELECT and FROM queries to check columns in the tables, and the WHERE, LIKE, AND, OR, and NOT filters to retrieve specific data to make the process faster and more efficient.]
