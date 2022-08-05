# -ANA-505-Week-5-Activity
download.file(url = "https://raw.githubusercontent.com/fivethirtyeight/data/master/airline-safety/airline-safety.csv", destfile = "airline_safety.csv")
airline_safety<- read.csv("airline_safety.csv")
str(airline_safety)
install.packages(package="dplyr")
library(package="dplyr")
mysample <-sample_n(airline_safety, size=15, replace = FALSE, weight = NULL, .env = NULL)
mysample<- as.data.frame(mysample)
write.csv(mysample,file = "mysample.cvs")
save(mysample,file = "mysample.cvs")

piping<-mysample %>% 
  mutate (seats = avail_seat_km_per_week) %>%
  subset(incidents_85_99 < 24) %>%
  dim()%>%
  print()

#TASK: revise this code chunk using piping
mysample2<-mysample
arrange(mysample2, airline)
mysample2<-filter(mysample2, incidents_85_99<25)
mysample2<-rename(mysample2, seats = avail_seat_km_per_week)
mysample3<-select(mysample2, incidents_00_14, incidents_85_99)
mysample4<-summary(mysample3)
print(mysample4)

piping2 <-arrange(mysample, airline)%>% 
  mutate (seats = avail_seat_km_per_week) %>%
  subset(incidents_85_99 < 25) %>%
  select(incidents_00_14, incidents_85_99)%>%
  summary()%>%
  print()
  
  [week5.txt](https://github.com/MahsaKarkhaneh/-ANA-505-Week-5-Activity/files/9265160/week5.txt)
