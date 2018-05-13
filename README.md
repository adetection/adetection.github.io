## Welcome to A-Detection

A-Detection is a software developed to automate the analysis of network anomalies in large dataframes. Thanks to a series of algorithms, A-Detection can detect anomalous data and display it in dynamic graphics.

![logo](https://github.com/adetection/adetection.github.io/blob/master/plot.png?raw=true)


## Table of content

* [How it works](#how-it-works)
    + [Data import](#data-import)
    + [Data group](#data-group)
    + [Data normalization](#data-normalization)
    + [Apply the Isolation Forest algorithm](#apply-the-isolation-forest-algorithm)
    + [Visualize the anomalies](#visualize-the-anomalies)
* [Installation Guide](#installation-guide)


<!-- toc -->

### How it works

A-Detection imports network traffic, and based on a series of algorithms like; Variable Scaling and Isolation Forest, is able to normalize data and detect anomalies in the dataframe.

#### Data import

This is the first step to start playing.

```markdown
import pandas as pd
import numpy as np

df = pd.read_csv('/home/alexfrancow/netflow.json')
```

#### Data group

At this point we basically tell the application to count the packets that have the same IP and the same protocol in a time period of 5 seconds.

*If we have the next table:*
```markdown
ipdst           proto   time                   count
10.3.20.102     HTTP    2017-03-20 17:08:56     1
10.3.20.102     HTTP    2017-03-20 17:08:57     1
10.3.20.102     HTTP    2017-03-20 17:08:58     1
10.3.20.102     HTTP    2017-03-20 17:08:58     1
10.3.20.102     TCP     2017-03-20 17:08:59     3
```

*With the data group, the output will be as follows:*
```markdown
  ipdst       proto  time                 count     
    -           -    2017-03-20 17:08:50    0
10.3.20.102    HTTP  2017-03-20 17:08:55    4
10.3.20.102    TCP   2017-03-20 17:08:55    4
    -           -    2017-03-20 17:09:00    0
```

#### Data normalization

An approach to Z-score normalization (or standardization) is the so-called **Min-Max scaling**.
In this approach, the data is scaled to a fixed range - usually 0 to 1.

![logo](https://github.com/adetection/adetection.github.io/blob/master/dataNorm.png?raw=true)

#### Apply the Isolation Forest algorithm

The IsolationForest ‘isolates’ observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature.

![logo](https://github.com/adetection/adetection.github.io/blob/master/IF.png?raw=true)

#### Visualize the anomalies

The results of all these algorithms will be printed on a map, to offer a good view to the user.

![logo](https://github.com/adetection/adetection.github.io/blob/master/mapA.png?raw=true)

### Installation Guide

Coming soon..

## Social media
### [![twitter][1.1]][1] [![github][6.1]][6]
[1]: http://www.twitter.com/alexfrancow
[1.1]: http://i.imgur.com/tXSoThF.png (twitter icon with padding)
[6.1]: http://i.imgur.com/0o48UoR.png (github icon with padding)
[6]: http://www.github.com/alexfrancow
