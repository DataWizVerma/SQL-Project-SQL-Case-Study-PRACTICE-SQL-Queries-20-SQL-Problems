### Project Challenges

During the development of this project, I encountered a significant challenge while attempting to import data into pgAdmin using Python code in Visual Studio Code. Specifically, I faced errors related to the installation of the `psycopg2` package. Resolving these errors required considerable time and effort, as I worked through various solutions to ensure successful installation and integration.

![image](https://github.com/user-attachments/assets/2a1b11a1-1d91-4355-be1f-f172b80083ca)

### Data Import into pgAdmin

This project includes a Python script to import data into pgAdmin using the `pandas` library and `SQLAlchemy`. Below is the code utilized for importing CSV files into a PostgreSQL database.

```python
import pandas as pd
from sqlalchemy import create_engine

# Connection string to connect to PostgreSQL
conn_string = 'postgresql://postgres:admin@localhost/painting'
db = create_engine(conn_string)
conn = db.connect()

# List of CSV files to import
files = ['artist', 'canvas_size', 'image_link', 'museum_hours', 'museum', 'product_size', 'subject', 'work']

# Loop through each file and import the data into the database
for file in files:
    df = pd.read_csv(f"C:/Users/kumar/Downloads/archive/{file}.csv")
    df.to_sql(file, con=conn, if_exists='replace', index=False)
