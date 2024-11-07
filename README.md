# 2024.11.8
##data will be made available on request.
some code
setwd("D:/doctor/24diversity/liying/data/analysis")
##绝对丰度相对丰度转换
yu2<- read.csv(file="fungall.csv",header=T,row.name=1)
#转置
df<-t(yu2)
#相对丰富度转化
data.prop<-df/rowSums(df)
#由于数据量大，转化完直接写出后打开不方便，因此对数据进行转置
yu2<-t(data.prop)
write.csv(yu2,file="reaallc.csv")
#div
a<- read.csv(file="otuf.csv",header=T,row.name=1)
a <- t(a)
design <- read.csv(file="gg.csv",header=T,row.names = 1)
library(vegan)
shannon <- diversity(a,"shannon")
simpson <- diversity(a,"simpson")
richness <- rowSums(a>0)
richness
chao1 <- estimateR(a)[2,]
chao1
group <- design['group']
group
data <- data.frame(richness,chao1,shannon,simpson)
data1 <- data.frame(data,group)
write.csv(data1,file="diversityf.csv")
head(group)
View(design)
