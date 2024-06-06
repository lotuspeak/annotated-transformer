Code for The Annotated Transformer blog post:

http://nlp.seas.harvard.edu/annotated-transformer/

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/harvardnlp/annotated-transformer/blob/master/AnnotatedTransformer.ipynb)

![image](https://user-images.githubusercontent.com/35882/166251887-9da909a9-660b-45a9-ae72-0aae89fb38d4.png)




# Package Dependencies

Use `requirements.txt` to install library dependencies with pip:

```
conda create --name annotated-transformer python=3.9 -y
conda activate annotated-transformer
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
```


# Notebook Setup

The Annotated Transformer is created using [jupytext](https://github.com/mwouts/jupytext).

Regular notebooks pose problems for source control - cell outputs end up in the repo history and diffs between commits are difficult to examine. Using jupytext, there is a python script (`.py` file) that is automatically kept in sync with the notebook file by the jupytext plugin.

The python script is committed contains all the cell content and can be used to generate the notebook file. The python script is a regular python source file, markdown sections are included using a standard comment convention, and outputs are not saved. The notebook itself is treated as a build artifact and is not commited to the git repository.

Prior to using this repo, make sure jupytext is installed by following the [installation instructions here](https://github.com/mwouts/jupytext/blob/main/docs/install.md).

To produce the `.ipynb` notebook file using the markdown source, run (under the hood, the `notebook` build target simply runs `jupytext --to ipynb the_annotated_transformer.py`):

```
make notebook
```

To produce the html version of the notebook, run:

```
make html
```

`make html` is just a shortcut for for generating the notebook with `jupytext --to ipynb the_annotated_transformer.py` followed by using the jupyter nbconvert command to produce html using `jupyter nbconvert --to html the_annotated_transformer.ipynb`                             
 

# Formatting and Linting

To keep the code formatting clean, the annotated transformer git repo has a git action to check that the code conforms to [PEP8 coding standards](https://www.python.org/dev/peps/pep-0008/).

To make this easier, there are two `Makefile` build targets to run automatic code formatting with black and flake8.

Be sure to [install black](https://github.com/psf/black#installation) and [flake8](https://flake8.pycqa.org/en/latest/).

You can then run:

```
make black
```

(or alternatively manually call black `black --line-length 79 the_annotated_transformer.py`) to format code automatically using black and:

```
make flake
```

(or manually call flake8 `flake8 --show-source the_annotated_transformer.py) to check for PEP8 violations.

It's recommended to run these two commands and fix any flake8 errors that arise, when submitting a PR, otherwise the github actions CI will report an error.

# mark
## 1 python -m pip install 'spacy~=3.2.6'

## 2  multi30k url changed
Plus, besides commenting the previous URL, you also need to change the MD5 in torchtext/datasets/multi30k.py （pkg: torchtext）.

    # URL = {
    #     'train': r'http://www.quest.dcs.shef.ac.uk/wmt16_files_mmt/training.tar.gz',
    #     'valid': r'http://www.quest.dcs.shef.ac.uk/wmt16_files_mmt/validation.tar.gz',
    #     'test': r'http://www.quest.dcs.shef.ac.uk/wmt16_files_mmt/mmt16_task1_test.tar.gz',
    # }
    # 
    # MD5 = {
    #     'train': '20140d013d05dd9a72dfde46478663ba05737ce983f478f960c1123c6671be5e',
    #     'valid': 'a7aa20e9ebd5ba5adce7909498b94410996040857154dab029851af3a866da8c',
    #     'test': '0681be16a532912288a91ddd573594fbdd57c0fbb81486eff7c55247e35326c2',
    # }

    URL = {
        "train": r"https://raw.githubusercontent.com/neychev/small_DL_repo/master/datasets/Multi30k/training.tar.gz",
        "valid": r"https://raw.githubusercontent.com/neychev/small_DL_repo/master/datasets/Multi30k/validation.tar.gz",
        "test": r"https://raw.githubusercontent.com/neychev/small_DL_repo/master/datasets/Multi30k/mmt16_task1_test.tar.gz",
    }

    MD5 = {
        "train": "20140d013d05dd9a72dfde46478663ba05737ce983f478f960c1123c6671be5e",
        "valid": "a7aa20e9ebd5ba5adce7909498b94410996040857154dab029851af3a866da8c",
        "test": "6d1ca1dba99e2c5dd54cae1226ff11c2551e6ce63527ebb072a1f70f72a5cd36",
    }

    可直接下载文件到 ~/.torchtext/cache/Multi30K/

## 3 下载 en/de_core_web/news_sm
https://github.com/explosion/spacy-models/releases?page=50
  280  pip install en_core_web_sm-3.2.0.tar.gz 
  281  pip install de_core_news_sm-3.2.0
  282  pip install de_core_news_sm-3.2.0.tar.gz s