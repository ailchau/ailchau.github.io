---
layout: single
title: "Pickling in Python (a short introduction)"
---

I first learned about the pickle module in Python when I was working on my [first project](https://ailchau.github.io/project1-MTA/) at Metis. I found myself using the pickle module for every project and it has become an important part of my data science workflow. As I work on a project, I often use pickle to save important Python objects and data frames for future use. The pickle module is easy to learn and use.

## The Basics

The pickle module is a part of the Python standard library and is Python-specific. *Pickling* (or serializing) is the process of translating a Python data structure or object into a format that can be easily stored, in this case as byte streams (0s and 1s). The reverse process is called *unpickling* (or deserializing). What I find very useful about pickling is that it lets me save, reuse, or send Python objects. These objects, such as integers, strings, lists, tuples, dictionaries, functions, data frames, and trained machine learning models, can be pickled. For example, I have saved the resulting data frame after data cleaning and munging using pickle. This saved me time because I didn't need run the cleaning and munging code each time I began to work on my project. I have also pickled trained machine learning model, which I later unpickled to reuse to make predictions on new data.

```python
import pickle

# to save a Python object to a pickle file
pickle.dump(object, open("pickle_filename.pkl", "wb"))

# to load a pickle file
object = pickle.load(open("pickle_filename.pkl", "rb"))
```

"wb" and "rb" ensures that the pickle files are written and read in binary mode.

## Pickling Multiple Objects

There are times I need to save multiple objects, but I don't necessarily want to save and load multiple pickle files. One option is to combine the objects into a dictionary and then pickle the dictionary. Another is to combine the objects into a list or tuple.

```python
# to save multiple objects (as a list) to a pickle file
pickle.dump([object1, object2, object3], open("pickle_filename.pkl", "wb"))

# to load a pickle file
object1, object2, object3 = pickle.load(open("pickle_filename.pkl", "rb"))
```

#### *Note*
- If you are saving a trained machine learning model from scikit-learn, make sure that the version of scikit-learn and python match when pickling and unpickling.
- *Always* be cautious when unpickling files from untrusted sources because malicious code can be executed when loading. The pickle module cannot recognize malicious code.

For more information about the pickle module, check out the [documentation](https://docs.python.org/3/library/pickle.html#module-pickle).
