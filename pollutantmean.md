pollutantmean <- function(directory, pollutant, id = 1:332){
      directory <- ("./specdata")
      pollutiondata <- c()
      datafiles <- as.character(list.files(directory))
      datapath <- paste(directory, datafiles, sep = "/")
      for (i in id){
          temp <- read.csv(datapath[i], header = TRUE, sep = ",")
          pollutant
          remove_na <- temp[!is.na(temp[, pollutant]), pollutant]
          pollutiondata <- c(pollutiondata , remove_na)
      }
      {
        pollutionmean <- round(mean(pollutiondata),3)
        return(pollutionmean)
      }
}