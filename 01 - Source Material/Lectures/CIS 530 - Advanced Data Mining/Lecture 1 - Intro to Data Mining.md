2026-01-29 11:05

Course: #cis530

## Big Ideas
- Main types of data: 
	- Transaction data, document data, network data, genomic sequences, behavioral data, and environmental data
- Data --> collection of attributes that describe an object
- Data can be categorical (qualitative) or numeric (quantitative)
	- Each has different characteristics
- Data be represented differently depending on use case: BoW (bag of words) for document data, or binary representation for transaction data
- Data mining: analysis of often large data sets to find unsuspected relationships and to summarize the data in novel ways
	- Data mining is also the discovery of data models
- Once clean, data can be applied in unique ways: clustering (group similar points together) or classification (assign a class to previously unseen datapoints)

## Notes
- Data is a collection of attributes used to describe an object
- Attribute: property or characteristic of an object
	- Eye color, height, weight, job, etc. are attributes for a person
- Size: number of objects; dimensionality: number of attribute; sparsity: proportion of unpopulated object-attribute pairs
	- Sparsity is often calculated as a ratio of the unpopulated pairs compared to the total object-attribute pairs
---

- Categorical (qualitative)
	- Non-numeric data
	- Nominal (no order or comparison)
		- Cannot say blue eyes > green eyes
	- Ordinal (can be ordered/compared)
		- We can say bad < fair < good
		- But doesn't have a numeric meaning (cannot do good-bad)
	- Special case: binary attributes
- Numeric (quantitative)
	- Dates, temperatures, time, length, value, count
	- Discrete (counts of chairs) or continuous (temperature)
---

- Bag-of-words (BoW) representation for document data
	- Word order is ignored
	- Only the frequency of words within the document matter
	- i.e., Document 1: health (3), wow (1), heart (3)
	- Vector for document 1 would be: [3, 1, 3]
- Binary representation for transaction data

| Bread | Coke | Milk |
| ----- | ---- | ---- |
| 0     | 0    | 1    |
| 1     | 1    | 0    |
- Based on this, you can find patterns between the data
	- Maybe people who commonly buy bread also buy coke
- Time series
	- Sequence of ordered (over "time") numeric values
	- Ex: stock prices, weather
- Sequenced data: such as genomic sequences have a defined order
- Naturally, this type of data examples can be used for a wide range of applications
	- BoW can be used to group related documents together, binary representations can recommend better products for users, and time series can be used to predict stock prices
	- Or with network data: Who is the most important node?, How does information spread on the network?
---

- Can identify sets of items (itemsets) occurring frequently together
- Produce dependency rules which will predict occurrence of an item based on occurrences of other items
	- Dependency rules not covered in this lecture 
- Text mining can also be used to find associated phrases within text
	- Such as "artificial intelligence" often appearing in the same document as "machine learning" or "data mining"
- Recommendations are another common use case, such as in Netflix or social media
---

- What is clustering?
	- Find a similarity measure among the data points such that:
		- Data points within a cluster are more similar to one another
		- Data points in separate clusters are less similar to one another
	- How to perform similarity measures?
		- Continuous attributes --> Euclidean Distance
		- Other methods like cosine similarity, Manhattan distance, etc.
- Document clustering
	- Find groups of documents that are similar to each other based on the terms appearing in them
	- I.e., technology articles will use different words more commonly compared to biology articles
- Classification goal: previously unseen records should be assigned a class as accurately as possible



## Questions/Gaps/Concerns
- What are the limitations or clustering based on similarity measure?
- How can edge cases be handled with clusters (i.e., points that are equal parts two distinct groups)?
- Clarification on discrete vs. continuous? Is it really as simple as discrete are basically int type and continuous are floats?


## Follow-up 




## Reference
- [Lecture Slide Deck 2](https://canvas.umassd.edu/courses/20828/files/9715575?module_item_id=1386360)
- Slides not posted yet (would be slide deck 3)
