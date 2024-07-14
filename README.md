Patient Insurance Data Analysis
Overview
This project involves analyzing patient insurance data using a custom Python class. The class Info_on_patients is designed to read data from a CSV file and provide various analytical insights such as average patient age, gender distribution, unique regions, average medical charges, and creating a dictionary with all patient information.

Files
insurance.csv: The CSV file containing patient data.
analysis.py: The main Python script that defines the Info_on_patients class and performs the data analysis.
Requirements
Python 3.x
CSV file containing the following columns:
age
sex
bmi
children
smoker
region
charges

Usage
Step 1: Load the Data
Ensure your CSV file is located in the correct directory. Update the file path in the script if necessary.

Step 2: Run the Script
Run the analysis.py script to perform the analysis. This script includes:

Loading the data from insurance.csv.
Creating an instance of the Info_on_patients class.
Calling methods to analyze the data and print the results.
Example
Here's an example of how to use the script:

Define the Function to Load Data
python

``` ruby
import csv

def load_list_data(lst, csv_file, column_name):
    with open(csv_file) as csv_info:
        csv_dict = csv.DictReader(csv_info)
        for row in csv_dict:
            lst.append(row[column_name])
```

Create and Use the Class

``` ruby
class Info_on_patients:
    def __init__(self, patients_ages, patients_sexes, patients_bmis, patients_num_children, patients_smoker_statuses, patients_regions, patients_charges):
        self.patients_ages = patients_ages
        self.patients_sexes = patients_sexes
        self.patients_bmis = patients_bmis
        self.patients_num_children = patients_num_children
        self.patients_smoker_statuses = patients_smoker_statuses
        self.patients_regions = patients_regions
        self.patients_charges = patients_charges

    def analyze_ages(self):
        total_age = 0
        for age in self.patients_ages:
            total_age += int(age)
        return "Average Patient Age: " + str(round(total_age / len(self.patients_ages), 2)) + " years"

    def analyze_sexes(self):
        females = 0
        males = 0
        for sex in self.patients_sexes:
            if sex == 'female':
                females += 1
            elif sex == 'male':
                males += 1
        print("Count for female: ", females)
        print("Count for male: ", males)

    def unique_regions(self):
        unique_regions = []
        for region in self.patients_regions:
            if region not in unique_regions:
                unique_regions.append(region)
        return unique_regions

    def average_charges(self):
        total_charges = 0
        for charge in self.patients_charges:
            total_charges += float(charge)
        return "Average Yearly Medical Insurance Charges: " + str(round(total_charges / len(self.patients_charges), 2)) + " dollars."

    def create_dictionary(self):
        self.patients_dictionary = {}
        self.patients_dictionary["age"] = [int(age) for age in self.patients_ages]
        self.patients_dictionary["sex"] = self.patients_sexes
        self.patients_dictionary["bmi"] = self.patients_bmis
        self.patients_dictionary["children"] = self.patients_num_children
        self.patients_dictionary["smoker"] = self.patients_smoker_statuses
        self.patients_dictionary["regions"] = self.patients_regions
        self.patients_dictionary["charges"] = self.patients_charges
        return self.patients_dictionary
```

Load DATA and Create Class Instance
You will load your own dataset into the code off your computer

``` ruby

# Provide the full path to the CSV file
csv_file_path = r"C:\python-portfolio-project-starter-files\python-portfolio-project-starter-files\insurance.csv"

ages = []
sexes = []
bmis = []
num_children = []
smoker_statuses = []
regions = []
charges = []

load_list_data(ages, csv_file_path, 'age')
load_list_data(sexes, csv_file_path, 'sex')
load_list_data(bmis, csv_file_path, 'bmi')
load_list_data(num_children, csv_file_path, 'children')
load_list_data(smoker_statuses, csv_file_path, 'smoker')
load_list_data(regions, csv_file_path, 'region')
load_list_data(charges, csv_file_path, 'charges')

# Create an instance of the Info_on_patients class
patients_info = Info_on_patients(ages, sexes, bmis, num_children, smoker_statuses, regions, charges)

# Use the methods from the class
print(patients_info.analyze_ages())
patients_info.analyze_sexes()
print(patients_info.unique_regions())
print(patients_info.average_charges())
print(patients_info.create_dictionary())
```
Output
The script will output:

-The average age of the patients.
-The count of male and female patients.
-A list of unique regions.
-The average yearly medical insurance charges.
-A dictionary containing all the patient information.

