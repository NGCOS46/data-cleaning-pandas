![portada](https://github.com/Ironhack-Data-Madrid-Enero-2022/w3-pandas-project/blob/main/images/portada.jpg)

# W2 Project - Data cleaning & wrangling

The goal of this project is to combine everything you have learned about data wrangling, cleaning, and manipulation with Pandas so you can see how it all works together. For this project, you will start with this messy data set Shark Attack. You will need to download it, import it, use your data wrangling skills to clean it up, prepare it to be analyzed, and then export it as a clean CSV data file. Some graphs to better understand the data will surely be useful!!

## TO DO's

1. Explore the data and write down what you have found
   - you can use: `df.describe()`, `df["column"]`, etc.
1. Use at least 5 data cleaning techniques inside a file named `clean.ipynb`
   - null values, columns drop, duplicated data, string manipulation, apply fn, categorize, regex, etc.
1. Show data that validates the conclusions based on your hypoteses in a file named `analysis.ipynb`


## Suggested Ways to Get Started

- Examine the data and try to understand what the fields mean before diving into data cleaning and manipulation methods.
- Break the project down into different steps - use the topics covered in the lessons to form a check list, add anything else you can think of that may be wrong with your data set, and then work through the check list.
- Use the tools in your tool kit - your knowledge of Python, data structures, Pandas, and data wrangling.
  Work through the lessons in class & ask questions when you need to! Think about adding relevant code to your project each night, instead of, you know... procrastinating.
- Commit early, commit often, don’t be afraid of doing something incorrectly because you can always roll back to a previous version.
- Consult documentation and resources provided to better understand the tools you are using and how to accomplish what you want.

## How to deliver the project

1. Create a new repo with the name `data-cleaning-pandas` on your github account.
   - Create a `README.md` file on repo root with project documentation. Make sure to include as much useful information as possible. Someone that finds the README.md should be able to fully get a gist of the project without browsing your files.
   - Include a `.gitignore`
   - At least 1 jupyter notebook is required
   - Including your functions in a `src.py` is very, very highly reccommended (maybe even mandatory, check with your instructors)
   - **DO NOT UPLOAD SHARKs ATTACK DATASET TO GITHUB**
2. Open an `Issue` on this repo and paste your own repo's link.

## Links & Resources

- <https://www.kaggle.com/teajay/global-shark-attacks>
- <https://numpy.org/doc/1.18/>
- <https://pandas.pydata.org/>
- https://docs.python.org/3/library/functions.html
- https://plotly.com/python/
- https://matplotlib.org/
- https://seaborn.pydata.org/
- https://pandas.pydata.org/docs/
- https://towardsdatascience.com/beware-of-storytelling-with-data-1710fea554b0?gi=537e0c10d89e

# W2 Project - Data cleaning & wrangling.Steps I took to clean the data:
1.	Dealing with nulls:
a.	first, we eliminated the nulls of the data frame which contained all nulls in the rows, because we would have no relevant information to get out of these rows.
b.	after that, we reset the index, and saw using the method tail that the remaining rows had a lot of nulls, and the rest was filled with zeros or xxx or something else that wasn`t relevant, so by creating a variable umbral, we discarded the rows that had 80% or more filled with nulls because even if they had the information it would be too little to even appreciate the data.
c.	again, we reset the index and lost a couple of rows. In this next step we saw that in the date column, there was information before Christ and letters, describing the events, so what we did is not consider relevant any date that could not be passed into date time, using the date_time method of numpy and eliminate those that were not being used in the format, lowering the number of rows significantly.
2.	- the next step was editing the columns so that we wouldn't have any errors of writing so we eliminated the spaces,          so to eliminate the possibility of spending endless time on stupid mistakes, that could be fixed by this simple step.
a.	after that, we counted all the null values from the data frame to see what was left. My plan of action was simple, I decided to eliminate the rows under 100, of any column, not relevant to my case study. I understood that those rows would not make a difference in the grand scheme of things.
b.	after that, I wanted to speed up the process and saw that for the columns that had over 100 but less than 800 nulls, I would look into them and find a way to relate them to each other. So I created a function to see the null elements of a column called def visualizar_nulos.
c.	after seeing that the nulls I looked at, contained the necessary information to be in the whole row I just changed the nulls for unknown.
3.	- in the case of the column name I decided that if the name was null, but in the row the sex was there, the name of          the man would be male and the name of the female would be female, for it not to be so boring with unknown. and I             created another function that if both were nulls the name would be unidentified. Also, I replaced the rest of the          sex column with unknowns, so that the information to be relevant would be looked at other elements of the row. I             did the same with Age.
a.	for the injury column I created a function that would relate the null injury to the activity, because if you don't know the injury, you could just combine the name of the activity with the injury, so if in a row we had a null in injury, but the activity was swimming, the injury would be swimming injury.
b.	for the time column I decided that if the time wasn't known it would be between 0:00- and 0:24.
4.	for the species column, there was much cleaning to do. so I created a dictionary of the column counted the                   elements to get repetitions, and eliminated all numbers or hyphens with a loop. again I tried to clean all the              elements that preceded the shark word, the separate a, and m, the word to, and the left part of the elements               separated by the coma. Even so, there was still much cleaning to do that I lack the skills to do. Then with a               loop, I put back the elements into the species column, overwriting the previous rows.
a.	after that replaced all the null values and 1 for unknown in the species value

b.	I did the same with unnamed 22 and unnamed 33 because all of the elements were nulls so I replaced them with zeros

2.	Modifying elements to be better looking:
c.	the year column had the year and a .0 next to it so I converted the year into a year into an int so that I could only see the number and be easier to find.
d.	I did the same with the original order and converted the number to an int value
e.	after that, I eliminated all the rows that had 80% unknown or zero values, because even if they contained information it would not be relevant to the case study.
f.	for case numbers 1, and 2 because they are dates but with a letter attached. I converted the elements into a                string, replace the . for a -, and eliminated the a and b. then I converted it to date time.
g.	for the pdf column I eliminated the date before the - and only kept the name.pdf element.
h.	the last thing I did was created and dealt with the outlier rows, that would mess with the general statistical calculations, so I eliminated them from the list, to get clearer results.



