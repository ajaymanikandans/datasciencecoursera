corr <- function(directory, threshold = 0) {
      df <- complete("specdata", 1:332)
      tid <- df[df["njobs"] > threshold,]$id
      corrs <- numeric()
      for(i in tid){
          temp <- read.csv(paste(directory, "/", formatC(i, width = 3, flag = "0"),
                                 ".csv", sep = ""))
          ndf <- temp[complete.cases(temp), ]
          corrs <- c(corrs, cor(ndf$sulfate, ndf$nitrate))
      }
      corrs
}
