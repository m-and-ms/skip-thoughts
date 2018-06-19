# skip-thoughts

Simple implementation of skip-thought vectors ([Kiros et al., 2015](https://arxiv.org/abs/1506.06726)). This repository can be used to generate general-purpose sentence embeddings for numerous NLP tasks, and gives the means to obtain the data and train the model.

## Usage

This code is written for python 3.6. To download, clone this repository:
```bash
git clone https://github.com/danielwatson6/skip-thoughts.git
```

To obtain the training data, navigate to [https://www.smashwords.com/] and navigate the website to restrict the books to obtain to the desired categories (e.g. only free books of >=20,000 word length, of a certain genre, etc.). The resulting URL in the browser with the paginated list of books can be passed to this script to download all books in English that are available in text file format:
```bash
python smashwords.py [URL] [SAVE_DIRECTORY (defaults to ./books)]
# Example: python smashwords.py https://www.smashwords.com/books/category/1/newest/0/free/medium 
```

To clean the training data, there is a script provided that will overwrite all files in the input directory with their clean versions. In this context, cleaning means turning sentences into lines and only keeping alphanumeric characters, hyphens, apostrophes, and spaces. Note that `main.py` expects sentences to be lines. Usage:
```bash
python clean.py [TARGET_DIRECTORY]
```

We use Google's pre-trained 300-dimensional word vectors, which can be downloaded [here](https://drive.google.com/file/d/0B7XkCwpI5KDYNlNUTTlSS21pQmM/edit?usp=sharing) (this link just mirrors the download link of the [official website](https://code.google.com/archive/p/word2vec/)). The general model is of course independent of what word vectors are fed.

To train the model, change hyperparameters, or get sentence embeddings, see the help page of the main script:
```bash
python main.py --help
```

## Dependencies

All the dependencies are listed in the `requirements.txt` file. They can be installed with `pip` as follows:
```bash
pip install -r requirements.txt
```

