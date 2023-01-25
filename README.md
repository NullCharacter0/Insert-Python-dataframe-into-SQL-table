# Insert-Python-dataframe-into-SQL-table
Inserting Python dataframe into SQL table if the table is created 

# Requirements 
```python
import pandas as pd 
import sqlite3 
```

# Function 
---

```python

for v in df.iterrows():
    conn.execute("INSERT OR REPLACE INTO CANDLE_STICK values (?,?,?,?,?,?)", [str(v[0])] + list(v[1].values))

conn.commit()
print(conn.total_changes)


```



# Prior
---

```python 
conn = sqlite3.connect("CoinbaseAPI.sqlite")
         # Purpose is to create a table if it doesnt exist 
         df.to_sql(name="CANDLE_STICK",
                   con=conn,
                   if_exists="fail", # "append","replace","fail" default: fail 
                   index=True, #  Sets df index to table index
                   dtype={
                       "start": "TIMESTAMP PRIMARY KEY",
                       "open": "REAL",
                       "high": "REAL",
                       "low": "REAL",
                       "close": "REAL",
                          }
                   )
```





