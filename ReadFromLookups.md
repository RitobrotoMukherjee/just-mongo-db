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
- Without query table `$match`
```
db.source.aggregate([
    {
        $lookup: {
            from: "topics",
            let: { source_topic_name: "$topic_name" },
            pipeline: [
                {
                    $match : {
                        $expr: {
                            $and: [
                                { 
                                    $eq: ["$name", "$$source_topic_name"] 
                                },
                                {
                                    $eq: ["$type", "Software"]
                                }
                            ]
                        },
                    }
                },
                { 
                    $project: {
                        name: 0
                    } 
                }
            ],
            as: "topicData"
        },
    }
])
```
- With query table `$match`
```
db.source.aggregate([
    { 
        $match: { source: ["Books", "Online"] } 
    },
    {
        $lookup: {
            from: "topics",
            let: { source_topic_name: "$topic_name" },
            pipeline: [
                {
                    $match : {
                        $expr: {
                            $and: [
                                { 
                                    $eq: ["$name", "$$source_topic_name"] 
                                },
                                {
                                    $eq: ["$type", "Software"]
                                }
                            ]
                        },
                    }
                },
                { 
                    $project: {
                        name: 0
                    } 
                }
            ],
            as: "topicData"
        },
    }
])
```