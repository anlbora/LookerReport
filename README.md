# Company Report Dashboard

This README file provides a comprehensive guide to understanding and using the Company Report Dashboard. This dashboard is designed to offer insights into the employee distribution, salary ranges, and departmental structures within the company.

## Report Link
- [Report](https://lookerstudio.google.com/reporting/0fce3e31-1d30-4446-ab57-5042cd9a2202)

## Dashboard Overview

![1](https://github.com/anlbora/LookerReport/assets/100442507/9dfe2f90-7c03-40df-a62e-9d88c5f383b2)

The dashboard is divided into several sections, each providing valuable information through visualizations and data tables. Below is a breakdown of the components included in the dashboard:

### 1. Filters and Navigation

- **Department Dropdown**: Select a specific department to filter the data displayed in the report.
- **Salary Slider**: Adjust the range to filter employees based on their salary.
- **Name Search**: Enter a first name to filter the data by employee name.
- **Date Range Selector**: Choose a date range to filter employees by their join date.
- **Reset Filters Button**: Click this button to clear all filters and reset the dashboard to its default view.
  
![2](https://github.com/anlbora/LookerReport/assets/100442507/140e5b82-6c75-4276-8051-e5ad0180126d)

![3](https://github.com/anlbora/LookerReport/assets/100442507/400554ff-9b9f-4dbb-9691-684f45c13be4)

![4](https://github.com/anlbora/LookerReport/assets/100442507/b0c85ac7-960f-4086-af30-642b981e4c8c)

![5](https://github.com/anlbora/LookerReport/assets/100442507/73eb7edf-c8f9-4a8e-b9d2-f4f66b7c0271)

![6](https://github.com/anlbora/LookerReport/assets/100442507/4760c065-147c-4413-ab9f-5c49d6b87474)

### 2. Key Metrics

- **Record Count**: Displays the total number of employees in the filtered view.
- **Average Salary**: Shows the average salary of the employees in the filtered view.

### 3. Data Table

The data table provides detailed information about each employee, including:
- **ID**: Employee identification number.
- **First Name**: Employee's first name.
- **Last Name**: Employee's last name.
- **Title**: Job title of the employee.
- **Email**: Employee's email address.
- **Join Date**: Date the employee joined the company.
- **Phone Number**: Contact number of the employee.
- **Salary**: Employee's salary.

### 4. Charts

#### a. Record Count by Title

This bar chart shows the number of employees for each job title within the company. It helps in understanding the distribution of employees across different roles.

#### b. Salary by Employee Title

This pie chart illustrates the percentage of total salary attributed to each job title. It's useful for visualizing how the company's payroll is distributed among different roles.

#### c. Departmental Specific Insights

For each department, the dashboard provides:
- **Record Count by Title**: Similar to the company-wide chart but filtered by the selected department.
- **Salary by Employee Title**: Provides the salary distribution for the titles within the selected department.

## Example Usage

1. **Viewing All Employees**:
   - Reset all filters to see the data for all employees in the company.
   - Observe the total number of employees and the average salary in the company.

2. **Analyzing a Specific Department**:
   - Select a department from the dropdown to filter the data.
   - Check the detailed records and charts related to that department to understand the structure and salary distribution.

3. **Salary Analysis**:
   - Use the salary slider to view employees within a specific salary range.
   - Analyze which titles and departments have the highest or lowest average salaries.

4. **Join Date Trends**:
   - Adjust the date range selector to view employees hired during a specific period.
   - This helps in analyzing hiring trends over time.

## Files and Resources

### Included Files

- **company_employees_combined_realistic.csv**: The combined dataset containing employee details.

### Generated Charts

- **Employee Distribution by Department**: Visualizes the number of employees per department.
- **Average Salary by Department**: Shows the average salary within each department.
- **Employee Distribution by Title Level**: Illustrates the count of employees at different title levels (Entry-Level, Mid-Level, Managerial, Senior Management).
- **Salary Distribution Across the Company**: Provides a histogram of the salary distribution.
- **Join Date Trends**: Displays the number of employees hired over time.
- **Employee Count by Department and Title Level**: Combines department and title level to show detailed employee counts.

## How to Use the Dashboard

1. **Open the CSV file**: Load `company_employees_combined_realistic.csv` into your data visualization tool (e.g., Excel, Power BI, Tableau).
2. **Apply Filters**: Use the provided filters to narrow down the data based on your requirements.
3. **Analyze Charts**: Examine the generated charts to get insights into employee distribution, salary ranges, and departmental breakdowns.
4. **Use the Data Table**: For detailed analysis, refer to the data table which provides comprehensive employee information.

## Data Creation

### Organization Structure
```json
    "Finance": {
        "Entry-Level": ["Accountant", "Financial Analyst"],
        "Mid-Level": ["Senior Financial Analyst"],
        "Managerial": ["Finance Manager"],
        "Senior Management": ["Finance Director"]
    },
    "HR": {
        "Entry-Level": ["HR Specialist", "Recruiter"],
        "Mid-Level": ["Senior HR Specialist"],
        "Managerial": ["HR Manager"],
        "Senior Management": ["HR Director"]
    },
    "Engineering": {
        "Entry-Level": ["Software Engineer", "Mechanical Engineer", "Electrical Engineer"],
        "Mid-Level": ["Senior Software Engineer", "Senior Mechanical Engineer", "Senior Electrical Engineer"],
        "Managerial": ["Engineering Manager"],
        "Senior Management": ["VP of Engineering"]
    },
    "Sales": {
        "Entry-Level": ["Sales Associate", "Business Development Representative"],
        "Mid-Level": ["Senior Sales Associate"],
        "Managerial": ["Sales Manager"],
        "Senior Management": ["Sales Director"]
    },
    "Marketing": {
        "Entry-Level": ["Marketing Coordinator", "Content Creator"],
        "Mid-Level": ["Senior Marketing Coordinator"],
        "Managerial": ["Marketing Manager"],
        "Senior Management": ["Marketing Director"]
    },
    "IT": {
        "Entry-Level": ["IT Support", "Network Administrator"],
        "Mid-Level": ["Senior IT Support"],
        "Managerial": ["IT Manager"],
        "Senior Management": ["IT Director"]
    },
    "Operations": {
        "Entry-Level": ["Operations Coordinator", "Supply Chain Specialist"],
        "Mid-Level": ["Senior Operations Coordinator"],
        "Managerial": ["Operations Manager"],
        "Senior Management": ["Operations Director"]
    },
    "Customer Service": {
        "Entry-Level": ["Customer Service Representative", "Call Center Agent"],
        "Mid-Level": ["Senior Customer Service Representative"],
        "Managerial": ["Customer Service Manager"],
        "Senior Management": ["Customer Service Director"]
    },
    "role_distribution": {
      "Entry-Level": 0.70,
      "Mid-Level": 0.20,
      "Managerial": 0.07,
      "Senior Management": 0.03
  }
```
### Data Creation Code

```python
# Calculate the number of each role type for 2600 entries
num_entries = 2600
entries_distribution = {role: int(num_entries * pct) for role, pct in role_distribution.items()}

# Ensure total is exactly 2600 due to rounding issues
entries_distribution["Entry-Level"] += num_entries - sum(entries_distribution.values())

# Generate data based on the organizational structure
data = []
id_counter = 1

for role, count in entries_distribution.items():
    for _ in range(count):
        department = random.choice(list(organizational_structure.keys()))
        title = random.choice(organizational_structure[department][role])
        salary = round(random.uniform(40000, 120000), 2)
        join_date = faker.date_between(start_date='-10y', end_date='today')
        
        person = {
            "ID": id_counter,
            "First Name": faker.first_name(),
            "Last Name": faker.last_name(),
            "Department": department,
            "Title": title,
            "Salary": salary,
            "Join Date": join_date,
            "Email": faker.email(),
            "Phone Number": faker.phone_number()
        }
        data.append(person)
        id_counter += 1

# Create DataFrame for additional 2600 entries
df_2600 = pd.DataFrame(additional_data)

# Save the dataframe to a new CSV file
file_path = "/mnt/data/company_employees.csv"
df_2600.to_csv(file_path, index=False)

```


