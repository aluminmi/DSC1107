FA2\_ Cuerdo, Naomi Hannah A.
================
Cuerdo, Naomi Hannah A.
2025-02-05

## Import the Required Datasets

``` r
data("who")
data("population")
```

### Previewing the contents of who.tsv and population.csv

``` r
glimpse(who)
```

    ## Rows: 7,240
    ## Columns: 60
    ## $ country      <chr> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan…
    ## $ iso2         <chr> "AF", "AF", "AF", "AF", "AF", "AF", "AF", "AF", "AF", "AF…
    ## $ iso3         <chr> "AFG", "AFG", "AFG", "AFG", "AFG", "AFG", "AFG", "AFG", "…
    ## $ year         <dbl> 1980, 1981, 1982, 1983, 1984, 1985, 1986, 1987, 1988, 198…
    ## $ new_sp_m014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_m1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_m2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_m3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_m4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_m5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_m65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sp_f65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_m65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_sn_f65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_m65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ new_ep_f65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_m65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f014  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f1524 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f2534 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f3544 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f4554 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f5564 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…
    ## $ newrel_f65   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…

``` r
glimpse(population)
```

    ## Rows: 4,060
    ## Columns: 3
    ## $ country    <chr> "Afghanistan", "Afghanistan", "Afghanistan", "Afghanistan",…
    ## $ year       <dbl> 1995, 1996, 1997, 1998, 1999, 2000, 2001, 2002, 2003, 2004,…
    ## $ population <dbl> 17586073, 18415307, 19021226, 19496836, 19987071, 20595360,…

### Determining the number of rows and columns in each tibble

``` r
dim(who)
```

    ## [1] 7240   60

``` r
dim(population)
```

    ## [1] 4060    3

The WHO dataset has 7240 rows and 60 columns, while the population
dataset has 4060 rows and 3 columns.

### Fixing any anomalies from the dataset

``` r
summary(population)
```

    ##    country               year        population       
    ##  Length:4060        Min.   :1995   Min.   :1.129e+03  
    ##  Class :character   1st Qu.:1999   1st Qu.:6.029e+05  
    ##  Mode  :character   Median :2004   Median :5.319e+06  
    ##                     Mean   :2004   Mean   :3.003e+07  
    ##                     3rd Qu.:2009   3rd Qu.:1.855e+07  
    ##                     Max.   :2013   Max.   :1.386e+09

``` r
population2 <- population %>% mutate(across(where(is.character), ~ suppressWarnings(as.numeric(.)), .names = "cleaned_{col}"))
```

## Tidy Data

### WHO Dataset

``` r
who2 <-who %>%
  pivot_longer(cols = starts_with("new"), 
               names_to = "category",
              values_to = "cases",
              values_drop_na = TRUE)

who3 <- who2 %>% separate(category, into = c("new", "type", "sex_age"), sep = "_", fill = "right", extra = "merge") %>% select(-new)

who_tidy <- who3 %>% mutate(sex = substr(sex_age, 1, 1), age_group = substr(sex_age, 2, nchar(sex_age))) %>% select(-sex_age)
```

### Population Dataset

``` r
colnames(population)
```

    ## [1] "country"    "year"       "population"

Since the variables in the dataset is already tidy, there is no need to
perform a pivot operation. we then proceed to cast the population
variable into an appropriate data type.

``` r
population_tidy <- population %>% mutate(year = as.integer(year))
```

### Join Datasets

``` r
tuberculosis <- left_join(who_tidy, population_tidy, by = c("country", "year"))
```

### Removing the unnecessary variables from the Tuberculosis Dataset

``` r
tuberculosis <- tuberculosis %>% drop_na()
tuberculosis
```

    ## # A tibble: 72,402 × 9
    ##    country     iso2  iso3   year type  cases sex   age_group population
    ##    <chr>       <chr> <chr> <dbl> <chr> <dbl> <chr> <chr>          <dbl>
    ##  1 Afghanistan AF    AFG    1997 sp        0 m     014         19021226
    ##  2 Afghanistan AF    AFG    1997 sp       10 m     1524        19021226
    ##  3 Afghanistan AF    AFG    1997 sp        6 m     2534        19021226
    ##  4 Afghanistan AF    AFG    1997 sp        3 m     3544        19021226
    ##  5 Afghanistan AF    AFG    1997 sp        5 m     4554        19021226
    ##  6 Afghanistan AF    AFG    1997 sp        2 m     5564        19021226
    ##  7 Afghanistan AF    AFG    1997 sp        0 m     65          19021226
    ##  8 Afghanistan AF    AFG    1997 sp        5 f     014         19021226
    ##  9 Afghanistan AF    AFG    1997 sp       38 f     1524        19021226
    ## 10 Afghanistan AF    AFG    1997 sp       36 f     2534        19021226
    ## # ℹ 72,392 more rows

## Data Manipulation

### Determining the Total TB Cases Among Men and Women in the 21st Century in the United States:

``` r
us_tb <- tuberculosis %>% filter(country == "United States of America", year >= 2000) %>% group_by(sex) %>% summarise(total_cases = sum(cases, na.rm = TRUE))
us_tb
```

    ## # A tibble: 2 × 2
    ##   sex   total_cases
    ##   <chr>       <dbl>
    ## 1 f           42184
    ## 2 m           72345

The table above shows the total cases of tuberculosis among men and
women in the 21st century in the United States.

From the table, It is shown that the total cases of TB for **females**
is at **42,184**, while the total cases of TB for **males** is at
**72,345**. From here, we can conclude that males have higher cases in
the 21st century than women.

### Determining the country and year with the highest cases per 100,000 people by year, sex, age group, and TB type.

``` r
tuberculosis <- tuberculosis %>% mutate(cases_per_100k = (cases / population) * 100000)
```

``` r
top_case <- tuberculosis %>% filter(cases_per_100k == max(cases_per_100k, na.rm = TRUE))

low_case <- tuberculosis %>% filter(cases_per_100k == min(cases_per_100k, na.rm = TRUE))
```

### Reviewing the Top Case of Tuberculosis

``` r
top_case
```

    ## # A tibble: 1 × 10
    ##   country iso2  iso3   year type  cases sex   age_group population
    ##   <chr>   <chr> <chr> <dbl> <chr> <dbl> <chr> <chr>          <dbl>
    ## 1 Samoa   WS    WSM    2009 sp     1111 f     65            184704
    ## # ℹ 1 more variable: cases_per_100k <dbl>

The table above shows the highest cases of TB in the 21st century in
100,000 per people. From the table, it is shown that **Samoa** has the
highest TB cases in **2009**, with a total number of **601.5029.**

### Reviewing the Lowest Case of Tub

``` r
low_case
```

    ## # A tibble: 10,600 × 10
    ##    country     iso2  iso3   year type  cases sex   age_group population
    ##    <chr>       <chr> <chr> <dbl> <chr> <dbl> <chr> <chr>          <dbl>
    ##  1 Afghanistan AF    AFG    1997 sp        0 m     014         19021226
    ##  2 Afghanistan AF    AFG    1997 sp        0 m     65          19021226
    ##  3 Afghanistan AF    AFG    1997 sp        0 f     5564        19021226
    ##  4 Afghanistan AF    AFG    2007 sn        0 m     014         26349243
    ##  5 Afghanistan AF    AFG    2007 sn        0 m     1524        26349243
    ##  6 Afghanistan AF    AFG    2007 sn        0 m     2534        26349243
    ##  7 Afghanistan AF    AFG    2007 sn        0 m     3544        26349243
    ##  8 Afghanistan AF    AFG    2007 sn        0 m     4554        26349243
    ##  9 Afghanistan AF    AFG    2007 sn        0 m     5564        26349243
    ## 10 Afghanistan AF    AFG    2007 sn        0 m     65          26349243
    ## # ℹ 10,590 more rows
    ## # ℹ 1 more variable: cases_per_100k <dbl>

The table above shows the lowest cases of TB in the 21st century in
100,000 per people. It seems that there are a lot of countries that has
zero cases of tuberculosis in the 21st century, so it is best to check
the first 10 rows:

``` r
low_cases <- tuberculosis %>% arrange(cases_per_100k) %>% head(10)

low_cases
```

    ## # A tibble: 10 × 10
    ##    country     iso2  iso3   year type  cases sex   age_group population
    ##    <chr>       <chr> <chr> <dbl> <chr> <dbl> <chr> <chr>          <dbl>
    ##  1 Afghanistan AF    AFG    1997 sp        0 m     014         19021226
    ##  2 Afghanistan AF    AFG    1997 sp        0 m     65          19021226
    ##  3 Afghanistan AF    AFG    1997 sp        0 f     5564        19021226
    ##  4 Afghanistan AF    AFG    2007 sn        0 m     014         26349243
    ##  5 Afghanistan AF    AFG    2007 sn        0 m     1524        26349243
    ##  6 Afghanistan AF    AFG    2007 sn        0 m     2534        26349243
    ##  7 Afghanistan AF    AFG    2007 sn        0 m     3544        26349243
    ##  8 Afghanistan AF    AFG    2007 sn        0 m     4554        26349243
    ##  9 Afghanistan AF    AFG    2007 sn        0 m     5564        26349243
    ## 10 Afghanistan AF    AFG    2007 sn        0 m     65          26349243
    ## # ℹ 1 more variable: cases_per_100k <dbl>

From the table, it is shown that **Afghanistan** has zero cases of TB
during 1997 and 2007.

## Data Visualization

### Plotting the total cases per 100k as a function of year for China, India, and the United States:

``` r
tuberculosis %>% filter(country %in% c("China", "India", "United States of America")) %>%
  ggplot(aes(x = year, y = cases_per_100k, color = country)) +
  geom_line() +
  scale_y_log10() +
  labs(title = "TB Cases per 100k Over Time", y = "Cases per 100k (log scale)")
```

![](FA2_Cuerdo,-Naomi-Hannah-A._files/figure-gfm/data%20visualization%20for%20CN,%20IN,%20&%20US-1.png)<!-- -->

The graph above shows the trends in TB cases per 100,000 people over
time for China, India, and the United States. From the graph, **China**
shows a **steady decline**, suggesting their efforts for controlling TB
is effective over time, while **India** shows **fluctuations with
occasional spikes**, indicating inconsistent outbreaks of the disease.
The U.S., on the other hand, maintains the lowest TB rates with periodic
fluctuations. Overall, India has the highest TB cases, followed by
China, and the U.S having the lowest case.

### Comparing distributions of total cases per 100,000 people summed over years, sexes, and TB types across age groups:

``` r
tuberculosis %>% 
  group_by(age_group) %>%
  summarise(total_cases_per_100k = sum(cases_per_100k, na.rm = TRUE)) %>%
  mutate(age_group = case_when(
    age_group == "014" ~ "0-14",
    TRUE ~ str_replace(age_group, "(\\d{2})(\\d{2})", "\\1-\\2")
  )) %>%
  ggplot(aes(x = age_group, y = total_cases_per_100k, fill = age_group)) +
  geom_col() +
  scale_y_log10() +
  labs(title = "TB Cases per 100k by Age Group") +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```

![](FA2_Cuerdo,-Naomi-Hannah-A._files/figure-gfm/data%20vis%20across%20age%20groups-1.png)<!-- -->

The graph shows visualizes the total cases of TB in 100,000 people over
the 21st century. From the graph, it is shown that adults in **ages
25-34 has the highest number of cases**, which **exceeds over 10,000
cases, followed by ages 15-24 and 35-44**. This indicates that TB cases
are common among young and middle-aged adults. Meanwhile, **cases in
older age groups decline, specifically in ages 55 and above**. **Ages
0-14 have lower TB cases**, suggesting that diagnosis is uncommon among
children.

Furthermore, The y-axis seems to be logarithmic, which means that the
difference between age groups may be more significant that it is being
visualized.

``` r
tuberculosis %>% 
  filter(year == 2000, cases_per_100k > 0, population > 0) %>%
  ggplot(aes(x = population, y = cases_per_100k)) +
  geom_point(alpha = 0.5, color = "purple") +
  scale_x_log10() +
  scale_y_log10() +
  labs(
    title = "Cases per 100k vs. Population in 2000",
    x = "Population (log scale)",
    y = "Cases per 100k (log scale)"
  ) +
  theme_minimal() +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold"),
    axis.text = element_text(size = 12),
    axis.title = element_text(size = 14)
  )
```

![](FA2_Cuerdo,-Naomi-Hannah-A._files/figure-gfm/Relationship%20Between%20Cases%20and%20Population-1.png)<!-- -->

The graph above shows the relationship between population size and
tuberculosis cases per 100,00 people in the year 2000, using a
logarithmic scale for both axes. From the graph, there is an evident
downward trend, wherein smaller populations tend to have higher TB
incidence rates per 100k, while larger populations generally report
lower rates. This potentially indicates that TB disproportionately
affects smaller or less developed regions with limited healthcare
access, or populations with smaller sizes tend to spread the disease
much easier since TB can be carried through air can circulate more
rapidly in close knit close-knit communities.

Furthermore, the clustering of points at higher TB rates for smaller
population may also reflect reporting biases or localized outbreaks,
while the more dispersed points for larger populations suggest
variability in TB prevalence across different countries.
