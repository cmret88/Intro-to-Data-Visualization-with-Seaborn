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
