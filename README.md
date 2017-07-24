# intro_to_r
A whistlestop tour of the R language and its capabilities

# contents
- How to install R

# getting going

## how to install R
1. Install base r
```
pacaur -S r
```
2. Run R in sudo __you need sudo here as we're going to check what's been set up__
```sudo R```
3. Check where R is going to install its packages
```Sys.getenv()```
`R_LIBS_USER` is where your packages go by default when you're not sudo, `R_HOME` is where they go when you are. This is important because there are a number of ways of installing packages in R, and not all of them allow you to specify where to put them!
If you want to change any of these locations, then go ahead and just change these environment variables interactively or in your `.rprofile` file.

## installing packages
There are a number of ways to install packages.
- From interactive R, you can install open source packages stored on R's CRAN repository.
```
R
install.packages('devtools')
```

- Using the additional `devtools` package, you can install from other sources (including github)
```
devtools::install_github('kater-s/intro_to_r')
```

- From the terminal, use `R CMD INSTALL`. This is useful if you want to script an install, or install from local (packages you have made).
```
R CMD INSTALL --help
```

> If you want to follow this demo along, I'm using:
> R version 3.4.0
> The following packages:
> - tidyverse (note one of the dependencies here requires gcc-fortran. Don't ask. Really, don't)
> - nycflights13

# what R can do
R started life as a stats language. Because it's pretty easy to get started, and because it contains a lot of pre-written statistical stuff, lots of statiticians use it. As their data requirements have grown, so have the capabilities of R. Some of these things are good, and some are not!

## Useful things in R
### using pre-installed sample data
If you want to try out some stats or even just get your hands on some numeric data, R has a lot of this pre-installed, or you can use external packages:

```
data()
library(nycflights13)
head(mtcars)
head(diamonds)
head(flights)
```

### reading and writing to csv
You can also read in data from various files

```
library(readr)
read_csv("~/trainingMaterials/london.csv")
write_csv(mtcars, "~/trainingMaterials/mtcars.csv)
```

This just makes trying things out and learning stats really quick and easy. Happy face.

### developing alongside the data

### stats
Understandably, R is really good for stats. Any methods you would ever want to use are there. Many also follow a convention:


### good programming practices
There are ways to write pretty good R code. I'll get on to how often people do this later, but they are there. These include things like:
- the reference class (RC) class system and environments
- function argument and return conventions (see the `tidyverse` for a lot of these)
- function argument assertions (`assert_that`, `assertive`, `checkmate`...)
- linting (`lintr`)
- test frameworks (`testthat`)
- test coverage statistics (`covr`)

## things that R can get you into trouble for
### the global environment
### masking without warning
