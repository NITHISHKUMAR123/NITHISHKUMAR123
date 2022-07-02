- 👋 Hi, I’m @NITHISHKUMAR123
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
NITHISHKUMAR123/NITHISHKUMAR123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import sqlite3 as sql

connection = sql.connect("dabaseMovies.db")

pointer = connection.cursor()
pointer.execute("CREATE TABLE IF NOT EXISTS MOVIES( NAME TEXT, ACTOR TEXT, ACTRESS TEXT,DIRECTOR_NAME TEXT, YEAR INTEGER )")
pointer.execute("INSERT INTO MOVIES VALUES('Shang-Chi and the Legend of the Ten Rings','Simu Liu','Awkwafina','Destin Daniel Cretton',2021)")
pointer.execute("INSERT INTO MOVIES VALUES('Dune','Timothée Chalamet','Rebecca Ferguson','Denis Villeneuve',2021)")
pointer.execute("INSERT INTO MOVIES VALUES('Spider-Man: Homecoming','Tom Holland','Zendaya','Jon Watts',2017)")
pointer.execute("INSERT INTO MOVIES VALUES('Spider-Man: Far From Home','Tom Holland','Zendaya','Jon Watts',2019)")
pointer.execute("INSERT INTO MOVIES VALUES('Spider-Man: No Way Home','Tom Holland','Zendaya','Jon Watts',2021)")

# Printing all the elements of the database 
print("************************Everything in the database************************")
allMovies = pointer.execute("SELECT * FROM MOVIES").fetchall()
for i in allMovies:
  title,actor,actress,director,releasedYear = i
  print("{t}\t\t{a}\t\t{ats}\t\t{d}\t\t{ry}".format(t=title,a=actor, ats=actress,d=director,ry=releasedYear))
  print("============================================================================================")

# In this query, we are printing only the details from the db where Tom Holland is the lead actor
print("************************Actor Query************************")
actorQuery = pointer.execute("SELECT * FROM MOVIES WHERE ACTOR = 'Tom Holland'").fetchall()
for i in actorQuery:
  title,actor,actress,director,releasedYear = i
  print("{t}\t\t{a}\t\t{ats}\t\t{d}\t\t{ry}".format(t=title,a=actor, ats=actress,d=director,ry=releasedYear))
  print("============================================================================================")
