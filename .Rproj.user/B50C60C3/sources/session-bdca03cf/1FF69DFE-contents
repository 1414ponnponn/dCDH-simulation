library(dplyr)
library(tidyverse)

## a function to generate a simulation data

make_simulation <- function(n_obs, total_years){ # n_obs: the number of observations, total_years: the length to observe
  df_ind <- tibble(
    id = 1:n_obs, # individual's number
    firmFixed = rnorm(n_obs, 0, 0.5), # individual fixed effect
    group = sample(1:4, n_obs, replace = TRUE), # how to treat
    trTime = recode(group, `1` = 1989, `2` = 1989, `3` = 1998, `4` = 2007) # when treatments are started
  )
  
  data <- df_ind |> 
    slice(rep(1:n(), each = total_years)) |>
    mutate(
      year = rep(1980:2015, time = n_obs), # year: 1989~2007
      timeFixed = rep(rnorm(total_years, 0, 0.5), time = n_obs), # time fixed effect
      isTreated = if_else(group == 2, between(year, 1989, 1997), year >= trTime), # treatment dummy
      y1 = firmFixed + timeFixed + rnorm(n_obs * total_years, 0, 0.5) +
        rnorm(n_obs * total_years, 2, 0.2) * isTreated,
      y2 = firmFixed + timeFixed + rnorm(n_obs * total_years, 0, 0.5) + case_when(
        group %in% 1:2 ~ rnorm(n_obs * total_years, 5, 0.2) * isTreated,
        group == 3 ~ rnorm(n_obs * total_years, 3, 0.2) * isTreated,
        group == 4 ~ rnorm(n_obs * total_years, 1, 0.2) * isTreated
      ),
      y3 = firmFixed + timeFixed + rnorm(n_obs * total_years, 0, 0.5) + 
        rnorm(n_obs * total_years, 0.2, 0.2) * (year - trTime + 1) * isTreated,
      y4 = firmFixed + timeFixed + rnorm(n_obs * total_years, 0, 0.5) + case_when(
        group %in% 1:2 ~ rnorm(n_obs * total_years, 0.5, 0.2) * (year - trTime + 1) * isTreated,
        group == 3 ~ rnorm(n_obs * total_years, 0.3, 0.2) * (year - trTime + 1) * isTreated,
        group == 4 ~ rnorm(n_obs * total_years, 0.1, 0.2) * (year - trTime + 1) * isTreated
      )
    )
}

