# Datasets

## -- Python code I use to load these Datasets
```python
import requests
import zipfile as zfm
import io

ro = 'jmonti-gh'                  # repo_owner
rn = 'Datasets'                   # repo_name
zipfln = 'DataToVisualize..zip'
dataset = 'iris.csv'

url = f'https://raw.githubusercontent.com/{ro}/{rn}/main/{zipfln}'

r = requests.get(url)

with zfm.ZipFile(io.BytesIO(r.content)) as zf:
    print(zf.namelist())
    df = pd.read_csv(zf.open(dataset))

print(df.shape)
df.iloc[[0, 9, -9, -1]]
```
