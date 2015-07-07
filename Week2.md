MySQL:
Free and widely used open source database

Data are structured in
1) Database
2) tables within databases
3) fields within databases
4) each row is called a record
5) All data tables should have a primary variable

6) dbGetQuery(function to get data from my SQL database dbdisconnect( disconnecting the database)
-------------------------------------------------
HDF- hierarchial data format
group contains zero or more data sets and metadata

group header with group names and a list of attributes

group symbol table with of list of objects in that group

datasets of multidimensional array of data elements with meta data

have a header with name ,datatype ,dataspace,storage layout

have a data array with data

h5createdfile ## command to create hD5 file in R

-------------------------

Reading data from Web ## http://www.thecricketmonthly.com/story/888421/cook-s-pickle ## url

con<-url("http://www.thecricketmonthly.com/story/888421/cook-s-pickle") ## open a connection

htmlcode<-readLines(con) ## read the data into R

close(con) ## always close the connection once you extracted the data

will get data in unstructured form use XML package see details below

span<-xpathSApply(HTML,"//span",xmlValue) ## webscraping data from cricker monthly

title<-xpathSApply(HTML,"//title",xmlValue) ## TITLE OF THE ARTICLE
------------------------------------------------
Application programing interfaces
 getting data from face book and twitter etc refer webpages saved in favourites

 fb_Auth<-fbOAuth(app_id="942682755752791", app_secret="ce2ad0abe906adf79cb5387ebd47b138", extended_permissions = TRUE) ## attempt to scrape data from facebook 
-----------------------------
Week 3 
James_Bond2[,1] ## subsetting the first coloumn of a data frame 

James_Bond2[,"Movies"]  ## alternate method to subset columns from a dataset

James_Bond2[1:2,1] ## first 2 elements of the first coloumn of a dataset

James_Bond2[(James_Bond2$Movies == "Goldeneye"& James_Bond2$Names == "Pierce"),] ## subsetting rows based on specific logical statements

James_Bond2[(James_Bond2$Movies == "Goldeneye"| James_Bond2$Names == "Pierce"),] ## or statements

sort(James_Bond2$MonthlyGross) ## sorting data 

sort(James_Bond2$MonthlyGross,descending=T) ## sorting in descending order

James_Bond2[order(James_Bond2$Names,James_Bond2$Movies),] ## ordering the dataset based on a variable

James_Bond2$BoxOffice<-c("Superhit","Poor","Goodshow") ## adding a new variable to dataset

James_Bond2<-cbind(Directors=c("Martin Campbell","Peter Hunt","Terence Young"),James_Bond2) ## coloumnbind a new variable to the left of the dataset

head(restdata,n=3) ## seeing top 3 rows of a datset

tail(restdata,n=3) ## seeing bottom 3 rows of a datset

summary(restdata) ## gives a short summary of the dataset

str(restdata) ## gives info about the structure of the dataset 

quantile(restdata$councilDistrict,na.rm=T) ## gives the quantile distribution of the quaantitative variable in a dataset


table1<-table(restdata$zipCode,useNA ="ifany") ## make table in a dataset

table2<-table(restdata$councilDistrict,restdata$name) ## multidimensional table

table(restdata$zipCode == c(21206,21231,21224)) ## find whether a specific variable equals a value

zipcode_restaurants<-restdata[restdata$zipCode == c("21206","21231","21224"),] ## subsetting datasets based on zipcodes

performing crosstabs

DF=as.data.frame(UCBAdmissions) ## CONVERTING A DATASET INTO A DATAFRAME

xtabs(Freq~ Gender + Admit,DF) ## CROSS TABS specify the relatonship between different variables

xtabs(Freq~ Gender + Dept,DF) ## how many Males and Females in different departments

print(object.size(restdata),units = "Mb") ## command to identify memory space dataset is occupying R memory

restdata$wrongzipcode<-ifelse(restdata$zipCode<0,TRUE,FALSE) ## IF ELSE TO IDENTIFY negaive valyes zip codes

restdata2<-mutate(restdata,zipGroups=cut2(zipCode,g=4)) ## creating a new variable based on a existing variable in a dataset and appending it to a new dataset object

new_mtcars<-melt(mtcars,id=c("gear","cyl"),measure.vars = c("hp","mpg","drat")) ## melt the dataset into a id and measure variables makes the data lean

cyldata<-dcast(new_mtcars,cyl~variable,mean) ## dcasting a dataset according to our requirement

tapply(InsectSprays$count,InsectSprays$spray,sum) ## applying a tapply for sum of insectspray counts across sprays
-----------------------
Main dplyr commands :
select()
filter()
mutate()
arrange() ## use desc(varname) for reverse ordering
summarise()
group_by()
 ------------------------
merge(reviews,solutions,by.x= "solution_id",by.y="id" ,all=TRUE) ## IT MERGES THE SOLUTION_ID of reviews dataset with the id of the solutions dataset 
if what coloumns to be merged is not given it merges according to the variables common in both datasets

intersect() ## command to see the common variables in both datasets






