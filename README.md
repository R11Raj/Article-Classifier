# Article-Classifier
Article Classification using Wordnet and N-grams

<h3>Dependencies</h3>
<ul>
<li>Get API key from New York Times developer site and The Guardian developer site.
<li>nltk.download('punkt')</li>
<li>nltk.download('averaged_perceptron_tagger')</li>
<li>nltk.download('wordnet')</li>
</ul>

<h2>Overview</h2>
The Classifier classifies articles into Four categories : Terror,Crime,Cancer and Health.
I have trained it using new using articles from New York times and The Guardian
for each article retrieved I have three properties.

|   Type   |    Title   |    Content     |

<h3>Datasets</h3>
<ul>
<li>Training Data : around 7K articles for all four categories</li>
<li>Validation Data : around 800 articles i.e. 200 for each category</li>
<li>Test Data : around 800 articles i.e. 200 for each category but completely unknown</li>
</ul>

<h4>Data Collection</h4>
Code from getting data from NYTimes and Guardian and also saving it into the appropriate format is in the file "get data.ipynb" and data is saved in "Train Data" Directory.

<h4>BoW and Context Words</h4>
In this experiment I have two versions of context words i.e. V1 and V2.
<ul>
<li>V1: first set of context words in which health category has more words then the rest.</li>
<li>V2: Final set of context words which has similar number of words for all categories.</li>
</ul>

The file "Preprocess and get context words.ipynb" contains the code for this stage.
This stage contains:
<ul>
<li>Preprocessing</li>
<li>Noun Extraction from Title and Content</li>
<li>Context word extraction using WUP similarity</li>
<li>Saving context words using pickle module</li>
<li>The above steps are repeated for each Category of articles mentioned in the overview section.</li>
</ul>

<h4>Building N gram Data frequencies</h4>
I have used Python dictionaries to build different N-gram data frequencies for context words

<h4>Unlabled Article Classification</h4>
The following two approaches were used:
<ul>
<li>BW-CW : N-gram weight followed by Context Weight</li>
<li>Kesalj Similarity</li>
</ul>
The above mentioned approaches were caried out for four types of N-gram data:
<ul>
<li>Bigram</li>
<li>Trigram</li>
<li>Quadgram</li>
<li>Pentagram</li>
</ul>

Building N-gram data and article classification is done in a single file named "Bigram.ipynb","Trigram.ipynb","Quadgram.ipynb" and "Pentagram.ipynb". 

<h1>Flow to run the code</h1>
<ul>
<li>"get data.ipynb" :ignore if you want to use the default data</li>
<li>"Preprocessing and get context words.ipynb" :ignore if you want to use pre-obtained context words</li>
<b>Note: Preprocessing and getting context words can take hours to finish so better to use pre-obtained ones.</b>
<li>The following files can be run in parallel</li>
<li>"Bigram.ipynb"</li>
<li>"Trigram.ipynb"</li>
<li>"Quadgram.ipynb"</li>
<li>"Pentagram.ipynb"</li>
<b>Note: The above files load both V1 and V2 sets so both BW-CW and Kesalj codes can run only one set of context words either V1 or V2. Seperate metric calculations cell are available in the files.</b>
</ul>

<h1>Conclusion</h1>
The experiment resulted in Bigram has better F scores then the rest in both approaches and both the approaches had similar scores for all N-gram data.
Different metrics obtained from the above experiment are stored in text format in the "Results" directory.
