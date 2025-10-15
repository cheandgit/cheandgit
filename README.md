## Hi there! 👋 I'm Andrei Cherniltsev

## Skills
1. Programming
   - C/C++, C#, Python, ...
2. Computer networks
3. Foreign languages
   - English A2

## Schedule (it may vary)
| Day           | Lesson                      | Start     |
|---------------|-----------------------------|-----------|
| Monday        | Лекция по алгоритмам        | 10:00     |
| Вторник       | Практика по Python          | 14:00     |
| Среда         | Свободный день              | —         |
| Четверг       | Лабораторная по БД          | 16:00     |
| Пятница       | Семинар по английскому      | 12:00     |


## Example code in Python
```Python
from flask import Flask, render_template, jsonify
import pandas as pd
import os

app = Flask(__name__)

def read_file(file_path):
    """Чтение CSV файла"""
    return pd.read_csv(file_path, encoding='utf-8')

def get_sales_data(dataset, year):
    """Выручка по городам за конкретный год с учетом штата"""
    year_data = dataset[dataset['order_date'].str[:4] == year].copy()
    # Группируем по городу и штату вместе
    result = year_data.groupby(['city', 'state'], as_index=False).agg(
        count=('order_date', 'count'), 
        sales=('sales', 'sum')
    )
    # Создаем объединенное название "Город, Штат"
    result['city_state'] = result['city'] + ', ' + result['state']
    return result.sort_values('sales', ascending=False)    

@app.route('/')
def index():
    """Главная страница"""
    return render_template('index.html')
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
