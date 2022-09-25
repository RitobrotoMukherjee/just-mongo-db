## Use `$lookup` to join **collections**

---

## Join `source` with `topics`
```
db.source.aggregate([
    {
        $lookup: {
            from: "topics",
            localField: "topic_name",
            foreignField: "name",
            as: "topics"
        }
    }
])
```

## Complex `$lookup` -> `topics` with `source`