install.packages(c("ggplot2", "reshape2", "dplyr"))

library(ggplot2)
library(reshape2)
library(dplyr)

# ggplot will handle and remove all of the missing values

# We are going to analyze COVID-19 data based on the follow criteria:
  # 1. Cases
  # 2. Deaths
  # 3. Vaccinations
  # 4. Testing

df <- read.csv("Desktop/owid-covid-data.csv")
head(df)
tail(df)
str(df)


#1. Cases 

# Are the number of new cases rising or falling per day?

ggplot(df, aes(x = date, fill = new_cases)) + 
  theme_bw() +
  geom_bar() +
  labs(y = "Total Cases per Million",
       x = "Time Progression ->",
       title = "Total Cases per Day") + 
  theme(plot.title = element_text(hjust = 0.5)) 

# 1a. In North America?

#create North America variable
north_america <- df %>%
  filter(continent == "North America")

#filter for North American rows 
north_america %>%
ggplot(data = df, aes_(x = date, y = continent, fill = new_cases)) +
  geom_bar() +
  labs(y = "Total Cases per Million",
       x = "Time Progression ->",
       title = "Total Cases per Day") +
  theme(plot.title = element_text(hjust = 0.5))

# 1b. In Europe?

#create Europe variable
europe <- df %>%
  filter(continent == "Europe")

#filter for European rows 
europe %>%
  ggplot(data = df, aes_(x = date, y = continent, fill = new_cases)) +
  geom_bar() +
  labs(y = "Total Cases per Million",
       x = "Time Progression",
       title = "Total Cases per Day ->") +
  theme(plot.title = element_text(hjust = 0.5))

# We can see that the number of new cases is falling per day for Europe and North America.

# 2. Deaths

# 2a. How many deaths from COVID-19 have been reported per continent? 
# We have data spanning from 1/2020 to 3/2021.

ggplot(df, aes(x = continent, fill = total_deaths)) + 
  theme_bw() +
  geom_bar() +
  labs(y = "Total Deaths per Million",
       title = "Total Deaths based on Continent") +
  theme(plot.title = element_text(hjust = 0.5))

# 2b. Is the number of deaths in each continent rising or falling? 

ggplot(df, aes(x = date, fill = total_deaths)) +
  theme_bw() +
  facet_wrap(~ continent) +
  geom_density(alpha = 0.5) +
  labs(y = "Total Deaths per Million",
       x = "Time Progression ->",
       title = "Falling Rates of COVID-19 Deaths") +
  theme(plot.title = element_text(hjust = 0.5))

# They are all falling in every continent.

# 3. Vaccinations

# 3a. Graph the rate of fully vaccinated people in each continent over time. 

ggplot(df, aes(x = date, fill = people_fully_vaccinated)) +
  theme_bw() +
  facet_wrap(~ continent) +
  geom_density(alpha = 0.5) +
  labs(y = "Total Vaccines per Million",
       x = "Time Progression ->",
       title = "Vaccine Rollout per Continent") +
  theme(plot.title = element_text(hjust = 0.5))

# 3b. Is vaccination rate rising or falling over time?

ggplot(df, aes(x = date, fill = new_vaccinations)) +
  theme_bw() +
  facet_wrap(~ continent) +
  geom_density(alpha = 0.5) +
  labs(y = "Total Vaccines per Million",
       x = "Time Progression ->",
       title = "Vaccine Rollout Rate per Continent") +
  theme(plot.title = element_text(hjust = 0.5))

# 4. Testing 

# How much testing for coronavirus do continents conduct?

ggplot(df, aes(x = date, fill = total_tests)) +
  theme_bw() +
  facet_wrap(~ continent) +
  geom_density(alpha = 0.5) +
  labs(y = "Total Test per Million",
       x = "Time Progression ->",
       title = "Testing Rate per Continent") +
  theme(plot.title = element_text(hjust = 0.5))
