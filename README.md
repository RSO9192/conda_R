# Quick tutorial on using conda/mamba and R

## Brief introduction
If you are an R user, it is possible that you simply installed R and RStudio in default locations. However, when you need to use specific version of R or some libraries require specific versions of R to be installed, then you need to understand environments. 

## Why using conda/mamba

The idea is that you can create [conda environments](https://docs.conda.io/en/latest/) in which you can install all your programmes (e.g R). These programmes now exists inside your environment only. This means you can have multiple environments in your computer, with different versions of R installed, for example. This has several benefits, including the fact that you can share your environment with other people avoiding dependencies issues. 

Mamba is a faster version of conda. 

## Practice

The first thing is installing [mamba](https://github.com/conda-forge/miniforge#mambaforge). After mamba is successfully installed, you can create your first environment! Open a terminal and input

`conda create --name first_env`

Now you can simply activate your environment by typing 

```
conda activate first_env
```

and, for example, install R and specify a specific version

`mamba install -c conda-forge r-base=4.1.2`

At this point you have installed R version 4.1.2, but this installation exists only inside your environment called first_env. This means you can create as many environments as you want with different versions of R installed. 
To deactivate an environment type

``` 
conda deactivate first_env
```

To install packages into your environment, activate your environment first and then type

``` 
R #launch R
install.packages("dplyr")
```
If you want to install RStudio, you can, by tipying:

``` 
mamba install -c conda-forge -c r rstudio

```
and then you can launch RStudio from your environment and work in RStudio and you would normally do. The only difference is that now all your installed libraries will only exist within the environment. Thus, to access them, you need to activate the environment first and then launch rstudio. 
[You can also install RStudio outside your environment](https://stackoverflow.com/questions/38534383/how-to-set-up-conda-installed-r-for-use-with-rstudio) so that it can be used for any R versions if you are using multiple environments

## Solving dependencies issues
If you install packages with install.packages and you encounter problem with dependencies or others, the best solution is trying [rhumba](https://github.com/mamba-org/rhumba), the R package manager. To install it, open a terminal and type

``` 
conda activate first_env # activate env
mamba install rhumba # install rhumba
R # launch R
rhumba::install("r-purrr") # install purrr via rhumba

```

## Final remarks

Now you can work with independent version of R (and other programmes) in a safer and more professional way. 
