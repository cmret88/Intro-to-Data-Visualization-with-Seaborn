# Intro-to-Data-Visualization-with-Seaborn
Seaborn

# What is Seaborn?
# Powerful python library for data visualization
# easily create most common types of plots
# Data Analysis Workflow:
# Gather data -> transform & clean -> explore -> analyze & build models -> communicate results
# Seaborn is good for exploring and communicating results
# Advantages of Seaborn
# easy to use
# works well with pandas (python library) data structure
# built on top of matplotlib (another python library)

# Getting started
# Example 1: Do Taller People Tend to Weigh More?
import seaborn as sns
import matplotlib.pyplot as plt
height = [62, 64, 69, 75, 66, 68, 65, 71, 76, 73]
weight = [120, 136, 148, 175, 137, 165, 154, 172, 200, 187]
sns.scatterplot(x=height, y=weight)
plt.show()
# shows that yes, taller people tend to weigh more

# Example 2: Create a count plot
# what is the breakdown of observations?
# count plots take in a categorical list and return bars that represent the # of list entries per category
import seaborn as sns
import matplotlib.pyplot as plt
gender = ['Female', 'Female', 'Female', 'Female', 'Male', 'Male', 'Male', 'Male', 'Male', 'Male']
sns.countplot(x=gender)
plt.show()
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns
# Change this scatter plot to have percent literate on the y-axis
sns.scatterplot(x=gdp, y=phones)
# Show plot
plt.show()

# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns
# Change this scatter plot to have percent literate on the y-axis
sns.scatterplot(x=gdp, y=percent_literate)
# Show plot
plt.show()
# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns
# Create count plot with region on the y-axis
sns.countplot(y=region)
# Show plot
plt.show()

#### Using pandas with Seaborn ####
# its an advantage that pandas works well with seaborn
# what is pandas?
# library for data analysis
# easily read datasets from csv, txt, and other types of files
# datasets take the form of DataFrame objects

# Working with DataFrames
# this dataset contains the results of a survey of adult men
# contains four columns: 'participant_id', 'age', 'how_masculine', 'how_important'
import pandas as pd
df = pd.read_csv('masculinity.csv')
df.head()

# Using Dataframes with countplot()
# this shows us that the most common response to the question to "how masculine do you feel" is "somewhat" and "very"
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv('masculinity.csv')
sns.countplot(x='how_masculine',
              data=df)
plt.show()

# IMPORTANT TO NOTE THAT SEABORN WORKS GREAT WITH PANDAS, BUT ONLY IF THE DATA IS 'TIDY'
# 'Tidy' means that each observation has its own row and each variable has its own column
# the 'masculinity' DataFrame shown here is tidy because each row is a survey response with one answer to each survey question in each column
# an untidy DataFrame, each row doesn't contain the same info
# doesn't work well with Seaborn

# Import Matplotlib, pandas, and Seaborn
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Create a DataFrame from csv file
df = pd.read_csv(csv_filepath)

# Create a count plot with "Spiders" on the x-axis
sns.countplot(x='Spiders', data=df)

# Display the plot
plt.show()

#### Adding a third variable with hue ####
# loading the tips dataset
# the dataset contains one row for each table served at a restaurant and has info about bill amount, # of ppl at table, etc
import pandas as pd
import seaborn as sns
tips = sns.load_dataset('tips')

# A basic scatter plot
import matplotlib.pyplot as plt
import seaborn as sns
sns.scatterplot(x='total_bill',
                y='tip',
                data=tips)
plt.show()
# we see that largers bills are associated with larger tips
# what if we wanted to see which of the data points are smokers vs nonsmokers?
# seaborn makes it super easy
# we add 'hue' argument:
import matplotlib.pyplot as plt
import seaborn as sns
sns.scatterplot(x='total_bill',
                y='tip',
                data=tips,
                hue='smoker')
plt.show()
# this adds a legend to the plot automatically
# Hue also allows you to assert more control over the ordering and coloring of each value
import matplotlib.pyplot as plt
import seaborn as sns
sns.scatterplot(x='total_bill',
                y='tip',
                data=tips,
                hue='smoker',
                hue_order=['Yes','No'])
plt.show()
# Yes is listed before No in the legend

# You can also choose the colors using the palette parameter
# this requires using a dictionary
# when we set hue equal to smoker and the palette parameter equal to this dictionary, we have a scatterplot where smokers are repped w/ black dots and nonsmokers w/ red dots
# this only works for a few colors available in matplotlib
import matplotlib.pyplot as plt
import seaborn as sns
hue_colors = {'Yes': 'black',
              'No' : 'red'}
sns.scatterplot(x='total_bill',
                y='tip',
                data=tips
                hue='smoker'
                palette=hue_colors)
plt.show()

# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Change the legend order in the scatter plot
sns.scatterplot(x="absences", y="G3", 
                data=student_data, 
                hue="location")

# Show plot
plt.show()

# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create a dictionary mapping subgroup values to colors
palette_colors = {"Rural": "green", "Urban": "blue"}

# Create a count plot of school with location subgroups
sns.countplot(x='school', data=student_data, hue='location', palette=palette_colors)

# Display plot
plt.show()
