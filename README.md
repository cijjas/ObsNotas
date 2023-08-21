hola

```dataview
TAble sort(rows.file.link) as Contiene, rows.file.cday as "Date created"
FROM "Economía" 
WHERE !contains(file.folder, "_Archive") AND !contains(file.name, "_Working on")
GROUP BY file.folder as Economía
sort Economía asc
```

```dataview
TAble sort(rows.file.link) as Contiene, rows.file.cday
FROM "PAW" 
WHERE !contains(file.folder, "_Archive") AND !contains(file.name, "_Working on")
GROUP BY file.folder as PAW
sort Economía asc
```


```dataview
TAble sort(rows.file.link) as Contiene, rows.file.cday as "Date created"
FROM "Protos" 
WHERE !contains(file.folder, "_Archive") AND !contains(file.name, "_Working on")
GROUP BY file.folder as Protos
sort Economía asc
```

```dataview
TAble sort(rows.file.link) as Contiene, rows.file.cday as "Date created"
FROM "TLA" 
WHERE !contains(file.folder, "_Archive") AND !contains(file.name, "_Working on")
GROUP BY file.folder as TLA
```
