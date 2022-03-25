```python
import matplotlib as mpl
import matplotlib.pyplot as plt
import matplotlib.font_manager as fm
from matplotlib import rc

import warnings
import numpy as np
import pandas as pd

# warning 출력 ignore
warnings.filterwarnings(action='ignore')

# 그래프에서 '-' 기호 때문에 문제 발생하는것 방지
mpl.rcParams['axes.unicode_minus'] = False

# 한글폰트 적용
font_path = './font/malgun.ttf'
font_name = fm.FontProperties(fname=font_path).get_name()
rc('font', family=font_name)
```



데이터 행 전부 보이게 하기

```python
import pandas as pd 
pd.set_option('display.max_rows', 10000)
pd.set_option('display.max_rows', None)
pd.set_option('display.max_columns', None)
```

