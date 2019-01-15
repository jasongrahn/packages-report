01\_write-installed-packages.R
================
rstudio
Tue Jan 15 23:09:32 2019

``` r
## deja vu from earlier!
library(fs)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.1.0     ✔ purrr   0.2.5
    ## ✔ tibble  1.4.2     ✔ dplyr   0.7.8
    ## ✔ tidyr   0.8.2     ✔ stringr 1.3.1
    ## ✔ readr   1.2.1     ✔ forcats 0.3.0

    ## ── Conflicts ────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
## create a data frame of your installed packages
## hint: installed.packages() is the function you need
ipt <- installed.packages() %>%
  as_tibble() %>%
  select(Package, LibPath, Version, Priority, Built)

## optional: select just some of the variables, such as
##   * Package
##   * LibPath
##   * Version
##   * Priority
##   * Built

## write this data frame to data/installed-packages.csv
## hint: readr::write_csv() or write.table()
## idea: try using here::here() to create the file path
readr::write_csv(x = ipt,
                 path = here::here("/data/installed-packages.csv"))

## YES overwrite the file that is there now (or delete it first)
## that's a old result from me (Jenny)
## it an example of what yours should look like and where it should go

####################################################
#                                                  #
#  system information at time of publish is below  #
#                                                  #
####################################################

devtools::session_info()[1]
```

    ## Warning in system("timedatectl", intern = TRUE): running command
    ## 'timedatectl' had status 1

    ## $platform
    ##  setting  value                       
    ##  version  R version 3.5.1 (2018-07-02)
    ##  os       Debian GNU/Linux 9 (stretch)
    ##  system   x86_64, linux-gnu           
    ##  ui       X11                         
    ##  language (EN)                        
    ##  collate  en_US.UTF-8                 
    ##  ctype    en_US.UTF-8                 
    ##  tz       Etc/UTC                     
    ##  date     2019-01-15
