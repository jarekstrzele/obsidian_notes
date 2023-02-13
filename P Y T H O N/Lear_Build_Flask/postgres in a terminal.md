[[PostgreSQL]]


# Postgres in a termial
```bash
>>> from run import db, Publication
>>> pub = Publication(100, 'Oxford Publi')
>>> pub.id   # -> 100
>>> pub.name # -> Oxford Publi

# add this object to the db
>>> db.session.add(pub)
>>> db.session.commit()
# `dir(db)` to see all db attributes
# `dir(db.session)` to see all db.session attributes (add, commit, ...)
```

```bash
>>> para = Publication(102, 'Paramount')
>>> oracle = Publication(103, 'Oracle')
>>> db.session.add_all([para, oracle])
>>> db.session.commit()
```


==Session Object==
- temporary storage in memory
- like a staging zone

In PostAdmin: Databases-> catalog_db -> Schemas -> public -> tables