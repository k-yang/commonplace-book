Without indexes, MongoDB performs a collection scan to select the documents matching the query. If an index exists, it limits the number of documents it must inspect.

The \_id field gets a default index. It prevents one from inserting two documents with the same \_id field.

# Creating an index
```js
collection.createIndex( { name : -1 }, function(err, result){
		console.log(result);
		callback(result);
	} 
);
```

# Index Types
There are many index types
## Single Field
Indexes a single field of a document. The sort order does not matter because MongoDB can traverse the index in either direction.

## Compound INdex
User-defined index on multiple fields. The order of the fields in the compound index matters and so does sort order. 