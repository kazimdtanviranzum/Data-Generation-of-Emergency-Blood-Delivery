Code Repository for Data Generation of Emergency Blood Delivery in a Post-Earthquake Megacity with a Two-Echelon System
The data-generating procedure for Emergency Blood Delivery in a Post-Earthquake Megacity with a Two-Echelon System is handled by this code repository. The Python format will contain all of the data and code used for the data production in the study. By following the guidelines, users might be able to replicate all of the data in the study and carry out additional testing.
The Python_Code subdirectory of this repository contains the Python files for every method covered in the paper.
Python version used:
   •	Python version 3.13.0
Python packages required to run the code:
   •	time
   •	pandas
   •	random
   •	os
Please check that all of the paths lead to the correct folders, paste the data under the appropriate relative path, and review the function comments in the code before attempting to execute any of the files in your environment.

To reproduce the Data Sampling Process
  •	Run: instance_gen.py
Note:
1. Please keep the file "dhaka_random_locations" in the same folder as the code file.
2. Input file name, output file name, and output file path could be user-specified.
3. Output data size/the amount of data sampled must be specified by the user in the code files.
To reproduce the Data Instance for the Optimization Problem
To produce input data for the optimization problem of Emergency Blood Delivery in a Post-Earthquake Megacity with a Two-Echelon System, Several steps need to be undertaken.
   •	Please complete the following steps:
1. Choose any CSV file from the instance folder in the repository.
2. Begin by copying the hospital name, longitude, and altitude data from the output file generated during the data sampling process. 
3. 	Next, copy the hospital name and demand data from the output file obtained during the data sampling process. 
•	Note:
i. After the data sampling process is finished, make sure the given instructions are followed. 
ii. Keep anything else aside from what is specifically mentioned in the instructions.



