Created a python file with connection to database bscit and table name record where data is inserted and deleted.
import mysql.connector 





mydb=mysql.connector.connect(host="localhost",username="root",password="",database="bscit")
print(mydb)

mycursor = mydb.cursor()
sql="insert into record(name,email,age,mobile) values(%s,%s,%s,%s)"
val=[('sanju','sanju@gmail.com','23','9815591802'),('rani','rani@yahoo.com','12','7784818000')]
mycursor.executemany(sql,val)
mydb.commit()
print(mycursor.rowcount,"record was inserted")
  
mycursor.executemany("delete from students whose age>22")
mydb.commit()
print(mycursor.rowcount, "record was deleted")
