#### [How to Use t-SNE Effectively](http://distill.pub/2016/misread-tsne/) (7/12/17)
* "A second feature of t-SNE is a tuneable parameter, “perplexity,” which says (loosely) how to balance attention between local and global aspects of your data. The parameter is, in a sense, a guess about the number of close neighbors each point has."
* "The t-SNE algorithm adapts its notion of “distance” to regional density variations in the data set. As a result, it naturally expands dense clusters, and contracts sparse ones, evening out cluster sizes."
* "There may not be one perplexity value that will capture distances across all clusters—and sadly perplexity is a global parameter."
* "In fact, these features are saying useful things about high-dimensional normal distributions, which are very close to uniform distributions on a sphere: evenly distributed, with roughly equal spaces between points. Seen in this light, the t-SNE plot is more accurate than any linear projection could be."
* "t-SNE tends to expand denser regions of data"
  * FWC - this seems like a huge benefit - the problem with a lot of data is uneven distribution - could this be used to de-bias fake news, the main problem with which is sampling bias (kws: truthiness)

#### [Reducing Dimensionality from Dimensionality Reduction Techniques](https://medium.com/towards-data-science/reducing-dimensionality-from-dimensionality-reduction-techniques-f658aec24dfe) (7/12/17)
* "Another great plus in Auto Encoders, is that since by the end of the training we have the weights that lead to the hidden layer, we can train on certain input, and if later on we come across another data point we can reduce its dimensionality using those weights without re-training"

#### [Two Decades of Recommender Systems at Amazon.com](https://www.computer.org/csdl/mags/ic/2017/03/mic2017030012.html) (7/12/17)

#### [A Statistical View of Deep Learning (III): Memory and Kernels 4](http://blog.shakirm.com/2015/04/a-statistical-view-of-deep-learning-iii-memory-and-kernels/) (5/10/17)
* "This highlights the deep relationship between deep networks and kernel machines: they are more than simply related, they are duals of each other."

#### [A Statistical View of Deep Learning (II): Auto-encoders and Free Energy](http://blog.shakirm.com/2015/03/a-statistical-view-of-deep-learning-ii-auto-encoders-and-free-energy/) (4/24/17)
* "Instead of considering perturbations in the observation space, we consider perturbations in the hidden space, obtained by using a prior p(z). The hidden variables are now random, latent variables.  Auto-encoders are now generative models that are straightforward to sample from."
* "Rather than designing the penalty by hand, we are able to *derive* the form this penalty should take, appearing as the KL divergence between the the prior and the encoder distribution."

#### [Tutorial - What is a variational autoencoder?](https://jaan.io/what-is-variational-autoencoder-vae-tutorial/) (4/17/17)
* "We measure this using the reconstruction log-likelihood `log p(x∣z)` whose units are *nats*."
* "If the encoder outputs representations `z` that are different than those from a standard normal distribution, it will receive a penalty in the loss. This regularizer term means 'keep the representations `z` of each digit sufficiently diverse.' If we didn’t include the regularizer, the encoder could learn to cheat and give each datapoint a representation in a different region of Euclidean space [FWC - i.e. not normal]. This is bad, because then two images of the same number (say a 2 written by different people, 2_alice​​ and 2_bob​​) could end up with very different representations z_alice, z_​bob​​. We want the representation space of `z` to be meaningful, so we penalize this behavior. This has the effect of keeping similar numbers' representations close together (e.g. so the representations of the digit two z_alice, z_bob, z_charley​​ remain sufficiently close)."
* "Now we can think about **inference** in this model. The goal is to infer good values of the latent variables given observed data, or to calculate the posterior p(z∣x)."
* "Note that at the start of training, the distribution of latent variables is close to the prior (a round blob around 0)."
* "**Inference**: in neural nets, inference usually means prediction of latent representations given new, never-before-seen datapoints. In probability models, inference refers to inferring the values of latent variables given observed data."

#### [Collaborative Filtering for Implicit Feedback Datasets](http://yifanhu.net/PUB/cf.pdf) by Hu, Koren, Volinsky, 2008 (4/13/17)
* This is the original *implicit* recommendation system paper.
* "Transferring the raw observations (r_ui) into two separate magnitudes with distinct interpretations: preferences (p_ui) and confidence levels (c_ui).  This better reflect the nature of the data and is essential to improving prediction accuracy"
* Explaining recommendations "helps in improving the users' trust in the system and their ability to put recommendations in the right perspective."
  * "Interestingly, our alternating least squares model enables a novel way to compute explanations ... reduces our latent factor model into a linear model that predicts preferences as a linear function of past actions ... each past action receives a separate term in forming the predicted p̂hat_ui, and thus we can isolate its unique contribution"

#### [Netflix phasing out ratings in favor of thumbs](https://www.theguardian.com/culture/2017/mar/17/netflix-thumbs-up-down-rating-system) (3/20/17)
* Netflix is phasing out ratings in favor of thumbs partly because the rating predictions don't seem to be very good--they're too heavily based on users who rate lots of stuff.  Possible also that negative ratings just aren't that accurate.  The article suggests that usage statistics are better for recommenders than ratings themselves.

#### Hashing for Similarity Search: A Survey. Wang. 2014 (3/6/17)
* file:///home/fred/Documents/articles/autoencoders/hashing_4_similarity_search_survey_wang_1408.2927.pdf
* It seems that hashing deals mostly with dimensionality reduction as opposed to effective feature engineering (also in reduced dimensions) towards the end of better representations.  I don't really care about the dimensionality reduction part so much as the feature engineering / representation part.

#### Variational Inference: A Review for Statisticians. Blei, Kucukelbir, McAuliffe. 2016. (3/6/17)
* file:///home/fred/Documents/articles/variational_inference_1601.00670v4.pdf
* Thus, **variational inference is suited to large data sets and scenarios where we want to quickly explore many models; MCMC is suited to smaller data sets and scenarios where we happily pay a heavier computational cost for more precise samples**. For example, we might use MCMC in a setting where we spent 20 years collecting a small but expensive data set, where we are confident that our model is appropriate, and where we require precise inferences. We might **use variational inference when fitting a probabilistic model of text to one billion text documents and where the inferences will be used to serve search results** [kws: semantic hashing] to a large population of users.
* MCMC is a tool for simulating from densities and variational inference is a tool for approximating densities.
* The **goal of variational inference is to approximate a conditional density of latent variables given observed variables** ... with optimization.

#### [Collaborative Filtering with Stacked Denoising AutoEncoders and Sparse Inputs](https://hal.inria.fr/hal-01256422v1/document). Strub and Mary, 2016 (2/28/17)
* Three processes are described to corrupt data:
  1. Gaussian Noise : Gaussian Noise is added to a subset of the input
  2. Masking Noise : A fraction ν of the input is randomly forced to be zero.
  3. Salt-and-Pepper Noise : A fraction ν of the input is randomly forced to be one of the input maximum/minimum.
* Using masking noise has two great advantages in our current issue. First, it works as a
strong regularizer. Second, it **trains the autoencoder to predict missing values**.
* The first encoding layer is 1/10 th of the input size, the second layer is 1/12 th of the input size.
  * They first train a order-1 AE (input -> 1/10 hidden -> input reconstruction)
  * Then the train another order-1 AE (1/10 hidden -> 1/12 hidden -> 1/10 reconstruction
  * Then they stack them into an order-2 and gently train
* Even if DAE loss and sparsity already entail a strong regularization, a weight decay is required.
  * FWC - but perhaps not in a VAE?
* Vencoders (item AEs) performs poorly on jester while they are excellent on movieLens. More research must be done to check whether Uencoders (user AEs) and Vencoders have similar errors.
  * FWC - kws: synthetic users
* Whenever new items occurs, Vencoders need to be retrained since it changes the size of the input/ouput layer. Yet, Vencoders immediately provide additional estimates for new users. The situation is reversed for Uencoders.
  * FWC - no Vencoder retraining necessary though if items are not discrete (e.g. Levenstein for words or some other "soft" similarity metric based on representations/embeddings for other things)

#### [Netflix Recommendations: Beyond the 5 stars (Part 1)](http://techblog.netflix.com/2012/04/netflix-recommendations-beyond-5-stars.html) (2/27/17)
* "we can observe viewing statistics such as whether a video was watched fully or only partially"
* "75% of what people watch is from some sort of recommendation"
* "in many parts of our system we are not only optimizing for accuracy, but also for [**freshness** and] **diversity**"
  * i.e. maximize stdev in addition to minimizing RMSE
* "**awareness**. We want members to be aware of how we are adapting to their tastes. This not only promotes trust in the system, but encourages members to give feedback"
* "**explanations** as to why we decide to recommend a given movie or show"
* "different rows that rely mostly on your **social** circle to generate recommendations"
* "**Similarity** ... can be between movies or between members, and can be in multiple dimensions such as metadata, ratings, or viewing data"
* "**ranking**, the choice of what order to place the items in a row, is critical in providing an effective personalized experience"
* [Part 2](http://techblog.netflix.com/2012/06/netflix-recommendations-beyond-5-stars.html)
  * `frank(u,v) = w1*p(v) + w2*r(u,v) + b`, where u=user, v=video item, p=popularity and r=predicted rating
  * "To measure model performance offline we track multiple metrics used in the machine learning community: from ranking measures such as normalized discounted cumulative gain, mean reciprocal rank, or fraction of concordant pairs, to classification metrics such as accuracy, precision, recall, or F-score."
  * "**Over time we have reformulated the recommendation problem to the question of optimizing the probability a member chooses to watch a title and enjoys it enough to come back to the service.**"

#### [Hybrid Collaborative Filtering with Autoencoders](https://arxiv.org/abs/1603.00806) (2/23/17)
* file:///home/fred/Documents/articles/recommender_systems/hybrid_collab_filt_w_AEs_1603.00806v3.pdf) 
* Really nicely written, clear and short paper.
* Implements a denoising autoencoder that incorporates side information (by linking representations into the autoencoder network) to help with the cold start problem.

#### [The WellDressed Recommendation Engine](https://deeplearning4j.org/welldressed-recommendation-engine) (2/17/17)
* "data feeds from merchants offer few categorization options, and on top of that, every data feed is very different from the other"
* "I decided to focus on Title, Description and Category/Keyword fields. Title and Description tend to give valuable, specific hints on what a garment actually is. Category works as a broad identification.  I do not use image data for garment identification.... The copy of the text tends to be the only true identifier of a garment type."
* "I use [word2vec](https://deeplearning4j.org/word2vec.html) to create vectors. A word needs to show at least 10 times, and I get 40 vectors for each wordset. I then proceed to sum all vectors per title, description and category, resulting in 120 vectors."
  * FWC - I think what he means by this is that he creates "40-*dimensional* vector" embeddings and then sums over the words in each of the 3 wordsets to get a 120-dimensional embedding vector for each item/garment.
* "The database has a lot of jeans and t-shirts, but very few tuxedoes and cummerbunds"
  * He has 84 garment types so he samples 1 from each of the 84 and he does this 1000 times to get an 84,000-point set.
  * So how does one count the number of URL/document types?  One possible way could be to treat each of the 120 dimensions of the item embeddings as a different type--and sample uniformly from each of those 120 *feature type* classes.
* **The algorithm described here is more for classification than for recommendations/ratings**.  It seems to be used as input to a recommendation system (i.e. first classify garment type then recommend one of the garments of a given type--filter)  It seems to predict one of 84 labels/categories given a 120-dim vector.
  * As noted, the author's first solution used "keywords with a complex rule-and weight-system" to predict category. "Title and Description tend to give valuable, specific hints on what a garment actually is."  This is the crux: figuring out what type of a garment is.

#### [Mozilla Context Graph: A recommendation system for the web](http://venturebeat.com/2016/07/06/mozilla-is-building-context-graph-a-recommender-system-for-the-web/)

#### [The truth is that people just don't dislike things online that often](http://www.benfrederickson.com/rating-set-distributions/)
* even if they did offer a dislike button, people just wouldn't use it often enough to justify the precious screen real estate it would take up.
* Most ratings are positive: more people watch good movies.
  * 15% of ratings are negative, but 30% of items rated have negative ratings.

#### Summary of techniques
  1. Information Retrival - based on various similarity metrics of word count (user) distributions for documents (purchased items)
  2. Latent Semantic Analysis - use SVD to factorize word x document (or user x item) matrix and then reconstruct with fewer dimensions
  3. Collaborative Filtering (aka Alternating Least Squares)
  4. Restricted Boltzmann Machines (see Hinton course notes)

#### ["People Who Like This Also Like ... " Part 2: Finding Similar Music using Matrix Factorization](http://www.benfrederickson.com/matrix-factorization/) (1/31/17)
* "Matrix Factorization methods can generate matches that are impossible to find with the techniques in my original [IR] post [below]."
* Covered techniques: Latent Semantic Analysis ([SVD](https://jeremykun.com/2016/04/18/singular-value-decomposition-part-1-perspectives-on-linear-algebra/) of BM25 weights), (Implicit) Alternating Least Squares (aka Collaborative Filtering (for implicit feedback datasets))
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