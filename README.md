# TF2.3 session.run performance drop

This folder can be used to investigate the performance drop that is found when you
use the session.run command in [tf2_3](https://www.tensorflow.org/api_docs/python/tf) compared to [tf1.15](https://www.tensorflow.org/versions/r1.15/api_docs/python/tf).

## Use instructions

### Conda environment

From the general python package sanity perspective, it is a good idea to use conda
environments to make sure packages from different projects do not interfere with each
other. We will therefore create to conda environments to compare the performance difference between [tf2_3](https://www.tensorflow.org/api_docs/python/tf) and [tf1.15](https://www.tensorflow.org/versions/r1.15/api_docs/python/tf).

#### Create tf1.15 environment

To create the first conda environment run the following command:

```bash
conda create -n tf115_performance_test python=3.6
```

To activate the env:

```bash
conda activate tf115_performance_test
```

You can then install the required packages using the following command:

```bash
pip install -r requirements_tf1_15.txt
```

#### Create tf2.3 environment

To create the first conda environment run the following command:

```bash
conda create -n tf23_performance_test python=3.8
```

To activate the env:

```bash
conda activate tf23_performance_test
```

You can then install the required packages using the following command:

```bash
pip install -r requirements_tf1_15.txt
```

## How to run

When both environments are created you can use the
[spyder](https://docs.spyder-ide.org/current/profiler.html) or
[cprofiler](https://docs.python.org/2/library/profile.html) to investigate
the difference in execution time. The cprofiler run command is:

```bash
python -m cProfile -o tf_115.cprof tf_1_15_vs_tf2_3_sess_speed_compare.py
```

To investigate the report you can use the following command:

```bash
pyprof2calltree -k -i tf_115.cprof
```

For this to work you need to install the `kcachegrind` debian package.
