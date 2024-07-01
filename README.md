# project-student-performance-analysis-
import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)
# Input data files are available in the read-only "../input/" directory
# For example, running this (by clicking run or pressing Shift+Enter) will list all files under the input directory
import os
for dirname, _, filenames in os.walk('/kaggle/input'):
for filename in filenames:
print(os.path.join(dirname, filename))
# Step 1= loading data set
df = pd.read_csv("/kaggle/input/student-performance-data/student_data.csv")
df.head()
# step 2= arranging data as per need to problem statement 
data = df[['school','Gender','age','Study Time','Exam Score']]
print(data['Exam Score'].mean())
print(data['Exam Score'].std())
data.head()
#importing some needed libraries
import matplotlib.pyplot as plt
import seaborn as sns
sns.set(style="whitegrid")
# step 3= Plot histogram of exam scores
plt.figure(figsize=(10, 6))
sns.histplot(data['Exam Score'], bins=10, kde=True, color='skyblue')
plt.title('Distribution of Exam Scores')
plt.xlabel('Exam Score')
plt.ylabel('Frequency')
plt.show()
# step 4= Scatter plot of Study Time vs. Exam Score
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Study Time', y='Exam Score', data=data, hue='Gender', palette='deep')
plt.title('Study Time vs. Exam Score')
plt.xlabel('Study Time (hours per week)')
plt.ylabel('Exam Score')
plt.legend(title='Gender')
plt.show()
# step 5= Bar chart of average exam scores by gender
plt.figure(figsize=(10, 6))
sns.barplot(x='Gender', y='Exam Score', data=data, palette='muted')
plt.title('Average Exam Scores by Gender')
plt.xlabel('Gender')
plt.ylabel('Average Exam Score')
plt.show()
# step 6= Bar chart of average exam scores by age
plt.figure(figsize=(10, 6))
sns.barplot(x='age', y='Exam Score', data=data, palette='muted')
plt.title('Average Exam Scores by Age')
plt.xlabel('Age')
plt.ylabel('Average Exam Score')
plt.show()
