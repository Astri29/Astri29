import sqlite3

def createDatabase():
    try:
        sqliteConnection = sqlite3.connect('Biodata.db')
        cursor = sqliteConnection.cursor
        sqlite_create_table_query="""CREATE TABLE TB_BIODATA(
                                nim INTEGER PRIMARY KEY UNIQUE, 
                                nama TEXT NOT NULL,
                                prodi text NOT NULL,
                                hobi TEXT NOT NULL);"""
        
        print("Successfuly Connected to SQlite")
        cursor.execute(sqlite_create_table_query)
        sqliteConnection.commit()
        print("SQLite table created")
        cursor.close
        
    except sqlite3.Error as error :
        print("Error while creating a sqlite table", error)
    finally :
        if sqliteConnection:
            sqliteConnection.close
            print("sqlite connection is closed")

def insertDatatoDB(*data):
    try:
        sqliteConnection = sqlite3.connect('Biodata.db')
        cursor = sqliteConnection.cursor()
        print("Succesfully Conneted to SQLite")
        
        sqlite_insert_query = """INSERT INTO TB_BIODATA
                            (nim, nama, prodi, hobi)
                            VALUES
                            (data[0], data[1], data[2], data[3])"""
       
        count = cursor.execute ("""INSERT INTO TB_BIODATA
                            (nim, nama, prodi, hobi)
                            VALUES
                            (?,?,?,?)""")
    (int(data[0], data[1], data[2], data[3]))
    sqliteConnection.commit
    print("Record inserted successfully into SqliteDb_develovers table", cursor.rowcount)
    cursor.close
        
    except sqlite3.Error as error :
    print("Failed to insert data into sqlite table", error)
    finally:
        if sqliteConnection:
            sqliteConnection.close
            print("The SQLiite connection is closed") 
            
