## Welcome to A-Detection Web

A-Detection is a software developed to automate the analysis of anomalies in large dataframes. Thanks to a series of algorithms A-Detection is able, on the basis of red traffic, to learn and detect anomalous traffic.

![logo](https://github.com/adetection/adetection.github.io/blob/master/plot.png?raw=true)

### How it works

Thanks to a Python library called Pandas, A-Detection imports network traffic, and based on a series of algorithms like; Variable Scaling and Isolation Forest, is able to Normalize and detect anomalies in the dataframe.

#### Data import

```markdown
import pandas as pd
import numpy as np

pd.read_csv('/home/snort/Desktop/netflow.json')
```


#### Data group

```markdown
ipdst           proto   time                   count
10.3.20.102     HTTP    2017-03-20 17:08:56     1
10.3.20.102     HTTP    2017-03-20 17:08:57     1
10.3.20.102     HTTP    2017-03-20 17:08:58     1
10.3.20.102     HTTP    2017-03-20 17:08:58     1
10.3.20.102     TCP     2017-03-20 17:08:59     3
```

```markdown
df.set_index('time').groupby(['ipdst','proto']).resample('5S').sum().reset_index()
```

```markdown
 ipdst       proto  time                 count     
    -           -    2017-03-20 17:08:50    0
10.3.20.102    HTTP  2017-03-20 17:08:55    4
10.3.20.102    TCP   2017-03-20 17:08:55    4
    -           -    2017-03-20 17:09:00    0
```

#### Data normalization

![logo](https://github.com/adetection/adetection.github.io/blob/master/dataNorm.png?raw=true)


## Social media
#### [![twitter][1.1]][1] [![github][6.1]][6] @alexfrancow
[1]: http://www.twitter.com/alexfrancow
[1.1]: http://i.imgur.com/tXSoThF.png (twitter icon with padding)
[6.1]: http://i.imgur.com/0o48UoR.png (github icon with padding)
[6]: http://www.github.com/alexfrancow
