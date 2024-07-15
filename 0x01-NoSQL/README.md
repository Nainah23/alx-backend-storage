# alx-backend-storage: 0x01-NoSQL

This repository contains tasks and scripts for interacting with MongoDB. Each task corresponds to a specific script or Python function, demonstrating different MongoDB operations.

## Table of Contents

1. [List all databases](#list-all-databases)
2. [Create a database](#create-a-database)
3. [Insert document](#insert-document)
4. [All documents](#all-documents)
5. [All matches](#all-matches)
6. [Count](#count)
7. [Update](#update)
8. [Delete by match](#delete-by-match)
9. [List all documents in Python](#list-all-documents-in-python)
10. [Insert a document in Python](#insert-a-document-in-python)
11. [Change school topics](#change-school-topics)
12. [Where can I learn Python?](#where-can-i-learn-python)
13. [Log stats](#log-stats)
14. [Regex filter](#regex-filter)
15. [Top students](#top-students)

---

### List all databases

**File:** `0-list_databases`

**Description:** Script to list all databases in MongoDB.

```bash
$ cat 0-list_databases | mongo
```

---

### Create a database

**File:** `1-use_or_create_database`

**Description:** Script to create or use the database `my_db`.

```bash
$ cat 1-use_or_create_database | mongo
```

---

### Insert document

**File:** `2-insert`

**Description:** Script to insert a document into the `school` collection. The document will have an attribute `name` with value "Holberton school".

```bash
$ cat 2-insert | mongo my_db
```

---

### All documents

**File:** `3-all`

**Description:** Script to list all documents in the `school` collection.

```bash
$ cat 3-all | mongo my_db
```

---

### All matches

**File:** `4-match`

**Description:** Script to list all documents with `name="Holberton school"` in the `school` collection.

```bash
$ cat 4-match | mongo my_db
```

---

### Count

**File:** `5-count`

**Description:** Script to display the number of documents in the `school` collection.

```bash
$ cat 5-count | mongo my_db
```

---

### Update

**File:** `6-update`

**Description:** Script to add a new attribute `address` with value "972 Mission street" to documents with `name="Holberton school"` in the `school` collection.

```bash
$ cat 6-update | mongo my_db
```

---

### Delete by match

**File:** `7-delete`

**Description:** Script to delete all documents with `name="Holberton school"` in the `school` collection.

```bash
$ cat 7-delete | mongo my_db
```

---

### List all documents in Python

**File:** `8-all.py`

**Description:** Python function `list_all` that lists all documents in a collection.

```python
def list_all(mongo_collection):
    return list(mongo_collection.find())
```

---

### Insert a document in Python

**File:** `9-insert_school.py`

**Description:** Python function `insert_school` that inserts a new document in a collection based on keyword arguments.

```python
def insert_school(mongo_collection, **kwargs):
    return mongo_collection.insert_one(kwargs).inserted_id
```

---

### Change school topics

**File:** `10-update_topics.py`

**Description:** Python function `update_topics` that changes all topics of a school document based on the name.

```python
def update_topics(mongo_collection, name, topics):
    mongo_collection.update_many({"name": name}, {"$set": {"topics": topics}})
```

---

### Where can I learn Python?

**File:** `11-schools_by_topic.py`

**Description:** Python function `schools_by_topic` that returns the list of schools having a specific topic.

```python
def schools_by_topic(mongo_collection, topic):
    return list(mongo_collection.find({"topics": topic}))
```

---

### Log stats

**File:** `12-log_stats.py`

**Description:** Python script that provides stats about Nginx logs stored in MongoDB.

```python
from pymongo import MongoClient

client = MongoClient('mongodb://127.0.0.1:27017')
nginx_collection = client.logs.nginx

print(f"{nginx_collection.count_documents({})} logs")
print("Methods:")
methods = ["GET", "POST", "PUT", "PATCH", "DELETE"]
for method in methods:
    count = nginx_collection.count_documents({"method": method})
    print(f"\tmethod {method}: {count}")

status_check = nginx_collection.count_documents({"method": "GET", "path": "/status"})
print(f"{status_check} status check")
```

---

### Regex filter

**File:** `100-find`

**Description:** Script to list all documents with `name` starting with "Holberton" in the `school` collection.

```bash
$ cat 100-find | mongo my_db
```

---

### Top students

**File:** `101-students.py`

**Description:** Python function `top_students` that returns all students sorted by average score.

```python
def top_students(mongo_collection):
    return mongo_collection.aggregate([
        {"$project": {
            "name": 1,
            "averageScore": {"$avg": "$topics.score"}
        }},
        {"$sort": {"averageScore": -1}}
    ])
```

---
