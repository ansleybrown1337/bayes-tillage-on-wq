# R Environment Notes

The Bayesian workflows are R Markdown analyses using Stan through `cmdstanr`.
Install CmdStan and configure `cmdstanr` before running either Bayesian driver.

Required R packages used by the included workflows:

- `cmdstanr`
- `posterior`
- `rethinking`
- `dplyr`
- `tidyr`
- `ggplot2`
- `ggridges`
- `readr`
- `stringr`
- `purrr`
- `blastula` only if optional sampling-complete email notifications are used

The included Stan source files should be compiled locally rather than relying
on the compiled Windows executables from the development repository.
