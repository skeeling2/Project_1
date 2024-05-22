# COVID-19 Data Analysis
#This repository contains data for analyzing COVID-19 data across different continents.
#Table of Contents
#Introduction
#Data
#Usage
#Scripts
#Results

#Introduction
#This project aims to analyze COVID-19 data from various continents. The analysis includes visualizing the trend of smoothed new deaths and performing statistical tests to understand the relationship between different variables.
#Data
#The data used in this project includes:
#date: The date of the recorded data.
#continent: The continent where the data was recorded.
#new_deaths_smoothed: The number of new deaths smoothed over a period.
#'cardiovasc_death_rate':Cardiovascular death rate data in continents
#'diabetes_prevalence': Diabetes prevalence data in continents
#'median_age':Median age in continents
#'smokers': Male and female smokers in continents
    
    
    # Dependencies and Setup
import os
import pandas as pd
import numpy as np
from pathlib import Path
import plotly as py
import matplotlib.pyplot as plt
from scipy import stats
from scipy.stats import linregress
from scipy.stats import pearsonr
import plotly.graph_objects as go
import plotly.io as pio


Data Cleaning and Preparation
Load the data into a pandas DataFrame.
Visualization
To visualize the smoothed new deaths over time for different continents, use the plot_new_deaths.py script:

# Read the COVID-19 data 
​
COVID_df = pd.read_csv('/owid-covid-data.csv')
​

import pandas as pd
import plotly.graph_objects as go
​
# Load your data
df = pd.read_csv('path_to_your_data.csv')
​
# Ensure 'date' column is in datetime format
df['date'] = pd.to_datetime(df['date'])
​
# Function to create traces for each continent
def create_trace(continent, color):
    filtered_df = df[df['continent'] == continent].groupby('date')['new_deaths_smoothed'].sum().reset_index()
    return go.Scatter(
        x=filtered_df['date'],
        y=filtered_df['new_deaths_smoothed'],
        mode='lines',
        name=continent,
        marker=dict(color=color)
    )
​
# Create traces for each continent
trace1 = create_trace('Asia', 'green')
trace2 = create_trace('Europe', 'red')
trace3 = create_trace('Africa', 'black')
trace4 = create_trace('North America', 'blue')
trace5 = create_trace('South America', 'brown')
​
# Create the figure and add the traces
fig = go.Figure()
fig.add_trace(trace1)
fig.add_trace(trace2)
fig.add_trace(trace3)
fig.add_trace(trace4)
fig.add_trace(trace5)
​
# Customize layout
fig.update_layout(
    title='New Deaths Over Time by Continent',
    xaxis_title='Date',
    yaxis_title='New Deaths',
    template='plotly_white'
)
​
# Save the plot as a PNG file
fig.write_image("output/Trace_vs_New_Death.png")
​
# Show the plot
fig.show()
​
Create box plot for cardiovascular death rate

#Example
​
# Cardivascular death rate continent wise
​
plt.figure(figsize=(10, 6))
box_plot = filtered_df.boxplot(column='cardiovasc_death_rate', by='continent', grid=False)
​
# Customize the plot
plt.title('Box Plot of Cardiovascular Death Rate by Continent')
plt.suptitle('')  # Remove the default title to avoid duplication
plt.xlabel('continent')
plt.ylabel('Cardiovascular Death Rate')
plt.xticks(rotation=45)  # Rotate x-axis labels if necessary
plt.tight_layout()
plt.savefig("/Users/Apple/Desktop/COVID_19_Meenakshi/Resources/BoxPlot_CVDR.png")
Statistical Analysis

#Example
from scipy import stats
import matplotlib.pyplot as plt
​
# Example: Scatter plot and linear regression for Europe
x_values = df[df['continent'] == 'Europe']['cardiovasc_death_rate']
y_values = df[df['continent'] == 'Europe']['female_smokers']
​
slope, intercept, rvalue, pvalue, stderr = stats.linregress(x_values, y_values)
regress_values = x_values * slope + intercept
​
plt.figure(figsize=(10, 6))
plt.scatter(x_values, y_values, alpha=0.75, edgecolors='Orange', linewidths=1, label='Year_2020')
plt.plot(x_values, regress_values, 'r-')
plt.annotate(f'y = {round(slope, 2)}x + {round(intercept, 2)}\n$p$-value = {pvalue:.2e}', (x_values.min(), y_values.min()), fontsize=12, color='r')
plt.title('Europe: Cardiovasc Death Rate vs Female Smokers')
plt.xlabel('Cardiovasc Death Rate')
plt.ylabel('Female Smokers')
plt.legend()
plt.grid(True)
plt.tight_layout()
​
plt.savefig("output/Europe_cardiovasc_death_rate_vs_female_smokers.png")
plt.show()
​
Create scatter plot

#Example
​
# Scatter Plot:Europe:cardiovasc_death_rate vs female_smokers
​
x_values = Reduced_Europe_Comorbidity_df['cardiovasc_death_rate']
y_values = Reduced_Europe_Comorbidity_df['female_smokers']
​
# Perform linear regression
slope, intercept, rvalue, pvalue, stderr = stats.linregress(x_values, y_values)
regress_values = x_values * slope + intercept
line_eq = f'y = {round(slope, 2)}x + {round(intercept, 2)}'
​
# Create a scatter plot with linear regression
plt.figure(figsize=(10, 6))
plt.scatter(x_values, y_values, alpha=0.75, edgecolors="Orange", linewidths=1, label="Year_2020")
plt.plot(x_values, regress_values, "r-")
plt.annotate(line_eq, (x_values.min(), y_values.min()), fontsize=12, color='r')
​
plt.title(f"Europe:cardiovasc_death_rate vs female_smokers")
print(f"The r-value is: {rvalue}")
print(f"slope:{slope}")
print(f"intercept:{intercept}")
print(f"rvalue (Correlation coefficient):{rvalue}")
print(f"stderr:{stderr}")
​
line_eq = "y = " + str(round(slope,2)) + "x + " + str(round(intercept,2))
​
print(line_eq)
​
plt.xlabel('Cardiovasc_death_rate')
plt.ylabel('Female_smokers')
plt.legend()
plt.grid(True)
plt.tight_layout()
​
plt.savefig("output/Europe_cardiovasc_death_rate vs female_smokers.png")
​
plt.show()


#Results
#The results of the analysis, including the plots and statistical summaries, are saved in the output directory.