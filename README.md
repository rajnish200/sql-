# MySQL-lesson

! Connecting to MySql;
  using the command line:	 
	
	 	   mysql - u username -p

#Creating Database  
  1  -  To Create Database(CREATE Query)-
		
		    CREATE DATABASE Hospital;
			
   2- Show all Database   (SHOW Query)
	 
		    SHOW DATABASES;

  3- Creating the a Patient Table:

		 	CREATE TABLE Patients (
   				  patient_id INT AUTO_INCREMENT PRIMARY KEY,
   				  patient_name VARCHAR(100),
				    doctor_name VARCHAR(100),
				    diagnosis VARCHAR(255),
				    phone_no VARCHAR(20),
				    admit_date DATE,
				    discharge_date DATE,
				    gender ENUM('Male', 'Female', 'Other'),
				    address VARCHAR(255)
     );
![image alt](https://github.com/amanrawa/MySQL-lesson/blob/4e3cc7ec349f5668a032604451d8e94bb59015eb/Screenshot%202024-11-06%20234410.png)
 4- Inserting a New Patient:

		
        INSERT INTO patients (patient_name, doctor_name, diagnosis, phone_no, admit_date, discharge_date, gender, address)
	VALUES
			    ('Aryan Singh', 'Dr. Patel', 'Malaria', '9876543210', '2023-11-06', '2023-11-08', 'Male', 'New Delhi, India'),
			    ('Aisha Khan', 'Dr. Sharma', 'Dengue Fever', '9876543211', '2023-11-07', '2023-11-09', 'Female', 'Mumbai, Maharashtra, India'),
			    ('Ravi Kumar', 'Dr. Gupta', 'Tuberculosis', '9876543212', '2023-11-08', '2023-11-10', 'Male', 'Kolkata, West Bengal, India'),
			    ('Priya Patel', 'Dr. Nair', 'Typhoid', '9876543213', '2023-11-09', '2023-11-11', 'Female', 'Chennai, Tamil Nadu, India'),
			    ('Rohan Sharma', 'Dr. Iyer', 'Diabetes', '9876543214', '2023-11-10', '2023-11-12', 'Male', 'Bangalore, Karnataka, India'),
			    ('Neha Gupta', 'Dr. Singh', 'Heart Disease', '9876543215', '2023-11-11', '2023-11-13', 'Female', 'Hyderabad, Telangana, India'),
			    ('Amit Kumar', 'Dr. Sharma', 'Kidney Stones', '9876543216', '2023-11-12', '2023-11-14', 'Male', 'Pune, Maharashtra, India'),
			    ('Anika Patel', 'Dr. Nair', 'Asthma', '9876543217', '2023-11-13', '2023-11-15', 'Female', 'Ahmedabad, Gujarat, India'),
		    ('Rahul Sharma', 'Dr. Gupta', 'Depression', '9876543218', '2023-11-14', '2023-11-16', 'Male', 'Jaipur, Rajasthan, India'),
		    ('Rani Singh', 'Dr. Patel', 'Anxiety', '9876543219', '2023-11-15', '2023-11-17', 'Female', 'Lucknow, Uttar Pradesh, India');

 ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/0b681f7465fc12c84b1b3c4c4446cd4a5937dc8f/Output/insert%20patients%20values.png)




 5- Select Query (Retrieving All Patients data)

     SELECT *FROM patients;
 ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/0b681f7465fc12c84b1b3c4c4446cd4a5937dc8f/Output/Select.png)
 
6- Retrieving Patients by Doctor Name

     SELECT * From patients WHERE doctor_name='Dr.Patel';
 ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/0b681f7465fc12c84b1b3c4c4446cd4a5937dc8f/Output/Select%20by%20doctor%20name.png)
7-Retrieving Patients Admitted on a Specific Date

    SELECT * FROM patients WHERE admit_date = '2023-11-06;
![image alt](https://github.com/amanrawa/MySQL-lesson/blob/f66193b7e589c43f499ca8c6f523663fb1e948eb/Output/Date%20-%20Copy.png)
8- Retrieving Patients Discharged Between Two Dates

    SELECT * FROM patients WHERE discharge_date BETWEEN '2023-11-01' AND '2023-11-10';
   ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/f66193b7e589c43f499ca8c6f523663fb1e948eb/Output/Discharge%20Date%20between%20-%20Copy.png)

9- Updating a Patient's Phone Number

    UPDATE patients SET phone_no = '987-654-3210' WHERE patient_id = 1;
   ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/f66193b7e589c43f499ca8c6f523663fb1e948eb/Output/Update%20phone%20no..png)
10-  Deleting a Patient

    DELETE FROM patients WHERE patient_id = 2;
   ![image alt]

#For performing Join Queries We need to build another table like doctor1 and insert values

      CREATE TABLE doctors1 (
    doctor_id INT AUTO_INCREMENT PRIMARY KEY,
    doctor_name VARCHAR(100),
    specialization VARCHAR(100));

    INSERT INTO doctors1 (doctor_name, specialization)
	VALUES
   	 ('Dr. Patel', 'General Physician',5),
   	 ('Dr. Sharma', 'Cardiologist',8),
   	 ('Dr. Gupta', 'Pediatrician',9),
	('Dr. Nair', 'Dermatologist',10),
    	('Dr. Iyer', 'Orthopedician',7);

  ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/3bcc4d25001c122131e14fbd2119f943a7599034/Output/create%20doctor.png)
11 - Inner Join: (Retrieve patients and their corresponding doctor details):

	SELECT p.patient_name, d.doctor_name, p.diagnosis
	FROM patients p
	INNER JOIN doctors1 d ON p.doctor_name = d.doctor_name;
 ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/4457b17db862d4a04d84e14241b5605e999f13fa/Output/inner%20join.png)
12- Left Join:Retrieve all patients, even if they don't have a corresponding doctor:

	  SELECT p.patient_name, d.doctor_name
	  FROM patients p
          LEFT JOIN doctors1 d ON p.doctor_name = d.doctor_name;
   ![image alt](https://github.com/amanrawa/MySQL-lesson/blob/4457b17db862d4a04d84e14241b5605e999f13fa/Output/left%20join.png)
13-   Right Join:Retrieve all doctors, even if they don't have any patients:

	 SELECT p.patient_name, d.doctor_name
	 FROM patients p
	 RIGHT JOIN doctors1 d ON p.doctor_name = d.doctor_name;
![image alt](https://github.com/amanrawa/MySQL-lesson/blob/4457b17db862d4a04d84e14241b5605e999f13fa/Output/Right%20join.png)
14- Full Outer Join:Retrieve all patients and doctors, combining matching and non-matching rows: 

	  SELECT p.patient_name, d.doctor_name,p.gender,p.diagnosis,p.admit_date
		from patients p
		Left Join doctors1 d ON p.patient_name=d.doctor_name
		UNION
		select p.patient_name, d.doctor_name,p.gender,p.diagnosis,p.admit_date
		from patients p
		right Join doctors1 d ON p.patient_name=d.doctor_name


![image alt](https://github.com/amanrawa/MySQL-lesson/blob/4457b17db862d4a04d84e14241b5605e999f13fa/Output/full%20join%20-%20Copy.png)


15 -The DROP DATABASE statment is used to drop an existing SQL database.

      DROP DATABASE databasename;
    

    
     

  

	 
