#R code
install.packages("dplyr")
install.packages("tidyr")
library(dplyr)
library(tidyr)
data.frame<- read.csv("us_perm_visas.csv")
str(data.frame)
visa = data.frame %>% select(case_received_date, case_status, class_of_admission,
country_of_citizenship, decision_date, employer_city, employer_decl_info_title,
employer_name, employer_num_employees, employer_state, foreign_worker_info_education,
foreign_worker_info_major, job_info_experience, job_info_job_title, pw_amount_9089)
visa = data.frame(visa %>% na_if("") %>% na.omit)
sum(is.na(visa))
colnames(visa)[15] <- c("work_pay")
