# Project_KY

Examining Jefferson (KY) Census Tracts' Social Vulnerability Through the Lens of the CDC Social Vulnerability Index (SVI)

# I. Introduction

The CDC SVI refers to social vulnerability as the potential negative effects on communities caused by external stresses on human health, furthermore that by reducing social vulnerability human suffering and economic losses could improve.

What is the CDC Social Vulnerability Index? The CDC SVI is a tool (to help local officials), which uses U.S. Census data (American Community Survey data) to determine the social vulnerability of every census tract. Census Tracts are subdivisions of counties for which the Census collects statistical data. The first version of the SVI was created in 2011 by ATSDR's Geospatial Research, Analysis, and Services Program. GRASP continues to create and maintain the SVI. The most current data is the 2018 SVI data, which was released in March 2020.

# II. Importing Data

The data used here was acquired from the Centers for Disease Control and Prevention/ Agency for Toxic Substances and Disease Registry/ Geospatial Research, Analysis, and Services Program's site, https://www.atsdr.cdc.gov/placeandhealth/svi/data_documentation_download.html.
The data selections from this site for this project are as follows:
1.  Years: 2014, 2016, and 2018
2.  Geography: Kentucky
3.  Geography Type: Census Tracts
4.  File Type: CSV Type
The CDC SVI Documentation was also available on the same site page.

Once the data was downloaded to the local HD (Windows 10) the Data and Project-KY folders were created inside Project_KY and were opened with Anaconda/Jupyter Lab, https://docs.anaconda.com/anaconda/install/, with Python3 Programming Language, https://www.python.org/downloads/, and the project's repository is at GitHub, https://desktop.github.com/. You can go to any of these sites to install any of these products.

# III. Cleaning Data

Pandas and Numpy were installed to read the CSV files and to clean and sort data, for example by using functions like, 'replace', to change incalculable -9.99e+02 with Nan (incalculable for this data because 0 TOTPOP or unavailable values), 'unique', to determine the original unique id when first created (for year 2014 ' Jefferson' was created with a blank space before Jefferson, and it changed in the following years to 'Jefferson', no blank space). This project examines Jefferson Census Tracts' vulnerability numbers, which requires redefining the Kentucky DataFrame to County and selecting Jefferson Census Tracts only. The total population and total square miles were checked against other sources to ensure the proper values were in placed and the 15 vulnerability factors were segregated by their respective themes and examined within 2014, 2016, and 2018 data in preparation for graph visualization. 

# IV. Data Visualization

Some of the libraries and functions used in this project's data visualization (graph):

* %matplotlib notebook
* matplotlib
* get_backend()
* pyplot 

**NOTES:
-inline was used here to work with JupyterLab, if using Jupyter Notebook try %matplotlib notebook
-in some instances numpy had to be re-imported**

The code for graph visualization was intended to capture the number of factor estimates (i.e., four under theme 1) within their respective themes, (i.e., Socialeconomic theme 1) in 2014, 2016, and 2018 data years, all within one graph. The mean was calculated and used for these graphs.

Let's take theme 1, Socialeconomic Status and its four factors; Below Poverty (persons below poverty), Unemployment (age 16+ unemployed), Income (per capita income), and No High School Diploma (age 25+ with no high school diploma).  Does the data indicate substantial changes during these periods? Are the changes increases or decreases or no changes? Are the changes material? Will the opinions about this data change once one theme and its factors are compared to other individual themes' numbers, or compared against the overall numbers? Theme 1-Socialeconomic Status' graph shows a  consecutive drop of all but income--a consecutive increase around the three years graphed. What does this mean? Some observations could be, the drop in 'no high school diploma' assisted with higher incomes, or higher incomes helped lift unemployment and below poverty numbers, for example.

The same process was applied to theme 2, theme 3, and theme 4, with their respective social factors.

![CDC SVI](https://www.atsdr.cdc.gov/placeandhealth/svi/documentation/pdf/Documentation_Image.jpg)


# V. Model

The model is performed with 2018 data only. The data was again segregated by themes and after modeling the four themes the overall numbers were plotted (i.e., X as the themes as factors and y as the percentile rankings as labels. A percentile ranking represents the proportion of tracts that are equal to or lower than a tract, re: social vulnerability, (i.e., an 0.85's CDC SVI ranking signals that 85% of tracts in KY are less vulnerable than the tract you are examining and that 15% of tracts in KY are more vulnerable. 

Some of the libraries and functions used in this project's models (plotting):

* Pandas
* seaborn
* scikit-learn
* model_selection 
* train_test_split
* neighbors
* KNeighborsRegressor with n=5
* matplotlib
* cm or colormap
* plotting
* scatter_matrix

After the X=factors and y=labels are defined, X as THEME# and y as RPL_THEME#, the training and test split process follows with its default of 75% training and 25% test. Note: a random_state of zerro (0) was used throughout, on the split.

After the scatter_matrix a KNeighborsRegressor was applied.
Note: n_neighbors = 5 was used here but it was also tested with the values of 1, 10, and 20. You may try these versions of the code to test the model.
The X_train and y_train were applied to the fit function and a score of 0.86936 was achieved after running the X_test and y_test under the score function. 

Two single tracts from the Jefferson data were additionally tested with the prediction function after each theme model. 

The final model consisted of all themes as overall vulnerability as the X or factors and y as the overall percentile rankings or RPL_THEMS.

The following links provide access to KY, Jefferson Census Tracts, and other maps:

https://svi.cdc.gov/Documents/CountyMaps/2018/Kentucky/Kentucky2018_Jefferson.pdf

https://svi.cdc.gov/prepared-county-maps.html



Something to consider are the total population numbers for those same years:

2014: 751,485
2016: 759,724 an increase of 8,239 from 2014
2018: 767,154 an increase of 7,430 from 2016
A total population increase of 15,669 from 2014 to 2018 survey. 

One could suggest an entry to Jefferson Census Tracts averaging higher income earners and/or with higher education levels or even crediting higher education graduation and technology and trade certifications could of contributed to some positive changes (this data does not contain higher education nor technology or trade certification information).




This project only begins to explore the questions behind the data. The segregated factors and themes contain additional data this project did not graph or model. In addition individuals could search for other counties or even their own tract in Kentucky.