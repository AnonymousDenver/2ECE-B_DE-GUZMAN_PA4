# ECE 2112 Programming Assingment 4
This repository features a collection of Python scripts designed to solve diverse programming challenges with a focus on data visualization using the matplotlib and seaborn libraries. Each script highlights specific problems, showcasing a variety of plotting techniques, chart customization options, and advanced visualization functionalities provided by these libraries.

## ECE PROBLEM
Loading a certain file to get a certain is important in both problem 1 and problem 2. We can do this using this type of code.
* File / Data Name : board2.xlsx
* Function/s : df = pd.read_excel
               print (df) 
* Description : This code reads data from an Excel file and stores it in a pandas DataFrame object called df, which allows for easy data manipulation and analysis. Print (df) will print the output. 
* Code/s : df = pd.read_excel('board2.xlsx')
           df
  
* Output :
*  ![image](https://github.com/user-attachments/assets/4ac64475-d0f6-4ae5-ace6-50e91ef70f81)





### PROBLEM 1 - Create the following data frames based on the format provided: Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas

* Function/s : pd.read_excel , loc[] ,& , < , == 
* Description : This code reads data from an Excel file, filters the DataFrame using the & (and) operator to meet two conditions: == (equality) for rows where 'Hometown' is 'Visayas', and < (less than) for rows where 'Math' scores are below 70. It selects the 'Name', 'Gender', 'Track', and 'Math' columns from the filtered data
  and prints the result.

* Code/s :df = df.loc[(df['Hometown']=='Visayas')&(df['Math']<70),['Name','Gender','Track','Math']] # Get less than 70 marks from all type of data df

* Output :
* ![image](https://github.com/user-attachments/assets/80ec0be6-7af1-497f-b571-1f182d667a98)


  


### 1 (A) - Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon

* Function/s : pd.read_excel , loc[] ,& , < , == 
* Description : The following code receives data from an Excel file, filters the DataFrame using the & (and) operator with three conditions: > (greater than) for rows where the scores for "Electronics" are more than 70, and == (equality) for rows where the 'Hometown' and 'Track' are 'Luzon'. From the filtered data, it picks the 'Name,' 'GEAS,' and 'Electronics' columns and outputs the outcome.

* Code/s : Instru = df.loc[(df['Track']=='Instrumentation')&(df['Hometown']=='Luzon')&(df['Electronics']>70),['Name','GEAS','Electronics']]
Instru

* Output :
* ![image](https://github.com/user-attachments/assets/fa88d244-eb01-46fe-bf0d-0b735db71b27)



### 1 (B) - Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

* Function/s : pd.read_excel , loc[] ,& , < , == , >= 
* Description : This code reads data from an Excel file and filters the DataFrame for female students from Mindanao with scores of 55 or above in Math, Electronics, GEAS, and Communication. It then selects and prints the 'Name', 'Track', and the relevant scores.

* Code/s : Mindy = df.loc[(df['Gender']=='Female')&(df['Hometown']=='Mindanao')&(df['Math']>=55)&(df['Electronics']>=55)&(df['GEAS']>=55)&(df['Communication']>=55),['Name','Track','Math','Electronics','GEAS','Communication']]
Mindy

* Output :
*  ![image](https://github.com/user-attachments/assets/ac7c0468-c68d-4e52-9f83-8503ea05239a)



### PROBLEM 2 - Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

#### Step 1 - Importing different kind of liblaries to use different kind of functions
* Code/s : import pandas as np , import matplotlib.pyplot as plt , import seaborn as sns 
* Description :  This code imports the pandas library for data manipulation, matplotlib for data visualization, and seaborn for enhanced statistical graphics.

#### Step 2 - Loading of the Data file . 
* Code/s  : pd.read_excel('board2.xlsx')
* Description : It loads the file from the data named - board2.xlsx

#### Step 3 - To calculate the average of different scores from different subjects. 

* Code/s : df['avg'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)  , print(df['avg'])
* Description : This code computes the average grades of students across four subjects: 'Math', 'Electronics', 'GEAS', and 'Communication'. By using the mean(axis=1) function, it calculates the mean for each row, allowing for the assessment of individual student performance across these subjects.
* Output :
* ![image](https://github.com/user-attachments/assets/aa63bf61-5d52-4fba-80bf-c89e01908cae)


#### Step 4 - It is needed also to get average from different type of classificatication. Gender , Hometown,  and Track.
* Code/s : subAvg = df.groupby(['Gender','Track','Hometown'])['avg'].mean() , subAvg
* Descriptionn : The code summarizes the average grades of students based on their gender, track of study, and hometown, helping to identify trends or performance differences among these categories and storing in new variables. 
* Output :
* ![image](https://github.com/user-attachments/assets/05fcf3fe-596f-4464-8f36-9989f6179f34)

#### Step 5 - USING OF MATPLOTLIB AND SEABORN LIBLARY. 

##### Gender 
* Codes : 
colors = ['#FFB6C1','#AA336A']
plt.figure(figsize=(11, 6))
sns.barplot(x='Gender', y='avg', data=df, hue='Gender', palette=colors)
sns.set(style="whitegrid")
plt.show


* Output -
* ![image](https://github.com/user-attachments/assets/9a0c00e1-a5cd-4f9b-8d82-5428cad17882)

* Description : The data visualize having a ll inches height and 6 inches width for both Male and Females showing Y-axis is the average and X-axis is the data frame of gender. 


##### Track 
* Codes : 
colors = ['#DAA520','#FFA07A','#FFDAB9'] # Color codes for phyton
plt.figure(figsize=(11, 4))
sns.barplot(x='Track', y='avg', data=df, hue='Track', palette=colors)
sns.set(style="whitegrid")
plt.show()

* Output : 
* ![image](https://github.com/user-attachments/assets/e168b00a-bd26-4c05-9a05-ae971483254e)

* Description : The data visualize having a ll inches height and 4 inches width for Instrumentation, Communication and Microelectronics showing Y-axis is the average and X-axis is the data frame of different track.  


##### Hometown 
* Codes :
colors = ['#FF00FF','#CC00CC','#990099']
plt.figure(figsize=(10, 4))
sns.barplot(x='Hometown', y='avg', data=df, hue='Hometown', palette=colors)
sns.set(style="whitegrid")
plt.show()

* Ouput :
![image](https://github.com/user-attachments/assets/6fab7025-d75d-46f4-a923-8c2a909f5ca3)

* Description : The data visualize having a l0 inches height and 4 inches width for Luzon, Visayas and Mindanao showing Y-axis is the average and X-axis is the data frame of different hometown.  



### AUTHOR 
## DE GUZMAN , JAN DENVER F 

### REFERENCES 
## • ECE 2112 Notes on Data Wrangling and Data Visualization by Assoc. Prof. Edison A.Roxas, Ph.D.
## AI 221 Notes on Exploratory Data Analysis by Assoc. Prof. Karl Ezra Pilario, Ph.D.

















