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

#### Introduction to relational plots and subplots ####
# many questions in data science are centered around describing the relationship between two quantitative variables
# these are "relational plots" in seaborn
# examples of relational plots:
# height vs. weight
# # of school absences vs. final grade
# GDP vs. % literate
# in this lesson, we will create a separate plot per subgroup
# Introducing relplot()
# create relational plots: scatter plots or line plots
# Why relplot() instead of scatterplot()?
# relplot() lets you create subplots in a single figure

# scatterplot() vs. relplot()
# using scatterplot()
import seaborn as sns
import matplotlib.pyplot as plt
sns.scatterplot(x='total_bill', y='tip', data=tips)
plt.show()

# using relplot()
# 'kind' parameter specifies what kind of relational plot to use
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter')
plt.show()

# Subplots in columns
# this shows two plots side by side
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', col='smoker')
plt.show()

# Subplots in rows
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', row='smoker')
plt.show()

# Subplots in rows and columns
# this shows four plots
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', col='smoker', row='time')
plt.show()

# Wrapping columns
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', col='day', col_wrap=2)
plt.show()

# Ordering columns
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', col='day', col_wrap=2,
            col_order=['Thur','Fri','Sat','Sun'])
plt.show()

# Change this scatter plot to arrange the plots in rows instead of columns
sns.relplot(x="absences", y="G3", 
            data=student_data,
            kind="scatter", 
            row="study_time")

# Show plot
plt.show()

# Create a scatter plot of G1 vs. G3
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='G1',
            y='G3',
            kind='scatter',
            data=student_data)

# Show plot
plt.show()

# Adjust further to add subplots based on family support
sns.relplot(x="G1", y="G3", 
            data=student_data,
            kind="scatter", 
            col="schoolsup",
            col_order=["yes", "no"])

# Show plot
plt.show()

# Adjust further to add subplots based on family support
sns.relplot(x="G1", y="G3", 
            data=student_data,
            kind="scatter", 
            col="schoolsup",
            col_order=['yes','no'],
            row='famsup',
            row_order=["yes", "no"])

# Show plot
plt.show()

#### Customizing scatter plots ####
# customizing point size
# setting the 'size' parameter equal to the variable name 'size' from our dataset
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', size='size')
plt.show()

# Point size and hue
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', size='size', hue='size')
plt.show()

# Subgroups with point style
import seaborn as sns
import matplotlib.pyplot as plt
sns.relplot(x='total_bill', y='tip', data=tips, kind='scatter', hue='smoker', style='smoker')
plt.show()

# Changing point transparency
import seaborn as sns
import matplotlib.pyplot as plt
# set alpha to be between 0 and 1
sns.relplot(x='total_bill',
            y='tip',
            data=tips,
            kind='scatter',
            alpha=0.4)
plt.show()

# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create scatter plot of horsepower vs. mpg
sns.relplot(x="horsepower", y="mpg", 
            data=mpg, kind="scatter",
            size='cylinders', 
            hue="cylinders")

# Show plot
plt.show()

# Import Matplotlib and Seaborn
import matplotlib.pyplot as plt
import seaborn as sns

# Create a scatter plot of acceleration vs. mpg
sns.relplot(x='acceleration', y='mpg', data=mpg, kind='scatter', style='origin', hue='origin')

# Show plot
plt.show()

#### Introduction to Line Plots ####
# What are line plots?
# two types of relational plots: scatter plots and line plots
# Scatter plot - each plot point is an independent observation
# Line plot - each plot point represents the same thing typically tracked over time
# common example could be tracking the value of a company stock over time
# we'll be using air pollution data for this exercise
# collection stations across a city that collects air nitrogen dioxide samples
# one data point per x-value

# Scatterplot
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2_mean', data=air_df_mean, kind='scatter')
plt.show()

# Line Plot
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2_mean', data=air_df_mean, kind='line')
plt.show()

# Subgroups by location
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2_mean', data=air_df_mean, kind='line', style='location', hue='location')
plt.show()

# Adding by markers
# this displays a marker for each data point
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2_mean', data=air_df_mean, kind='line', style='location', hue='location', markers=True)
plt.show()

# Turning off line style
# if you don't want to the line styles to vary by subgroup, set the dashes parameter to False
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2_mean', data=air_df_mean, kind='line', style='location', hue='location', markers=True, dashes=False)
plt.show()

# Multiple observations per x-value
# line plots can also be used when you have more than one obs per x-value
# the dataset in this exercise has a row for each station that is taking a measurement every hour
# Scatterplot
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2_mean', data=air_df, kind='scatter')
plt.show()

# Line plot
# if a line plot is given multiple observations per x-value, it will aggregate them into a single summary measure
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2', data=air_df, kind='line')
plt.show()

# Replacing confidence interval with standard deviation
# Seaborn will automatically calculate a confidence interval and display with a shaded region on the graph
# assuming the data set is a random sample
# there is a 95% CI (95% confident that the mean is within this interval
# indicates uncertainty in our estimate
import matplotlib.pyplot as plt
import seaborn as sns
sns.relplot(x='hour', y='NO_2', data=air_df, kind='line', errorbar='sd')
plt.show()

#### Count plots and bar plots ####
# Categorical plots: count plots and bar plots
# involve a categorical variable
# comparisons between groups

# catplot()
# used to create categorical plots
# same advantages of relplot()
# easily create subplots with col= and row=

# countplot() vs. catplot()
# countplot()
import matplotlib.pyplot as plt
import seaborn as sns
sns.countplot(x='how_masculine', data=masculinity_data)
plt.show()

# catplot()
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='how_masculine', data=masculinity_data, kind='count')
plt.show()

# changing the order
import matplotlib.pyplot as plt
import seaborn as sns
category_order=['No answer', 'Not at all', 'Not very', 'Somewhat', 'Very']
sns.catplot(x='how_masculine', data=masculinity_data, kind='count', order=category_order)
plt.show()

# Bar plots
# display means of quantitative variable per category
# lines shows 95% CI for the mean
# shows uncertainty about our estimate
# assumes our data is a random sample
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='day', y='total_bill', data=tips, kind='bar')
plt.show()

# turning off CIs
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='day', y='total_bill', data=tips, kind='bar', errorbar=None)
plt.show()

# changing the orientation
# switch the x and y parameters
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='total_bill', y='day', data=tips, kind='bar')
plt.show()

# Separate into column subplots based on age category
sns.catplot(y="Internet usage", data=survey_data,
            kind="count", col='Age Category')

# Show plot
plt.show()

# Create a bar plot of interest in math, separated by gender
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='Gender', y='Interested in Math', data=survey_data, kind='bar')

# Show plot
plt.show()

# List of categories from lowest to highest
category_order = ["<2 hours", 
                  "2 to 5 hours", 
                  "5 to 10 hours", 
                  ">10 hours"]

# Turn off the confidence intervals
sns.catplot(x="study_time", y="G3",
            data=student_data,
            kind="bar",
            order=category_order,
            errorbar=None)

# Show plot
plt.show()

#### Creating a box plot ####
# shows a distribution of quantitative data
# see median, spread, skewness and outliers
# facilitates comparisons between groups

# how to create a box plot
import matplotlib.pyplot as plt
import seaborn as sns
g = sns.catplot(x='time',
                y='total_bill',
                data=tips,
                kind='box')
plt.show()

# change the order of categories
import matplotlib.pyplot as plt
import seaborn as sns
g = sns.catplot(x='time',
                y='total_bill',
                data=tips,
                kind='box',
                order=['Dinner', 'Lunch'])
plt.show()

# Omitting the outliers
import matplotlib.pyplot as plt
import seaborn as sns
g = sns.catplot(x='time',
                y='total_bill',
                data=tips,
                kind='box',
                showfliers=False)
plt.show()

# Changing the whiskers using 'whis'
# by default, the whiskers extend to 1.5* the IQR (the 25th to 75th percentile of a distribution of data)
# make them extend to 2.0*IQR: whis=2.0
# show the 5th and 95th percentiles: whis=[5, 95]
# show min and max values: whis=[0, 100]
import matplotlib.pyplot as plt
import seaborn as sns
g = sns.catplot(x='time',
                y='total_bill',
                data=tips,
                kind='box',
                whis=[0, 100])
plt.show()

# NOTE THAT THERE ARE NOT OUTLIERS B/C THE BOX AND WHISKERS COVER THE ENTIRE RANGE OF DATA

#### Point Plots ####
# point show mean of quantitative variable
# vertical line show 95% CI for mean estimates
# point plots vs. line plots
# both show mean of quantitative variable
# 95% CI for the mean
# differences - line plot has quantitative variable (usually time) on x-axis
# point plot has categorical variable on x-axis
# when should we use one over the other?

# Creating a point plot
# this is a categorical plot, so we use catplot and kind=point
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

# Disconnecting the points
# sometimes we may want to remove the lines connecting each point b/c we wish to compare only within a category group and not between them
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point',
            linestyle='none')
plt.show()

# Displaying the median
# median is more robust to outliers, so if your dataset has a lot of outliers, the median may be a better stat to use
import matplotlib.pyplot as plt
import seaborn as sns
from numpy import median
sns.catplot(x='smoker',
            y='total_bill',
            data=tips,
            kind='point',
            estimator=median)
plt.show()

# Customizing the CI
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='smoker',
            y='total_bill',
            data=tips,
            kind='point',
            capsize=0.2)
plt.show()

# Turning off CIs
import matplotlib.pyplot as plt
import seaborn as sns
sns.catplot(x='smoker',
            y='total_bill',
            data=tips,
            kind='point',
            errorbar=None)
plt.show()

#### Changing Plot Style & Color ####
# Why customize?
# Reasons to change style:
# personal preference, improve readability, direct audience to key takeaway

# Changing the figure style
# figure 'style' includes background and axes
# preset options: 'white', 'dark', 'whitegrid, 'darkgrid', 'ticks'
sns.set_style()

# Default figure style ('white')
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

# Other styles
sns.set_style('ticks')
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

sns.set_style('darkgrid')
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

sns.set_style('whitegrid')
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

# Changing the palette
# figure 'palette' changes the color of the main elements of the plot
# use preset palettes or create a custom palette
sns.set_palette()

# Example (default palette)
category_order = ['No answer',
                  'Not at all',
                  'Not very',
                  'Somewhat',
                  'Very']
sns.catplot(x='how_masculine',
            data=masculinity_data,
            kind='count',
            order=category_order)
plt.show()

# Example (diverging palette)
sns.set_palette('RdBu')
category_order = ['No answer',
                  'Not at all',
                  'Not very',
                  'Somewhat',
                  'Very']
sns.catplot(x='how_masculine',
            data=masculinity_data,
            kind='count',
            order=category_order)
plt.show()

# Custom palettes
custom_palette = ['red','green','orange','blue','yellow','purple']
sns.set_palette(custom_palette)

# Changing the scale
# figure 'context' changes the scale of the plot elements and labels
sns.set_context()
# smallest to largest: 'paper','notebook','talk','poster'

# Default context: 'paper'
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

# Larger context:'talk'
sns.set_context('talk')
sns.catplot(x='age',
            y='masculinity_important',
            data=masculinity_data,
            hue='feel_masculine',
            kind='point')
plt.show()

#### Adding titles and labels: Part 1 ####
# Creating informative visualizations
# FacetGrid vs. AxesSubplot objects
# seaborn plots creates these two different types of objects ^
g=sns.scatterplot(x='height',y='weight', data=df)
type(g) # returns object type

# a FacetGrid consists of one or more AxesSubplots, which is how it supports subplots
# replot() and catplot() both support making subplots
# scatterplot() and countplot() only create a single plot

# Adding a title to FacetGrid
g=sns.catplot(x='Region',
              y='Birthrate',
              data=gdp_data,
              kind='box')
g.figure.suptitle('New Title')
plt.show()

# Adjusting the height of title in FacetGrid
g=sns.catplot(x='Region',
              y='Birthrate',
              data=gdp_data,
              kind='box')
g.figure.suptitle('New Title', y=1.03)
plt.show()






