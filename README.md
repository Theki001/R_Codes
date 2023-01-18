# R_Codes
Basic &amp; Intermediate R
#Installing tidyverse and factoextra
install.packages("tidyverse")
install.packages("factorextra")

#Uploading data in R
pharma.data<- read.csv("C:/Users/Lenovo/Downloads/Pharmaceuticals.csv")
view(pharma.data)

#Normalize data using sapply()
sapply(pharma.data[,3:11],scale)

#Using kmeans algorithm
library(tidyverse)
library(factoextra)

#Determining the number of clusters
fviz_nbclust(sapply(pharma.data[,3:11],scale),kmeans,method="wss")
fviz_nbclust(sapply(pharma.data[,3:11],scale),kmeans,method="silhouette")
fviz_nbclust(sapply(pharma.data[,3:11],scale),kmeans,method="gap_stat")

#Creating clusters with k-means
kmeans(sapply(pharma.data[,3:11],scale),centers = 2,iter.max = 100,nstart = 100)

#Creating cluster biplots
fviz_cluster(kmeans(sapply(pharma.data[,3:11],scale),centers = 2,iter.max = 100,nstart = 100),data=sapply(pharma.data[,3:11],scale))

#Six centers
#Creating clusters with k-means
kmeans(sapply(pharma.data[,3:11],scale),centers = 6,iter.max = 100,nstart = 100)

#Creating cluster biplot
fviz_cluster(kmeans(sapply(pharma.data[,3:11],scale),centers = 6,iter.max = 100,nstart = 100),data=sapply(pharma.data[,3:11],scale))
