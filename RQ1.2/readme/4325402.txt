# MAE 288A Lectures

![Unit Tests](https://github.com/tdenewiler/mae288a-lectures/workflows/Unit%20Tests/badge.svg)

This repository contains lecture notes completed for [MAE 288A](http://maeresearch.ucsd.edu/mceneaney/mae288a/mae288a.html)
at UC San Diego during Fall quarter 2009 and taught by Prof McEneaney.

You can compile using

```shell
pdflatex mae288a_lectures.tex
bibtex mae288a_lectures.aux
pdflatex mae288a_lectures.tex
pdflatex mae288a_lectures.tex
```

After running those commands initially, further changes can be compiled just running a single `pdflatex` command.

## Static Analysis

[Statick](https://github.com/sscpac/statick) is used to ensure consistent style and that certain classes of errors
do not exist in this repository.
To run Statick locally, do the following:

```shell
apt install chktex lacheck python3-venv
python3 -m venv venv
. venv/bin/activate
pip install -r requirements.txt
mkdir statick_output
statick . statick_output --user-paths statick_config --profile tex-profile.yaml --config tex-config.yaml
```
