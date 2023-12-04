Data Collection
================
Yueyi Xu
2023-12-04

### Clean the dataset for the top 25 amusement/theme parks Worldwide in 2019 to 2022

``` r
top25_tp_worldwide =
  read_excel("statistic_id194247_most-visited-amusement-and-theme-parks-worldwide-2019-2022.xlsx", sheet = "Data")

top25_tp_worldwide_clean_df =
  top25_tp_worldwide |>
  pivot_longer(
    ("2019"):("2022"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited amusement and theme parks worldwide 2019-2022"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Amusement/Theme Park",
    Region = "Worldwide",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

    ## Warning: Expected 2 pieces. Additional pieces discarded in 4 rows [85, 86, 87,
    ## 88].

### Clean the dataset for the top 20 amusement/theme parks North America in 2019 to 2022

``` r
top20_tp_na =
  read_excel("statistic_id194269_most-visited-amusement-and-theme-parks-in-north-america-2022.xlsx", sheet = "Data")

top20_tp_na_clean_df =
  top20_tp_na |>
  pivot_longer(
    ("2019"):("2022"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited amusement and theme parks in North America 2022"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Amusement/Theme Park",
    Region = "North America",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

    ## Warning: Expected 2 pieces. Additional pieces discarded in 80 rows [1, 2, 3, 4, 5, 6, 7,
    ## 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, ...].

### Clean the dataset for the top 10 amusement/theme parks Latin America in 2019 to 2022

\*8 total

``` r
top10_tp_la =
  read_excel("statistic_id194312_most-visited-latin-american-amusement-and-theme-parks-2019-2022.xlsx", sheet = "Data")

top10_tp_la_clean_df =
  top10_tp_la |>
  pivot_longer(
    ("2019"):("2022"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited Latin American amusement and theme parks 2019-2022"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Amusement/Theme Park",
    Region = "Latin America",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

### Clean the dataset of the top 20 Amusement/Theme Parks Asia Pacific in 2019 to 2021

\*Fix (city+country)? and sinapore without country name

``` r
top20_tp_apac =
  read_excel("statistic_id194300_most-visited-amusement-and-theme-parks-apac-2019-2021.xlsx", sheet = "Data")

top20_tp_apac_clean_df =
  top20_tp_apac |>
  pivot_longer(
    ("2019"):("2021"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited amusement and theme parks APAC 2019-2021"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Amusement/Theme Park",
    Region = "Asia Pacific",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

    ## Warning: Expected 2 pieces. Additional pieces discarded in 9 rows [31, 32, 33, 43, 44,
    ## 45, 49, 50, 51].

    ## Warning: Expected 2 pieces. Missing pieces filled with `NA` in 3 rows [58, 59,
    ## 60].

### Clean the dataset for the top 20 water parks North America in 2019 to 2022

``` r
top20_wp_na =
  read_excel("statistic_id194352_total-attendance-at-waterparks-in-the-us-2019-2022.xlsx", sheet = "Data")

top20_wp_na_clean_df =
  top20_wp_na |>
  pivot_longer(
    ("2019"):("2022"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Total attendance at waterparks in the U.S. 2019-2022"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Water Park",
    Region = "North America",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

### Clean the dataset for the top 10 water parks Latin America in 2020

``` r
top10_wp_la =
  read_excel("statistic_id1024329_most-visited-latin-american-water-parks-2020.xlsx", sheet = "Data")

top10_wp_la_clean_df =
  top10_wp_la |>
  pivot_longer(
    ("2020"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited Latin American water parks 2020"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Water Park",
    Region = "Latin America",
    Attendance = Attendance * 10e3
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

### Clean the dataset for the top 20 water parks Asia Pacific in 2019 to 2021

``` r
top20_wp_apac =
  read_excel("statistic_id1346887_most-visited-water-parks-apac-2019-2021.xlsx", sheet = "Data")

top20_wp_apac_clean_df =
  top20_wp_apac |>
  pivot_longer(
    ("2019"):("2021"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited water parks APAC 2019-2021"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Water Park",
    Region = "Asia Pacific",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

    ## Warning: Expected 2 pieces. Additional pieces discarded in 57 rows [1, 2, 3, 4, 5, 6, 7,
    ## 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, ...].

### Clean the dataset for the top 20 museums Worldwide in 2019 to 2022

\*19 total

``` r
top20_mu_worldwide =
  read_excel("statistic_id901072_leading-museums-by-highest-attendance-worldwide-2019-2022.xlsx", sheet = "Data")

top20_mu_worldwide_clean_df =
  top20_mu_worldwide |>
  pivot_longer(
    ("2019"):("2022"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Leading museums by highest attendance worldwide 2019-2022"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Museum",
    Region = "Worldwide",
    Attendance = Attendance * 10e6
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

### Clean the dataset for the top 20 museums Europe Middle East Africa in 2019 to 2022

``` r
top20_mu_emea =
  read_excel("statistic_id747942_most-visited-museums-in-europe-2019-2022.xlsx", sheet = "Data")

top20_mu_emea_clean_df =
  top20_mu_emea |>
  pivot_longer(
    ("2019"):("2022"),
    names_to = "Year",
    values_to = "Attendance"
  ) |>
  separate(
    col = ("Most visited museums in Europe 2019-2022"), into = c("Park_Name", "Country_State"), sep = ","
  ) |>
  mutate(
    Type = "Museum",
    Region = "Europe",
    Attendance = Attendance * 10e3
  ) |>
  select(
    Park_Name, Country_State, Year, Attendance, Type, Region
  )
```

### Combine all dataset

``` r
combine_df = 
  bind_rows(top25_tp_worldwide_clean_df, top20_tp_na_clean_df, top10_tp_la_clean_df, top20_tp_apac_clean_df, top20_wp_na_clean_df, top10_wp_la_clean_df, top20_wp_apac_clean_df, top20_mu_worldwide_clean_df, top20_mu_emea_clean_df)
```

### Export the final dataset

``` r
write.csv(combine_df, "final data.csv", row.names = FALSE)
```
