#  Natural Language Processing on Financial Statements

## Project Description: 

##### NLP Analysis on 10-k financial statements to generate an alpha factor. For the dataset, we'll be using the end of day from Quotemedia and Loughran-McDonald sentiment word lists.

###### *Important Notes*: 

## 10-Ks (Steps)

* The function get_documents extracts the documents from the text.

* Alternative implementation:

* return extracted_docs = re.compile('<DOCUMENT>(.*?)</DOCUMENT>', re.DOTALL | re.IGNORECASE).findall(text)

* The function get_document_type returns the document type lowercased.

* Similar implementation:

```py
return re.findall("<TYPE>(.*?)\n", doc)[0].lower()
```

## Preprocess the Data

* The function lemmatize_words lemmatizes verbs.

- Similar implementation: but thought you should know you can write in this way also.
   
```py
wordnet_lemmatizer = WordNetLemmatizer()
return [wordnet_lemmatizer.lemmatize(word, pos=wordnet.VERB) for word in words]
```

## Analysis on 10ks

* The function get_bag_of_words generates a bag of words from documents.

* Just 2 Line Implementation :heart:

* Alternative Implementation : Using Lambda Function

```py
return np.array([sentiment_words.apply(lambda x: int(x in doc)) for doc in docs])
````

* The function get_jaccard_similarity calculates the jaccard similarities for neighboring documents.

* Alternative Implementation:

```py
return [jaccard_similarity_score(bag_of_words_matrix[i]>0,bag_of_words_matrix[i+1]>0) \
        for i in range(len(bag_of_words_matrix)-1)]
```

* The function tfidf generate TFIDF vectors for each document.

* The function get_cosine_similarity calculates the cosine similarities for each neighboring TFIDF vector/document.

* Alternative Implementation:

```py
    return [float(cosine_similarity(tfidf_matrix[i, :].reshape(1, -1), tfidf_matrix[i + 1, :].reshape(1, -1)))
            for i in range(tfidf_matrix.shape[0] - 1)]
```