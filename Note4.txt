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

DF3<-join(DF1,DF2,"id") ## joining if two dataframes has same variables used in plyr package

DF4<-arrange(join(DF1,DF2),id) ## joining by id and arranging it in ascending no "" required due to usage of arrange

-------------------------------------
Week 4

tolower((names(Cameradata))) ## lowe case of all the names of the dataset

strnames=strsplit(names(Cameradata),"\\.") ## command to split the special characters in the variable names

strnames[[1]][3] ## command to get the desired variable name

firstelement<-function(x) {x[1]} ## function to get only the first element of the variable name

sapply(strnames,firstelement) ## get only the first elements from the variable name

names(Cameradata)<-sapply(strnames,firstandthirdelement) ## assigning the new names to the variables

xtabs(Freq~ Sex + Survived,titanicdataset) ## performing cross tabs in titanic data set

xtabs(Freq~ Age + Survived,titanicdataset) ## same

xtabs(Freq~ Class + Survived,titanicdataset) ##  same

if you are a female child first class passenger your chance of suvival from the titanic disaster is best

if you are a male crew member your chance of survival is worst

sub("_",""",names(dataset)) ## remove underscores from dataset
gsub("_",""",names(dataset)) ## remove underscores from variables and values when they are repeated

grep("Alameda",Cameradata$intersection) ## find the  instance of occurence of the word Alameda in intersection variable

grepl("Alameda",Cameradata$intersection) ## displays the same answer as a logical vector of TRUES and FALSES)

grep("Alameda",Cameradata$intersection,value = TRUE) ## The exact rows where Alameda appears comes

nchar("Aravinthan") ## command to count the strings of the character name

substr("Aravinthan Radhakrishnan",1,10) ## command to get the first name


Regular expressions are combinations of literals and meta characters

Literals ##  words of a language
Meta character ## grammar of a language

## literals help us to match only the exact word that is given for search

## metacharacters helps us to match different words or variations of the same word

^ i think ## will match all words in a dataset that starts with i think ,hoewever it cannot match if the word comes in the middle

morning$ ## will match all word mornings at the end of the sentence it cannot match if the word comes in the middle 

[Bb] [Uu] [Ss] [Hh] ## this will match the word Bush in whatever variation they appear in the sentences

^[Ii] am ## will match both Iam and i am that comes at the beginning of the sentences

^[0-9] [a-zA-Z] ## looks for the range of numbers 0 to 9 at the beginning of the sentence and matches the range of letters in the sentence

[^?.]$ ## when the carrot sign is used at the beginning inside the square brackets followed by $ it indicates it needs to look for those sentences not ending with any punctuation marks

9.11 ## the "." signifies it will look for the combination 9 followed by 11 in any variation virtually everything

flood|fire ## not the pipe but or which can match either of these two words that is found in the sentences

flood|fire|hurricane|windfall ## can use any number of words to match these sentences


^[Gg]ood|[Bb]ad ## searches for te word good both starting in caps and small at the beginning or the word bad both with small and big letter anywhere at the sentence not necssarily in the beginning

^([Gg]ood|[Bb]ad) ## searches the word Good or Bad both at upper or lower cases at the starting of the sentence

[Gg]eorge([Ww].\)? [Bb]ush ## that W is optional if it finds it shows otherwise it just looks for the Gerorge bush 

(.*) ## looks for any character repeated any number of times bwtween the parenthesis

+[0-9] (.*) + [0-9] ## looks for atleast 1 number in the range followed by any number of characters between the parenthesis followed by atleast 1 number in the range

[Bb]ush( +[^ ] + +) {1,5} debate ## this looks for atleast one space follwed by not a pace and atleast one space for five times bwtween the word Bush and debate curly braces indicate fixed number of times

+( [a-zA-Z]+) +\1 + ## \1 LOOKS FOR RANGE OF LETTERS THAT REPEATS the same combination of letters after a space

^s(.*)s $$ looks for the longest combination of words that starts and ends with a s
































