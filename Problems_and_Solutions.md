# Problems_and_Solutions

To be clear, my computer system is `Windows10`. Use Git to clone the source of Hadley Wickham's **Advanced R Programming**.
```r
git clone https://github.com/hadley/adv-r.git
```
Set working directory temporarily using
```r 
setwd("C:/Users/-carol/dsia02/adv-r")
```
Install R Package dependencies using
```r
devtools::install_github("hadley/sloop")
devtools::install_github("hadley/emo")
```
Finanlly, use `bookdown` package to compile the book.
```r
bookdown::render_book("index.Rmd", output_format = "bookdown::pdf_book")
```

During the building process, I've met several problems, the followings are the errors I've met and how I solved them. Note: due to previous learning needs, [*TinyTex*],[*MiKTex*],[*Pandoc*] and some packages have been installed on my computer, some packages that must be installed during the compilation process may not be recorded.

## Unable to load devtools package

Maybe it is a network problem. Execute the following command in [*Git*].
```r
$ git config --global http.sslBackend "openssl"
$ git config --global http.sslCAInfo [path to .pem file] 
```

For example, My `[path to .pem file]` is `"C:\Program Files\Git\mingw64\ssl\cert.pem"`.

## Quitting from lines 223-235 (Introduciton.Rmd)

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Quitting_from_IntroducitonRmd.PNG)

Adding `encoding = "UTF-8"` in line 224 can fix it. The line 224 is displayed as
```r
contributors <- read.csv("contributors.csv", stringsAsFactors = FALSE,encoding = "UTF-8")
```

## Quitting from lines 327-328 (Names-values.Rmd)

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Quitting_from_Names-valuesRmd.PNG)

I first updated `rlang` by the update function in RStudio, but it failed. So I manually removed `rlang` based on the path `D:/R/R-3.6.2/library/rlang`, and then reinstalled `rlang` using
```r 
install.packages("rlang")
```

## Quitting from lines 172-176 (OO-tradeoffs.Rmd)

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Quitting_from_OO-tradeoffsRmd.PNG)

```r
install.packages("zeallot")
```

## Quitting from lines 209-221 (Big-picture.Rmd)

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Quitting_from_Big-pictureRmd.PNG)
 
```r
install.packages("dbplyr")
```

## Quitting from lines 77-84 (Rcpp.Rmd)

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Quitting_from_RcppRmd.PNG)

I added `C:\Rtools\bin\` to the path of the environment variable of the computer system, but the error still occurred, so I reinstalled `Rtools` and successfully solved this problem.

## Font

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Andale_Mono.PNG)

I downloaded the font `Andale Mono` from the internet and copied it to `C:\Windows\Fonts`.

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/main.PNG)

After 4 hours of intermittent compilation, the book was finally built.

In the communication with some classmates, I summarized the solutions to some problems they encountered:

## Package does not match the version

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/Package_isnot_available.PNG)

If the package does not match the version, such as the error in the figure above, you can try the following: 
```r
install.packages ("BiocInstaller", repos = "http://bioconductor.org/packages/3.7/ bioc ")
Library (BiocInstaller)
biocLite ("autoplot")
```

## LaTeX failed to compile

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/LaTeX_failed_to_compile.PNG)

Download the [*MiKTeX*], and add the path to the system settings. Then click the `setting` in the [*MiKTeX*], choose the `Alwayes install missing package on-the-fly`.

![Image text](https://github.com/data-science-in-action/02-compiling-advanced-r-Carol-seven/blob/master/image/MiKTeX_settings.PNG)

## dev.control() without an open graphics device for `Mac`

Download [*XQuartz*](https://www.xquartz.org), then restart the PC and install the package `Cairo`.
