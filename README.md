# SBUP-PMKVY-PROJECT-08
1. Raw Data Description (customers_raw_500.csv) :
The raw dataset comprises 500 customer records and includes five columns: CustomerID, Name, Email, Phone, and Address. Every customer has a unique ID and associated name, but the dataset contains missing values in the Email, Phone, and Address fields. Some entries have invalid formats, such as emails lacking the “@” symbol or phone numbers in inconsistent formats. Overall, while the structure is straightforward and intended for contact management or CRM use, the data lacks the consistency and completeness needed for reliable downstream processing.

⸻

2. Data Cleaning Script Description (Data cleaning script.docx) :
The data cleaning process is implemented in PySpark using AWS Glue. The script begins by loading raw customer data from an AWS Glue Data Catalog table. It then applies several transformations:
	•	Standardization: Names are replaced with "Unknown" if blank, and emails are validated and normalized to lowercase.
	•	Email Handling: Invalid or missing emails are replaced with "noemail@example.com".
	•	Phone Formatting: Phone numbers are cleaned to retain only digits, right-truncated to the last 10 digits, and padded as needed. Missing numbers are set to "0000000000".
	•	Address Handling: Missing addresses are filled in with "Not Provided".
	•	Deduplication: Duplicate records are removed.
	•	Data Quality: A basic ruleset checks that each row has at least one column.
Finally, the cleaned data is written back to an S3 location in CSV format.


3. Cleaned Data Description (Output-cleaned -data.csv) :
The cleaned output is a refined version of the original dataset, with 100% of records now containing valid, standardized values for all five columns. Emails are all present, lowercase, and properly formatted. Phone numbers are consistent in length and structure, and placeholder values are used where data was missing. The names and addresses have also been normalized to remove blanks. Duplicates have been eliminated, improving data integrity. This cleaned dataset is now ready for analysis, customer profiling, or integration into business systems with confidence in its quality and consistency.
