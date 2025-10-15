## Hi there! 👋 I'm Andrei Cherniltsev.

## Skills
1. Programming
   - C/C++, C#, Python, ...
2. Computer networks
3. Foreign languages
   - English A2

## Schedule (it may vary)
| Day           | Lesson           | Start     |
|---------------|------------------|-----------|
| Monday        | Two pairs        | 14:00     |
| Tuesday       | Three pairs      | 10:00     |
| Wednesday     | Seminars         | 14:00     |
| Thursday      | Three pairs      | 14:00     |
| Friday        | Two pairs        | 10:00     |
| Saturday      | Three pairs      | 10:00     |


## Example code in Python
```Python
from flask import Flask, render_template, jsonify
import pandas as pd
import os

app = Flask(__name__)

def read_file(file_path):
    """Reading a CSV file"""
    return pd.read_csv(file_path, encoding='utf-8')

def get_sales_data(dataset, year):
    """Revenue by city for a specific year, taking into account the state"""
    year_data = dataset[dataset['order_date'].str[:4] == year].copy()
    # Группируем по городу и штату вместе
    result = year_data.groupby(['city', 'state'], as_index=False).agg(
        count=('order_date', 'count'), 
        sales=('sales', 'sum')
    )
    # Combined name "City, State
    result['city_state'] = result['city'] + ', ' + result['state']
    return result.sort_values('sales', ascending=False)    
```

<!--
**cheandgit/cheandgit** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.
Here are some ideas to get you started:
- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
