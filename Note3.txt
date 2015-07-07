Getting and cleaning data : goal

Raw data - Processing script>- tidy data>-data analysis >- data communication

Raw data
1) original source
2) difficult to use
3) data analyses includes processing
4) may need to be processed once

Processed data :
1) Data ready for analysis
2) Processing includes merging subsetting and transforming
3) standards for processing
4) all steps should be recorded

components of tidy data:

the raw dara
a tidy data set
a code book describing each variable
4) a recipie i took to reach to step 1 to step 3

Components of raw data
1) ran no software
2) did not manipulate any numbers
3) you did not remove any data from the data
4) you did not summarize anything in the data set

tidy data:
1) each variable per coloumn
2) each observation in a different row
3) one table for every kind of variable
4) one primary variable to merge multiple data tables

Code book :
information about variables (including units)
information about the summary choices( mean, sum etc)
from where you got the data

A Rscript where we can go back and extract the raw data from the tidy data( vice versa) tidy data <- raw data <- tidy data

Relative Work directories
----------------------------------------
getwd(".//data") no need to give full path that . fulfills the purpose 
getwd("..//") moves one directory up
-----------------
Absolute Work directories 
("Drivename//username//foldername//filename with extension") full path of the file location
---------------
if(!file.exists("data")) {
+ dir.create("data")}   ## code to check whether  if a file called data  does not exists and create the file in our directory
----------------
download.file() ## command to download file from internet

URL<-"https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD&bom=true"
download.file(URL,destfile = ".//data//cameras.csv") ## assigning the copy location path to a URL variable
                                                       ## using the download.file() command to import the file from net        
                                                       ## dest file command tells in which file in our wd the data should be imported and under what name
list.files(".//data") ## lists the files in the folder name data 
datadownloadeddate<-date() ## date and time at which the file is downloaded from internet
-------------------------------------------------------------------------------------------------
Cameradata<-read.table(file=".//data//cameras.csv",sep=",",header=T) ## read the file into R even read.csv can be used
head(Cameradata) ## read first 10 rows of the dataset
--------------------------------------------------
URL<-"https://data.baltimorecity.gov/api/views/dz54-2aru/rows.xlsx?accessType=DOWNLOAD" ## download the file in xlsx format
download.file(URL,destfile = ".//data//cameras.xlsx")

-------------------------------------------------------
Extensible markup language ## XML
Used to store structured data
used in internet applications
used mostly for web scraping
Components of XML :
Markup-- labels that give text structure
Content -- Actual text of the document

Tags correspond to general labels
Start tag <section>
end tag</section> ## forward slash

elements are specific examples of tag
<Greeting> Hello world <Greeting/>  ## Start Markup followed by content and end markup ##
attributes are components we can add to a tag
<Greeting type ="Welcome"alt="Bonjour/"> 
---------------------------------------------------
XMLURL<-"http://www.w3schools.com/xml/simple.xml"## xml file URL node
doc<-xmlTreeParse(XMLURL,useInternal=TRUE) ## reading the file into R
RootNode<-xmlRoot(doc) ## Get the top node of the XML file
xmlName(RootNode) ## name of the topnode
names(RootNode) ## names of the elements inside the topnode
RootNode[[1]] ## first element of the top node
--------------------------
XPath 
./node ## top level node
.//node ## node at any level
.node[@attr-name] ## node with an attribute name
.node[@attr-name="bob] ## node with attribute name  ="bob"

xpathSApply(RootNode,".//name",xmlValue) ## Xml value of the name element in the topnode

scores<-xpathSApply(doc2,"//li[@class='score']",xmlValue) ## get the specific values of the score should identify class from source
use doc<-htmlTreeParse(XMLURL,useInternal=TRUE) ## reading the file into R in html
-------------------
Javascript object notation

Lightweight data storage

Data are stored in 
Numbers ( double)
Strings (doublequotes)
BOOLEANS (true or false)
Array ( ordered comma separated enclosed in [] )
Object (unordered comma separated collecyion of key value pairs in curly brackets)

https://api.github.com/users/Aravinthan1990/repos ## to get json file using github

jsonData<-fromJSON("https://api.github.com/users/Aravinthan1990/repos") ## import JSON file in R

a<-toJSON(datasetname) ## concert a existing dataframe to a JSON file
----------------------------------------
data table package
James_Bond2<-data.table(Names =c("Sean","Rojer","Pierce"),Movies=c("Dr.NO","Octopussy","Goldeneye"),Gross=c(5000000,100000,4320000)) ## creating a data frame using data table package

tables() ## see the created table in R memory
James_Bond2[2,] ## subsetting the 2nd row of the dataset

when we want subset columns instead of using indexes use names of the coloumn in data table and use specific functions to perform the desired activity

James_Bond2[,list(mean(Gross))] ## applied mean to the coloumn name Gross

James_Bond2[,MonthlyGross:=Gross/12] ## Create a new coloumn in the dataset in datatable package

James_Bond2[,MonthlyGrossgreater100000:=MonthlyGross>100000] ## creating plyr like logical variables

setkey(James_Bond2,Names) ## seting key helps us to subset the dataset based on a variabe

FirstMovie<-James_Bond2['Sean'] ## subsetting based on the name Sean

if two datasets has a same primary key then we can use the set key function like this
setkey(DT,x);setkey(DT2,x) ## this will help us to merge two datasets fast


------------------------------------------------------------------------





























