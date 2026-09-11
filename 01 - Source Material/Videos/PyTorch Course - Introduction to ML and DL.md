2026-09-04 09:48

Course: [pyTorch YouTube Course](https://www.youtube.com/watch?v=V_xro1bcAuA&t=637s)
Stopping Point: [53:33](https://www.youtube.com/watch?v=V_xro1bcAuA&t=637s)

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

**Chapter 1 and 2**
- Google's rule: *"if you can write a simple-rule based approach instead of machine learning, do that."*
- What is it (DL/ML) good for?
	- Long + complex lists of rules
	- Continually changing environments
	- Discovering new insights within large data collections
		- Imagine writing rules for 101 different types of foods
- Deep learning negatives
	- Explanability (hard to track the patterns learned)
	- Refer to google's rule of machine learning
	- Can't have *any* errors
	- Typically you need large amounts of data

**Chapter 3: ML vs DL**
- In general:
	- ML works great on structured data (spreadsheets)
		- Models: tree-based, XGBoost, support vector machine, and many more
		- Now referred to as shallow algorithms
	- DL on unstructured data (text, audio, images)
		- Neural networks, CNNs, transformers, RNNs

**Chapter 4: Neural Networks**
- Pipeline:
	- Inputs --> numerical encoding --> learns representation (patterns/features/weights) --> outputs (representation outputs) --> convert outputs into human-understandable 
	- ![[Pasted image 20260904100422.png]]
- Basic anatomy:
	- Input layer --> hidden layer(s) --> output layer
	- Each layer uses linear or non-linear lines to infer these patterns from the data

**Chapter 5: Different Learning Paradigms**
- Supervised learning --> you have the data and the labels
	- You know which images are cats and which are dogs
- Unsupervised & self-supervised learning --> only have the images/data, model learns from the data itself
- Transfer learning --> transferring foundational learned patterns from a model to a new model (usually for a more specific use case)

**Chapter 7: What is PyTorch?**
- Popular deep learning framework in Python
- Whole stack: preprocess data, model data, deploy model in your application/cloud 
- Accelerate your code by running on a GPU/TPU




## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
