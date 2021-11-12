# Analysis of Dune
Matt Ryan

## Abstract

The *Dune* series by Frank Herbert has often been lauded as the foundation of modern science fiction literature and generally widely influential in pop-culture. Though many fans of Herbert's writing have praised all 6 of the original Frank Herbert installments in the franchise, the sequels to the original *Dune* (installments 2-6) have not escaped criticism for lack of accessibility and an alleged general lower quality of writing relative to the first **(cite goodreads ratings (4.24 out of 950,00, average of 3.9 out of ~500,000))**. With that in mind, in this project I want to attempt to examine topic/thematic differences and trends among all 6 of Herbert's *Dune* series, as well as between book 1 and the grouping of books 2-6 with the hopes to highlight observable and significant thematic/topical differences and relate topic strength to critical reception.

## Design

Because this is simply a thematic analysis problem isolated to a single corpus, there is less need to apply unsupervised learning techniques or attempt to design recommender systems. As such, I will focus more in-depth on topic-modeling techniques and topic evaluation. 


## Data

I used for my corpus the original 6 *Dune* books written by Frank Herbert: *Dune*, *Dune - Messiah*, *Children of Dune*, *God Emperor of Dune*, *Heretics of Dune*, and *Dune: Chapterhouse*. The text-string of each book was acquired by converting the text from e-book PDF's of each book into .txt files.  From these .txt files, I split the corpus into 140 documents, one for each chapter. Upon vectorizing our processed corpus, we received a **140 x 16,075 matrix**. 

## Algorithms


*Pre-processing*

To prepare the corpus for topic-modeling, it first needed to be adequately cleaned and processed. All punctuation and numbers were filtered from the text using RegEx, and then all text was converted to lowercase characters. All appropriate words were then lemmatized using WordNetLemmatizer() from the NLTK library, before the text was filtered for English stop words using the 'stop_words' parameter of each vectorizer used. 

An n-gram tokenized model was considered due to the importance of word ordering in novels, but was ultimately decided against to maintain a manageable dimensionality in relation to the length of the novels.

Finally, our corpus of chapter documents was vectorized twice, once with a count-vectorizer and once with a TF-IDF-vectorizer.

*Topic modeling*

Several topic models were considered in this exploration: Latent Semantic Analysis (LSA), Latent Dirichlet Analysis (LDA), and CorEx. In preparation for modeling, the corpus was fed into both count-vecorizers and TF-IDF vectorizers. 

*Evaluation*

The topics were assessed by their explained variance ratio, which was also used to hyper-tune the number of topics generated.




## Tools
*General Corpus Processing and Manipulation*
- pandas 
- NumPy
- SciPy.Sparse 
*Text Pre-processing*
- Natural Language Toolkit (NLTK) (lemmatization)
- RegEx
*Vectorization and Topic Modeling*
- SkLearn
  - .feature_extraction (.CountVectorizer, .TfidfVectorizer)
  - .decomposition.TruncatedSVD (Latent Semantic Analysis)
- CorEx
*Visualization*
- matplotlib


## Communication

Topics that explain most variance are book-plot tied, so ultimately it was difficult to track topic strength over the course of each book. However, subjectively the books that are most plot-driven and explored plot-lines related to Paul and Jessica are the highest rated. Looking forward, omitting major characters from analysis and doing a further investigation of writing style and structure over the books may yield more interesting results.

