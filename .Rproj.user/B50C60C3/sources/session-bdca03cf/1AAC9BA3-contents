library(dplyr)
library(tidyverse)
library(broom)
source("code/gen_data.R")

## make a line plot of average y in time series

set.seed(1414)

n_obs <- 1000
total_years <- 36

data <- make_simulation(n_obs, total_years)

g1 <- data |> 
  mutate(group = recode_factor(group,
                               `1` = "1989-continued",
                               `2` = "1989-quited",
                               `3` = "1998",
                               `4` = "2007")) |> 
  group_by(group, year) |> 
  summarize(y1_avg = mean(y1)) |> 
  ggplot() +
  geom_line(aes(x = year, y = y1_avg, col = group)) +
  geom_vline(xintercept = 1988.5, linetype = "dashed") +
  geom_vline(xintercept = 1997.5, linetype = "dashed") +
  geom_vline(xintercept = 2006.5, linetype = "dashed") +
  labs(title = "Case1: Staggered + Constant/Equal Treatment Effect",
       x = NULL, y = NULL, color = NULL) +
  theme(legend.position = c(0.1, 0.9))

g2 <- data |> 
  mutate(group = recode_factor(group,
                               `1` = "1989-continued",
                               `2` = "1989-quited",
                               `3` = "1998",
                               `4` = "2007")) |> 
  group_by(group, year) |> 
  summarize(y2_avg = mean(y2)) |> 
  ggplot() +
  geom_line(aes(x = year, y = y2_avg, col = group)) +
  geom_vline(xintercept = 1988.5, linetype = "dashed") +
  geom_vline(xintercept = 1997.5, linetype = "dashed") +
  geom_vline(xintercept = 2006.5, linetype = "dashed") +
  labs(title = "Case2: Staggered + Constant/Unequal Treatment Effect",
       x = NULL, y = NULL, color = NULL) +
  theme(legend.position = c(0.1, 0.9))

g3 <- data |> 
  mutate(group = recode_factor(group,
                               `1` = "1989-continued",
                               `2` = "1989-quited",
                               `3` = "1998",
                               `4` = "2007")) |> 
  group_by(group, year) |> 
  summarize(y3_avg = mean(y3)) |> 
  ggplot() +
  geom_line(aes(x = year, y = y3_avg, col = group)) +
  geom_vline(xintercept = 1988.5, linetype = "dashed") +
  geom_vline(xintercept = 1997.5, linetype = "dashed") +
  geom_vline(xintercept = 2006.5, linetype = "dashed") +
  labs(title = "Case3: Staggered + Dynamic/Equal Treatment Effect",
       x = NULL, y = NULL, color = NULL) +
  theme(legend.position = c(0.1, 0.9))

g4 <- data |> 
  mutate(group = recode_factor(group,
                               `1` = "1989-continued",
                               `2` = "1989-quited",
                               `3` = "1998",
                               `4` = "2007")) |> 
  group_by(group, year) |> 
  summarize(y4_avg = mean(y4)) |> 
  ggplot() +
  geom_line(aes(x = year, y = y4_avg, col = group)) +
  geom_vline(xintercept = 1988.5, linetype = "dashed") +
  geom_vline(xintercept = 1997.5, linetype = "dashed") +
  geom_vline(xintercept = 2006.5, linetype = "dashed") +
  labs(title = "Case4: Staggered + Dynamic/Unequal Treatment Effect",
       x = NULL, y = NULL, color = NULL) +
  theme(legend.position = c(0.1, 0.9))

g <- (g1 + g2)/(g3 + g4)
ggsave("figure/fig1.png", g, height = 8, width = 14)