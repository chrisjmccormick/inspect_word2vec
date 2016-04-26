# inspect_word2vec
Google [released](https://code.google.com/archive/p/word2vec/ "Homepage for Google's Word2Vec code and pre-trained models") a large Word2Vec model that they trained on roughly 100 billion words from a Google News dataset. It contains exactly 3 million words, and the word vectors have 300 features each.

I was curious to explore some aspects of that 3 million word list, and that's what this project is about.

If you're interested in actually applying Word2Vec to a problem, I recommend the Python package `gensim`--it's what I've used here to interact with the pre-trained Google model.

If you'd like to browse the 3M word list in Google's pre-trained model, you can just look at the text files in the "vocabulary" folder. I split the word list across 50 files, and each text file contains 100,000 entries from the model. I split it up like this so your editor wouldn't completely choke (hopefully) when you try to open them. The words are stored in their original order--I haven't sorted the list alphabetically. I don't know what determined the original order.

For example:

* Does it include stop words? 
    * Answer: Some stop words like "a", "and", "of" are *excluded*, but others like "the", "also", "should" are *included*.
* Does it include misspellings of words?
    * Answer: Yes. For instance, it includes both "mispelled" and "misspelled"--the latter is the correct one.
* Does it include commonly paired words?
    * Answer: Yes. For instance, it includes "Soviet_Union" and "New_York".
* Does it include numbers?
    * Answer: Not directly; e.g., you won't find "100". But it does include entries like "###MHz_DDR2_SDRAM" where I'm assuming the '#' are intended to match any digit.

# The Code    
3 million words is a lot, so the full list of words is unwieldy. The code writes out the word list to 30 files with 100k words each.

Once you've loaded the model, you can also query it directly to check if a particular entry is present or not.
    
In order to run this, you're going to need to download the [binary file of Google's model](https://drive.google.com/file/d/0B7XkCwpI5KDYNlNUTTlSS21pQmM/edit?usp=sharing). It's 1.5GB, so I can't include it in the GitHub project.
