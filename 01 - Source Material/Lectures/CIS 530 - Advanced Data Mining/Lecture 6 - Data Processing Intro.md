2026-02-19 11:09

Course: #cis530 

## Big Ideas
- Sampling types: random sampling (with/without replacement), stratified sampling, and reservoir sampling
- DF, IDF, and TF-IDF are different ways to determine unique words in relation to all of the documents in the corpus
	- TF-IDF is term-frequency, inverse-document-frequency --> high rarity terms but frequent within the document
- Distributions: normal, power, and Zipf's law

## Key Concepts


## Notes
- Stratified sampling: splits data into several groups, draws random samples from each group
- Reservoir sampling: select each item with 1/n chance and replace the previous choice
	- E.g., item 1 will have probability of 1, then item 2 will have probability of 1/2 being put into memory slot
	- Probability that a given item is selected: $\frac{1}{n} * \frac{n}{N} = \frac{1}{N}$
		- (item selected) * (chance it makes it to the end)
- First cut --> basic preprocessing (remove white space, punctuation, etc.) and word count
- Second cut --> removing stop words (and, but, to)
- Document frequency: $DF(w)$: fraction of documents that contain word w.
	- $DF(w) = \frac{D(w)}{D}$
- Inverse document frequency (IDF): measure how rare a word is in a document:
	- $IDF(w) = \log\left( \frac{1}{DF(w)} \right)$
- TF-IDF(w,d) = TF(w,d) x IDF(w)
	- Gives you important and unique words
	- High rarity and high frequency
- Basic stats concepts: mean, median, mode, percentiles
- Some things are normal distributions, but not everything (power law)
- Power-law graphs can be expressed as a linear relationship in the log-log space

## Questions/Gaps/Concerns



## Follow-up 




## References

