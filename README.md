# Programming-Assignment-4

This repository contains solutions to identify the codes and functions needed in cleaning and visualizing data, and be able to apply and use the different codes and functions in creating a Python program that will
be used in data wrangling and data visualization


Problem #1 - ECE BOARD EXAM PROBLEM: Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames and (ii) visuals using the dataset given.

 a. Create the following data frames based on the format provided: 
 <img width="621" height="104" alt="image" src="https://github.com/user-attachments/assets/28b4d8ad-9f1d-4629-82b6-9e7c58ba094c" />

 Code:
          
          import pandas as pd
          import numpy as np
          import matplotlib.pyplot as plt

          Vsys = pd.read_excel('board2.xlsx') 
          Vsys

          Vis = Vsys.loc[(Vsys['Hometown'] == 'Visayas') & 
               (Vsys['Math'] < 70), 
               ['Name', 'Gender', 'Track', 'Math']] 
          Vis


b.  Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon.

Code:

          Instru = Vsys.loc[(Vsys['Track'] == 'Instrumentation') & 
                  (Vsys['Hometown'] == 'Luzon') & 
                  (Vsys['Electronics'] > 70), 
                  ['Name', 'GEAS', 'Electronics']] 
          Instru

Output:  

<img width="262" height="147" alt="image" src="https://github.com/user-attachments/assets/d8239a67-241b-46fe-93ef-c989abc632ed" />

c. Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female.

Code:

         Vsys['Average'] = Vsys[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) 

         Vsys.loc [(Vsys['Gender'] == 'Female') & 
         (Vsys['Hometown'] == 'Mindanao') & 
         (Vsys['Average'] >= 55),  
         ['Name', 'Track', 'Electronics', 'Average']] #print columns name, track, electronics, and average

Ouput: 

<img width="427" height="243" alt="image" src="https://github.com/user-attachments/assets/ec0ee4ae-c2f0-43ef-9f90-67b9b0ee9838" />

Analysis:


Problem #2 - Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

a. Does chosen track in college contributes to a higher average score?

Code:

      Vsys['Average'] = Vsys[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) # average grade of subjects of students then adds as a new column

      avg = Vsys.groupby('Track')['Average'].mean() # Compute the mean for each subject

      plt.bar (avg.index, avg.values, color = ['Violet', 'Red', 'Yellow']) # create a bar graph of average grade per track using its mean and assign colors
      plt.title('Average by Track') # Outputs the title average by track
      plt.ylabel('Mean') # assign y-axis to the number of mean
      plt.xlabel('Tracks') # assign x-axis to tracks
      plt.show() #output graph

Output: 

<img width="719" height="557" alt="image" src="https://github.com/user-attachments/assets/39c14fbf-8734-4997-beb5-ae65ca2b2b20" />



b. Does gender contribute to a higher average score?

Code:

        avg = Vsys.groupby('Gender')['Average'].mean() # average gender of students then adds as a new column

        plt.bar (avg.index, avg.values, color = ['Blue', 'Pink']) # Creates a bar graph of average genders that contribute to a higher average score
        plt.title('Average by Gender') # assign the title to average by gender
        plt.ylabel('Mean') # assign the y-axis to the number of mean
        plt.xlabel('Gender') # assign the x-axis to male and female
        plt.show() # Outputs bar graph

Output: 

<img width="731" height="558" alt="image" src="https://github.com/user-attachments/assets/61cc14a7-73e8-42d4-9b1b-fc844b6f9750" />


c. Does hometown contribute to a higher average score?

Code:

        avg = Vsys.groupby('Hometown')['Average'].mean() # average hometown of students then adds as a new column

        plt.bar (avg.index, avg.values, color = ['Green', 'Indigo', 'Orange']) # Creates a bar graph of average hometown of students that contribute to a higher average score
        plt.title('Average by Hometown') #label the title to average by hometown
        plt.ylabel('Mean') # assign y-axis to the number of mean
        plt.xlabel('Hometown') # assign x-axis to the different hometowns
        plt.show() # outputs the graph

Output: 

<img width="714" height="556" alt="image" src="https://github.com/user-attachments/assets/e477c130-828e-4a88-9c03-749effc85d09" />



Analysis:

