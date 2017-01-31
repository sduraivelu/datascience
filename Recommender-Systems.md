#### Summary of techniques
  1. Information Retrival - based on various similarity metrics of word count (user) distributions for documents (purchased items)
  2. Latent Semantic Analysis - use SVD to factorize word x document (or user x item) matrix and then reconstruct with fewer dimensions
  3. Collaborative Filtering (aka Alternating Least Squares)
  4. Restricted Boltzmann Machines (see Hinton course notes)

#### ["People Who Like This Also Like ... " Part 2: Finding Similar Music using Matrix Factorization](http://www.benfrederickson.com/matrix-factorization/) (1/31/17)
* "Matrix Factorization methods can generate matches that are impossible to find with the techniques in my original [IR] post [below]."
* Covered techniques: Latent Semantic Analysis ([SVD](https://jeremykun.com/2016/04/18/singular-value-decomposition-part-1-perspectives-on-linear-algebra/) of BM25 weights), (Implicit) Alternating Least Squares (aka Collaborative Filtering (for implicit datasets))
* Spotify uses a matrix factorization technique called [Logistic Matrix Factorization]() to generate their lists of related artists. This method has a similar idea to Implicit ALS: it's a confidence weighted factorization on binary preference data - but uses a logistic loss instead of a least squares loss

#### ["People Who Like This Also Like ... " Part 1: Distance Metrics for Fun and Profit](http://www.benfrederickson.com/distance-metrics/) (1/30/17)
* "most common way of dealing with this problem is [Jaccard distance](http://en.wikipedia.org/wiki/Jaccard_index), which normalizes the intersection size of the two sets by dividing by the total number of users that have listened to either artist."
* "Cosine based methods: The set based methods throw away a ton of useful information: how often the user has listened to the artist."
  * "Cosine distance succeeds in bringing up more relevant similar artists than the set based methods, but unfortunately there is also significantly more noise"
  * "While there are a bunch of more principled methods to overcome this ... one simple hack that I've seen used before is to smooth the cosine by the number of overlapping users
* "BM25 usually produces much better results than TF-IDF ... between the step function used in the Jaccard distance (K1 = 0) and the linear weighting used in the Cosine distance (K1 = +infinity)"
*  [Information Retrieval: Implementing and Evaluating Search Engines](https://www.amazon.ca/Information-Retrieval-Implementing-Evaluating-Engines/dp/0262026511): Learning to Rank, Relevance Feedback and Search Result Fusion. The Manning IR book is also decent and [freely available online](http://nlp.stanford.edu/IR-book/pdf/irbookonlinereading.pdf). [FWC - or just use [Lucene](http://lucene.apache.org/core/4_9_1/core/org/apache/lucene/search/similarities/TFIDFSimilarity.html#formula_tf)?]

#### [Wikipedia: Netflix Prize](https://en.wikipedia.org/wiki/Netflix_Prize)

#### [Stackoverflow: How to Implement A Recommendation System?](https://stackoverflow.com/questions/6302184/how-to-implement-a-recommendation-system#6302223) (1/30/17)
* use keywords (also has a link to a [list of stop words](http://en.wikipedia.org/wiki/Stop_words))

#### [Scaling Recommendation Engine: 15,000 to 130M Users in 24 Months [RS Labs]](https://www.retentionscience.com/scalingrecommendations/?utm_campaign=Data%2BElixir&utm_medium=email&utm_source=Data_Elixir_116) (1/30/17)
* this company appears to have built itself on recommendation systems
* "The resultant rule: 'Select the top items from the category that the user has already bought.' ... The users' purchase categories turned out to be a very strong latent factor"
* "The 'jaccard-semantic duplication annotation scheme,' was implemented which would figure out duplicate items and categories based on their textual description."
* "This led us to tap the feedback data to figure out specifically which recs schemes were performing well in order to gain insight into items that interested people."
* "metrics to measure the diversity and novelty of our recommendations"
* "we gambled with Spark. Again, it proved to be a good decision, as Spark soon became the industry leader for Machine Learning and Big Data analytics due to its elegant APIs for manipulating distributed data, growing machine learning library, and effective fault tolerance mechanisms"
* "Scala was adapted as the language of choice and refactored all our procedural code into a single functional machine learning repository"
* "Our current architecture looks like [this](https://www.retentionscience.com/wp-content/uploads/2017/01/image8.png)"

#### [Matrix Factorization with Tensorflow](http://katbailey.github.io/post/matrix-factorization-with-tensorflow/)