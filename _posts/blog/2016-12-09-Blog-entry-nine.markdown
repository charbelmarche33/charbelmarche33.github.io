---
layout: post
title:  "Using Wild Cards With PSYCOPG"
date:   2016-12-09 24:51:11
categories: blog
---

When running queries on a data base you may come across a situation where you want to use a wildcard in a query. The problem is that the cursor.execute() funtion automatically puts you paramters in quotes, which is why this would not work. So what you need to do is add the wildcard characters to the variable in the tuple that you are passing in like this:

```
cur.execute("SELECT * FROM stores where name LIKE %s OR type LIKE %s ORDER BY name;", ('%'+searchTerm+'%', '%'+searchTerm+'%'))
```

Hope this helps someone out there!