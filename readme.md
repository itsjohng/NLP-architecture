# **Understanding the Language of Architecture**

----------------------

### **1. THE PROMPT**

The intent of this work was twofold. 1. Create a “base-line” domain specific word2vec model that can be used to draw latent relationships between architectural concepts through the way architecture is written about, and 2. As a case study, attempt to find if and how the meaning of particular architectural concepts have shifted over time

### **2. THE DATA**

The data used for this project was 161 architectural history/theory/criticism essays spanning about 50 years starting in the mid-1960s. I show these images for one important purpose. There is no consistency in the formatting for each document. Therefore, pre-processing techniques had to be generalized in such a way to minimize individual time spent on each document, while maximizing the value added for the model… 

… so, due to artifacts created through ‘designerly’ formatting, or image overlays, the pre-processing pipeline…

Pushes strings like this through <2342dfs adfgdfgb yuutuut>. Fortunately, I haven’t to this point seen adverse effects on the results from the model due to this issue, but this process would be improved upon in future iterations.


### **3. THE MODEL**

I tried to evaluate the strength or veracity of the model by asking it to find similarities between influential architects, and to my surprise, it provided other architects who practiced in the same time frame, and share similar ideologies. Robert Venturi, famous post modern architect famous for the idea of the ‘decorated shed’ provided Colin Rowe, influential educator and theorist in that era, Robert A.M. Stern, prolific american architect whos early work was considered post-modern.

When given Le Corbusier, iconic modernist architect.. it provided Mies Van der Rohe, german modernist known among many other things for coining ‘less is more’, and Walter Gropius founder of the bauhaus movement. 

Additionally, when provided analogy tasks, the model was able to pin an architect to his architectural era. My favorite, when given corbusier is to modernism, Peter Eisenman is to…, it provided, ‘avant-garde’ ‘post-functionalism’ ‘critique’ in addition to ‘postmodernism’. 

So, with that, I tried to query more ‘nebulous’ architectural concepts pulled from early EDA topic modelling, and curated by domain knowledge. 

Words  like ‘drawn’, ’drawing’, ’draw’. I wanted to see if it is possible to trace a shift over time in how the word was used. This plot show the use of the word ‘drawn’ per every 5000 words mapped over time, and below, their respective similarity results with relevent highlights.   Reading a conceptual shift in words like these proved to be a difficult task, as it may not be immediately clear that a shift is occurring without context behind the words,

 for example… in 1970 ‘theory’ yields a similarity to ‘western’ which could either relate to the ‘western world’ or the ‘western united states’, which during this period had a robust theoretical Project.. I chose to delineate a ‘settling’ effect here where it appears prior to 1980 architecture seemed fluid in its use of theory, whereas after the similarities settled into a constant. 

Finally, my favorite word ‘technology’ seems completely continuously shifting over all time periods I’ll just note the focus on universities in the 1990s where there were large technologically forward projects, and in 2010 with technology yielding a similarity to ‘artist’. . ultimately, I think in order to be more rigorous about this, that a different mode of visualization in which its clear to see a ‘spatial shift’ in the word vector is necessary, but to-date I haven’t devised a clear way to do so. 

Also, of course, in order for this to be more robust, more data is needed. Unfortunately, because the corpus had to be chopped into discrete time periods and fed into individual models by decade, I believe they may be suffering from a lack of data. 

So for future work, I believe this is a proof of concept that I could take to various architectural publications to request  access to their digital archives to feed into the model to make it more robust by decade. 

### **4. THE FILE ORGANIZATION**

The Alberti cleaner was a notebook that was used early in the project working with a much older architectural theory text. I was not happy with the results it gave me with early topic modelling, but it did provide some useful ways of thinking about architectural terminology that I used when selecting terms to map for the presentation. Basically, I needed to create stop words for words I knew had significant meaning in architectural texts, ie 'build' 'place' and 'nature'.. These sort of 'nebulous' terms became the focus of the word embeddings. I'm keeping it here, just to keep organized, and a screenshot of some of the LSA is included in the project folder... but the notebook is a mess, and likely will not run. I believe there is a section that I cut and never pasted, so a chunk of the work is missing.

P4-Preprocessor notebook is where the raw pdfs are fed in and processed, put in a dataframe and concated with the meta data for the documents for use in the P4-Modeling and P4-Visuals notebooks.

P4-Modeling notebook is where the modeling and all the results live. There are many more results than were used for the presentation due to the 4 minute time limitation. I believe I have some tsne vis in this file as well, which ended up being kind of useless for me. I'm still trying to wrap my head around multi-dimensional space being squashed into 2D

P4-Visuals notebook is a very simple notebook plotting the bar graphs used in the presentation. The bar graphs where further processed thru adobe illustrator, which I discovered can reliably alter the svg output files for this project, which was a bonus.

docs_meta_lookup.csv is the manually created spreadsheet of meta data, the excel version is also provided

master.csv is the docs_meta_lookup.csv concat with the actual document text spit out of the preprocessor.

