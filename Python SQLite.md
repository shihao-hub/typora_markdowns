# SQLite

> 重点：
>
> 1、sqlite3 的数据类型主要就 number、string、blob（INTEGER、REAL、NUMERIC、TEXT、BLOG）

## 创建 SQLite 数据库



## 常用函数

### execute

```python
import os.path
import sqlite3
import sys
import time
from typing import Optional
from sqlite3 import Connection, Cursor

DATABASE_PATH = "sqlite_test.db"

def version1():
    conn: Optional[Connection] = None
    try:
        conn = sqlite3.connect(DATABASE_PATH)
        cur: Cursor = conn.cursor()

        cur.execute("select SQLITE_VERSION()1")
        for _ in range(2):
            data = cur.fetchone()
            print(f"SQLite version: {data}")
        conn.commit()
    except sqlite3.Error as e:
        print(f"Error {e.args[0]}")
        sys.exit(1)
    finally:
        if conn:
            conn.rollback()  # 不用 with，需要手动提交更改并提供我们自己的错误处理
            conn.close()
```

> 注意：以上代码没有使用 with 关键字，需要手动关闭和处理错误即回滚

### executemany

```python
CAR_VALUES = (
    (1, 'Audi', 52642),
    (2, 'Mercedes', 57127),
    (3, 'Skoda', 9000),
    (4, 'Volvo', 29000),
    (5, 'Bentley', 350000),
    (6, 'Hummer', 41400),
    (7, 'Volkswagen', 21600)
)

conn: Connection = sqlite3.connect(DATABASE_PATH)
with conn:
    cur: Cursor = conn.cursor()
	# cars table
    cur.execute("DROP TABLE IF EXISTS cars;")
    cur.execute("create table cars(id INT, name TEXT, price INT);")
    cur.executemany("insert into cars values(?, ?, ?)", CAR_VALUES)
```

> 注意：cur.executemany 执行完，lastrowid 并不会变。所以没办法确定最后插入的行的 ID。

### executescript

```python
con = sqlite.connect('ydb.db')
cur = con.cursor()
cur.executescript("""
	DROP TABLE IF EXISTS cars;
	CREATE TABLE cars(id INT, name TEXT, price INT);
	INSERT INTO cars VALUES(1,'Audi',52642);
	INSERT INTO cars VALUES(2,'Mercedes',57127);
	INSERT INTO cars VALUES(3,'Skoda',9000);
	INSERT INTO cars VALUES(4,'Volvo',29000);
	INSERT INTO cars VALUES(5,'Bentley',350000);
	INSERT INTO cars VALUES(6,'Citroen',21000);
	INSERT INTO cars VALUES(7,'Hummer',41400);
	INSERT INTO cars VALUES(8,'Volkswagen',21600);
	""")
con.commit()
# 注意：没有使用 with 关键字，需要 try except finally，并在 finally 块中调用 conn.rollback()
```

> 注意：该方法主要作用应该是用来导入数据的，读取 .sql 文件然后调用该函数执行！

### lastrowid

### fetchall

### fetchone

## 字典游标

```python
def test_dict_cursor():
    """ 测试字典游标 """
    with sqlite3.connect(DATABASE_PATH) as conn:
        # 注意：下面这行代码执行了之后在 cur = conn.cursor 才能改变 cursor 的返回值
        conn.row_factory = sqlite3.Row
        cur = conn.cursor()
        
        print("字典游标：")
        cur.execute("SELECT * FROM cars;")
        for row in cur.fetchall():
            row: sqlite3.Row = row
            # 注意：此处的 row 不是 dict，没有 get 方法
            print(f"{row['id']} -> {row.keys()} - {dict(row)}")
```



## 参数化语句

```python
# # SQLite
# ## Python SQLite 参数化语句
with sqlite3.connect(DATABASE_PATH) as conn:
    cur = conn.cursor()
    
    # ### 带问号的参数化语句
    cur.execute("UPDATE cars SET name=? where id=?", ("zsh_", 1))
    # ### 具有命名占位符的参数化语句
    cur.execute("UPDATE cars SET name=:name where id=:id", dict(name="zsh", id=2))
    # print(f"Number of rows updated: {cur.rowcount}")
```



## 插入图片和读取图像

```python
def test_insert_image():
    with sqlite3.connect(DATABASE_PATH) as conn:
        
        def read_image(path_):
            # 需要添加 check_image_file 逻辑
            try:
                with open(path_, "rb") as file:
                    return file.read()
            except IOError as e_:
                print(e_)
                sys.exit(1)
                
        cur = conn.cursor()
        # 有些人反对将图像放入数据库。在这里，我们只展示如何做。不讨论是否将图像保存在数据库中的技术问题。
        cur.execute("CREATE TABLE IF NOT EXISTS images(id INTEGER PRIMARY KEY ,data BLOB);")
        # BLOB: 二进制数据
		# cur.execute("INSERT INTO images values(NULL,?)", (sqlite3.Binary(read_image("./resources/cat.jpg")),))
        cur.execute("SELECT data FROM images;")
        with open("./resources/temp.jpg", "wb") as file:
            image_data = cur.fetchone()[0]
            file.write(image_data)
        
```



## 元数据、数据导出、数据导入、事务

```python
    with sqlite3.connect(DATABASE_PATH) as conn:
        cur = conn.cursor()

        # 根据提供的信息，我们打印列顺序号，列名称和列数据类型。
        # cur.execute('PRAGMA table_info(cars)')
        # data = cur.fetchall()
        # for d in data:
        #     print(f"{d[0]} {d[1]} {d[2]}")

        # 我们将 cars 表的内容打印到控制台。现在，我们也包括列的名称。记录与列名对齐。
        # cur.execute("SELECT * FROM cars;")
        # col_names = [cn[0] for cn in cur.description]
        # rows = cur.fetchall()
        # print(f"{col_names[0]:3} {col_names[1]:10} {col_names[2]:7}")
        # for row in rows:
        #     print(f"{row[0]:<3} {row[1]:<10} {row[2]:7}")

        # 在与元数据有关的最后一个示例中，我们将列出 ydb.db 数据库中的所有表。
        # cur.execute("SELECT name FROM sqlite_master WHERE type='table'")
        # rows = cur.fetchall()
        # for row in rows:
        #     print(row[0])

        # sqlite3 数据导出
        # format_ts = time.strftime('%Y%m%d_%H%M%S', time.localtime())
        # with open(f"./resources/backup_{format_ts}.sql", "w", encoding="utf-8") as file:
        #     data = '\n'.join(conn.iterdump())
        #     file.write(data)

        cur.execute("")

    # sqlite3 导入数据
    # > 注意：:memory: 内存数据库，程序运行结束则会清空！
    with sqlite3.connect(":memory:") as conn:
        cur = conn.cursor()

        with open("./resources/backup_20241005_212659.sql", "r", encoding="utf-8") as file:
            cur.executescript(file.read())

        print(":memory: database tables:")
        cur.execute("SELECT name FROM sqlite_master WHERE type='table';")
        for row in cur.fetchall():
            print(row)
```

