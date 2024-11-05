**November 4, 2024** <br>
**MPAD2003A**<br>
**Rana Mohammed**<br>
**Presented to Jean-Sébastien Marier**<br>

# Midterm Project: Exploratory Data Analysis (EDA)

Use one hashtag symbol (`#`) to create a level 1 heading like this one.

## Foreword

For this assignment, you must extract data from a dataset provided by the instructor. You must then clean and analyze the data, create exploratory charts/visualizations, and find a potential story idea. Your assignment must clearly detail your process. You are expected to write about 1500-2000 words, and to include several screen captures showing the different steps you went through. Your assignment must be written with the Markdown format and submitted on GitHub Classroom.

I have been assigning different versions of this project to my digital journalism and data storytelling students for a few years now. Its structure was inspired by the main sections/chapters of [*The Data Journalism Handbook*](https://datajournalism.com/read/handbook/one/). This version was further inspired by the [Key Capabilities in Data Science](https://extendedlearning.ubc.ca/programs/key-capabilities-data-science) program offered by the University of British Columbia (UBC).

**Here are some useful resources for this assignment:**

* [GitHub's *Basic writing and formatting syntax* page](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [The template repository for this assignment in case you delete something by mistake](https://github.com/jsmarier/jou4100_jou4500_mpad2003_project2_template)

Did you notice how to create a hyperlink? In Markdown, we put the clickable text between square brackets and the actual URL between parentheses.

And to create an unordered list, we simply put a star (`*`) before each item.

## 1. Introduction

This assignment analyzes a subset of a City of Ottawa dataset called "2024 Service Requests" that provides a summary of requests for services that require action by City staff. The data extracted for this assignment is a smaller dataset of the original that contains only the data from August 2024.

The data was collected from 311 Contact Centre, Client Service Centre, 311 Email, and Web-based Self-Service portal. The data is organized by ward and shows the responsible city department and service request description.

**The data includes:**
- Service Request ID and number
- Status
- Description of request
- Type
- Opened and Closed Date
- Address, Latitude, and Longitude
- Ward Number that request relates to and Channel is was created in.

**Links to datasets:**
 [Open Ottawa original dataset](https://open.ottawa.ca/documents/65fe42e2502d442b8a774fd3d954cac5/about)
[CSV File of assignment dataset](https://raw.githubusercontent.com/jsmarier/course-datasets/refs/heads/main/ottawa-311-service-requests-august-2024.csv)

**This Assignment will discuss:**
1. Getting data
1. VIMO Analysis
1. Cleaning Data
1. Exploratory Data Analysis
1. Potential Story
1. Conclusion
1. References

## 2. Getting Data

Use two hashtag symbols (`##`) to create a level 2 heading like this one.

**Importating Data into Google Sheets**
After clicking the csv file it will open as text on a website. To fix this open up your terminal and type cd and your directory. This will move the csv file to your chosen directory. I moved mine to downloads.

[insert image]

Then you should type curl with the url of the file after. Curl is a command-line tool that will transferr data with URL's. 

The csv should then be saved in you computer
[insert image]

Now to import the data into google sheets, open a blank sheet and go to file at the top left. Clcik on import.
[insert image]

this should pop up, go to upload and brows for the csv file or directly drag it into the box.

once you open the file, change the separator type to Comma and press import data.
[insert image]

This is what it should look like.

**General observations**
There are 11 columns and 28539 rows. 
The data looks messy and crowded. The desciption inlcudes both french and english in one column which makes it too long. There is alot of missing data

**Specific observations**

Column C features nominal feautures with types of service request. Column H shows the latitude with continuous varables, most of the data is missing though.

**Question/Hypothesis**

Do some wards get more of a specific type of service request such as Garbage and Recycling than other wards?

I hypothesis that garbage and Recycling reqests are more common in dense wards, such as ward 14 (Somerset) which covers the downtown and centretown area.

Are certain 


To include a screen capture, use the sample code below. Your images should be saved in the same folder as your `.md` file.

![](import-screen-capture.png)<br>
*Figure 1: The "Import file" prompt on Google Sheets.*

**Here are examples of functions and lines of code put in grey boxes:**

1. If you name a function, put it between "angled" quotation marks like this: `IMPORTHTML`.
1. If you want to include the entire line of code, do the same thing, albeit with your entire code: `=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)`.
1. Alternatively, you can put your code in an independent box using the template below:

``` r
=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)
```
This also shows how to create an ordered list. Simply put `1.` before each item.

## 3. Understanding Data

### 3.1. VIMO Analysis

Use three hashtag symbols (`###`) to create a level 3 heading like this one. Please follow this template when it comes to level 1 and level 2 headings. However, you can use level 3 headings as you see fit.

I will assess the quality, accuracy, and reliability of the data by conducting a VIMO analysis, mainly focusing on the three columns mentioned in the previous section.
VIMO is an acronym for valid, invalid, missing and outlier data values.

For data to be accurate, the values are valid, not blank and within a valid range.

**Invalid values**

Invalid data are values that are impossible or make no sense in the dataset.

**Missing**
There are many missing values in this dataset including the descriptions in column d for most water and the environment type in column C.
Most of the values for Latitude, longitude, and address are missing as well.

**Outliers**
There isn't any noticable outliers in the dataset

**Is the data reliable**
Since there are no invalid or outliers data we can canclude that the data is reliable, there are a few missing values but that does not effect the understanding of the dataset.



Support your claims by citing relevant sources. Please follow [APA guidelines for in-text citations](https://apastyle.apa.org/style-grammar-guidelines/citations).

**For example:**

As Cairo (2016) argues, a data visualization should be truthful...

### 3.2. Cleaning Data

The first thing I did to clean my data was resize the column sizes to see all the values. I did this by selecting everything and double clicking between 2 columns which automatically resizes all the columns.
[insert image]

I wanted to be able to individually look the different types of requests, status, and channel so I applied filters by seleting the first row, right clicking and pressing apply filters. Then to know what column I am looking at, I froze the first row by selecting it, going to view, freeze and selecting 1 row. This way the titles will show no matter how far down I scroll.
[insert image]

Column D is too crowded and messy because it includes both english and french descriptions. I deleted the french part by using the SPLIT function. first I right-clicked on the column to make 1 column on the right then did that again till I had 2. On the second row of the blank I typed =SPLIT(D2; "|"). This function splits the text at | which divides the french and english descriptions. I applied this function to both entire columns by double clicking on the bottom right circle of the box because dragging it down is too time consuming.
[insert image]

In order to delete the original column I selected both new columns, copied them then went to edit at the top left corner and pressed paste special, paste values only. 

Since I deleted the french portion, I also went ahead and removed the french part of the titles manually for a cleaner look.

Lastly, I deleted the address, langitude, and longitude columns because I don't find it important to know where the request was made.Most of the values for them are missing because they're only displayed for  public service requests.

### 3.3. Exploratory Data Analysis (EDA)

Insert text here.

**This section should include a screen capture of your pivot table, like so:**

![](pivot-table-screen-capture.png)<br>
*Figure 2: This pivot table shows...*

**This section should also include a screen capture of your exploratory chart, like so:**

![](chart-screen-capture.png)<br>
*Figure 3: This exploratory chart shows...*

## 4. Potential Story

Insert text here.

## 5. Conclusion

Insert text here.

## 6. References

Include a list of your references here. Please follow [APA guidelines for references](https://apastyle.apa.org/style-grammar-guidelines/references). Hanging paragraphs aren't required though.

**Here's an example:**

Bounegru, L., & Gray, J. (Eds.). (2021). *The Data Journalism Handbook 2: Towards A Critical Data Practice*. Amsterdam University Press. [https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153](https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153)
