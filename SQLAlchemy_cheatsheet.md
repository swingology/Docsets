# SQLAlchemy Cheatsheet


## LINKS
https://docs.sqlalchemy.org/en/14/core/engines.html#postgresql

https://towardsdatascience.com/sqlalchemy-python-tutorial-79a577141a91




## INSTALL
`pip install sqlalchemy`


## CONNECTING TO DATABASE

an example of a URL that includes the password "kx%jj5/g", where the percent sign and slash characters are represented as %25 and %2F, respectively:

postgresql+pg8000://dbuser:kx%25jj5%2Fg@pghost10/appdb
>>> import urllib.parse
>>> urllib.parse.quote_plus("kx%jj5/g")


``` python
# generic
import sqlalchemy as db
engine = db.create_engine('dialect+driver://user:pass@host:port/db')

# PostgreSQL
# default
engine = create_engine('postgresql://scott:tiger@localhost/mydatabase')

# psycopg2
engine = create_engine('postgresql+psycopg2://scott:tiger@localhost/mydatabase')

# pg8000
engine = create_engine('postgresql+pg8000://scott:tiger@localhost/mydatabase')


## MySQL
# default
engine = create_engine('mysql://scott:tiger@localhost/foo')

# mysqlclient (a maintained fork of MySQL-Python)
engine = create_engine('mysql+mysqldb://scott:tiger@localhost/foo')

# PyMySQL
engine = create_engine('mysql+pymysql://scott:tiger@localhost/foo')



## SQLite
# sqlite://<nohostname>/<path>
# where <path> is relative:
engine = create_engine('sqlite:///foo.db')

# Unix/Mac - 4 initial slashes in total
engine = create_engine('sqlite:////absolute/path/to/foo.db')

# Windows
engine = create_engine('sqlite:///C:\\path\\to\\foo.db')

# Windows alternative using raw string
engine = create_engine(r'sqlite:///C:\path\to\foo.db')

engine = create_engine('sqlite://')


```


## VIEWING TABLE DETAILS
``` python
import sqlalchemy as db

engine = db.create_engine('sqlite:///census.sqlite')
connection = engine.connect()
metadata = db.MetaData()
census = db.Table('census', metadata, autoload=True, autoload_with=engine)


# Print the column names
print(census.columns.keys())


# Print full table metadata
print(repr(metadata.tables['census']))

```


##  QUERYING
``` python

import sqlalchemy as db

engine = db.create_engine('sqlite:///census.sqlite')
connection = engine.connect()
metadata = db.MetaData()
census = db.Table('census', metadata, autoload=True, autoload_with=engine)


# Equivalent to 'SELECT * FROM census'
query = db.select([census])

ResultProxy = connection.execute(query)

ResultSet = ResultProxy.fetchall()

ResultSet[:3]


```



## DEALING WITH LARGE RESULTSET

``` python
while flag:
    partial_results = ResultProxy.fetchmany(50)
    if(partial_results == []): 
	flag = False
    //
	code
   //
ResultProxy.close()

```


## CONVERT TO PANDAS DATAFRAME

``` python
df = pd.DataFrame(ResultSet)
df.columns = ResultSet[0].keys()

```

## FILTERING DATA

``` python

# ------------ #
# WHERE
# SQL:
SELECT * FROM census
WHERE sex = f


# SQLAlchemy:
db.select([census]).where(censeus.columns.sex=='F')


# ------------ #
# IN
# SQL :
SELECT state, sex
FROM census
WHERE state IN (Texas, New York)

# SQLAlchemy :
db.select([census.columns.state, census.columns.sex]).where(census.columns.state.in_(['Texas', 'New York']))


# ------------ #
# AND OR NOT
# SQL :
SELECT state, sex
FROM census
WHERE state IN (Texas, New York)
# SQLAlchemy :
db.select([census.columns.state, census.columns.sex]).where(census.columns.state.in_(['Texas', 'New York']))


# ------------ #
# ORDER BY
# SQL :
SELECT * FROM census
ORDER BY State DESC, pop2000
# SQLAlchemy :
db.select([census]).order_by(db.desc(census.columns.state), census.columns.pop2000)



# ------------ #
# FUNCTIONS - sum, avg count, min max...
# SQL: 
SELECT SUM(pop2008)
FROM census


# SQLAlchemy:
db.select([db.func.sum(census.columns.pop2008)])



# ------------ #
# GROUP BY
# SQL:
SELECT SUM(pop2008) as pop2008, sex
FROM census

# SQLAlchemy:
db.select([db.func.sum(census.columns.pop2008).label('pop2008'),census.columns.sex]).group_by(census.columns.sex)




# ------------ #
# DISTINCT
# SQL:
SELECT DISTINCT state FORM census

# SQLAlchemy: 
db.select([census.columns.state.distinc()])



# ------------ #
# CASE & CAST
# The case() expression accepts a list of conditions to match and the column to return if the condition matches, followed by an else_ if none of the conditions match.

# cast() function to convert an expression to a particular type

import sqlalchemy as db

engine = db.create_engine('sqlite:///census.sqlite')
connection = engine.connect()
metadata = db.MetaData()
census = db.Table('census', metadata, autoload=True, autoload_with=engine)

female_pop = db.func.sum(db.case([(census.columns.sex == 'F', census.columns.pop2000)],else_=0))

total_pop = db.cast(db.func.sum(census.columns.pop2000), db.Float)

query = db.select([female_pop/total_pop * 100])

result = connection.execute(query).scalar()
print(result)



# ------------ #
# JOINS

# If you have two tables that already have an established relationship, you can automatically use that relationship by just adding the columns we want from each table to the select statement.

# prototype
select([census.columns.pop2008, state_fact.columns.abbreviation]) 

#  Setting up Database
import sqlalchemy as db
import pandas as pd

engine = db.create_engine('sqlite:///census.sqlite')
connection = engine.connect()
metadata = db.MetaData()

census = db.Table('census', metadata, autoload=True, autoload_with=engine)
state_fact = db.Table('state_fact', metadata, autoload=True, autoload_with=engine)


# AUTOMATIC JOIN
query = db.select([census.columns.pop2008, state_fact.columns.abbreviation])
result = connection.execute(query).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(5)


# MANUAL JOIN
query = db.select([census, state_fact])
query = query.select_from(census.join(state_fact, census.columns.state == state_fact.columns.name))
results = connection.execute(query).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(5)



# ------------ #
# CREATING AND INSERTIGN DATA INTO TABLES

import sqlachemy as db
import pandas as pd

engine = db.create_engine('sqlite:///test.sqlite') #Create test.sqlite automatically
connection = engine.connect()
metadata = db.MetaData()

emp = db.Table('emp', metadata,
              db.Column('Id', db.Integer()),
              db.Column('name', db.String(255), nullable=False),
              db.Column('salary', db.Float(), default=100.0),
              db.Column('active', db.Boolean(), default=True)
              )

# CREATE
metadata.create_all(engine) #Creates the table


# INSERTING DATA
#Inserting record one by one
query = db.insert(emp).values(Id=1, name='naveen', salary=60000.00, active=True) 
ResultProxy = connection.execute(query)

#Inserting many records at ones
query = db.insert(emp) 
values_list = [{'Id':'2', 'name':'ram', 'salary':80000, 'active':False},
               {'Id':'3', 'name':'ramesh', 'salary':70000, 'active':True}]
ResultProxy = connection.execute(query,values_list)

# SEE RESULTS
results = connection.execute(db.select([emp])).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(4)




# ------------ #
# UPDATING DATA IN DATABASES

# prototype
db.update(table_name).values(attribute = new_value).where(condition)


# setting up the db
import sqlalchemy as db
import pandas as pd


engine = db.create_engine('sqlite:///test.sqlite')
metadata = db.MetaData()
connection = engine.connect()
emp = db.Table('emp', metadata, autoload=True, autoload_with=engine)


results = connection.execute(db.select([emp])).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(4)


# Build a statement to update the salary to 100000
query = db.update(emp).values(salary = 100000)
query = query.where(emp.columns.Id == 1)
results = connection.execute(query)

# show results
results = connection.execute(db.select([emp])).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(4)





# ------------ #
# DELETE TABLE

# prototype
db.delete(table_name).where(condition)
 
# Setting up DB
import sqlalchemy as db
import pandas as pd


engine = db.create_engine('sqlite:///test.sqlite')
metadata = db.MetaData()
connection = engine.connect()
emp = db.Table('emp', metadata, autoload=True, autoload_with=engine)


results = connection.execute(db.select([emp])).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(4)

# results
#      Id 	name 	salary 	active
#   0 	1 	vinay 	100000.0 	True
#   1 	1 	satvik 	100000.0 	True
#   2 	1 	naveen 	100000.0 	True
#   3 	2 	rahul 	80000.0 	False

# Build a statement to delete where salary < 100000
query = db.delete(emp)
query = query.where(emp.columns.salary < 100000)
results = connection.execute(query)


# resutls after change
results = connection.execute(db.select([emp])).fetchall()
df = pd.DataFrame(results)
df.columns = results[0].keys()
df.head(4)





# ------------ #

# DROPPING A TABLE

# drops a single table
table_name.drop(engine)

#drops all the tables in the database
metadata.drop_all(engine) 











```

[Source](https://towardsdatascience.com/sqlalchemy-python-tutorial-79a577141a91)
