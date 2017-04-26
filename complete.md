complete <- function(directory, id = 1:332){
  directory <- ("./specdata")
  datafiles <- as.character(list.files(directory))
  datapath <- paste(directory, datafiles, sep = "/")
  df<- data.frame(id = integer(length(id)), njobs = integer(length(id)))
  j = 1
  for (i in id){
    temp <- read.csv(datapath[i], header = TRUE, sep = ",")
    good <- complete.cases(temp)
    temp2 <- temp[good,]
    njob <- nrow(temp2)
    df$id[j] <- i
    df$njobs[j] <- njob
    j <- j+1
  }
  df
}