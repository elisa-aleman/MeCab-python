# MeCab Japanese parser usage example in Python

MeCab is a Japanese language parsing tool and as such, it is widely discussed and documented only in Japanese.
If you wish to parse Japanese texts but aren' confident reading the documentation, this example might be of use to you.

I am working in python3, but I have examples for python2 as well in this tutorial.
I am also working in MacOSX (I included Linux too) so installing methods might be different in your case.

## Install MeCab

### If you are on MacOSX:

From the terminal, using homebrew:

```
brew install mecab
brew install mecab-ipadic
```

### If you are on a debian-based Linux:

```
sudo apt-get install libmecab-dev
sudo apt-get install mecab mecab-ipadic-utf8
```

## Install Python wrapper

### Python 3:

Now there is already a library dedicated to wrap MeCab in python3 available in PiPy.
The original project, copyright and install files can be found at:

https://pypi.python.org/pypi/mecab-python3

Also available at GitHub at:

https://github.com/SamuraiT/mecab-python3

**Note: I do not claim any property over these projects, my code is only an example of usage **

Install with pip:
```
pip3 install mecab-python3
```
### Python 2:

In python2, the available wrapper is not on PiPy, so we download manually:

https://pypi.python.org/pypi/mecab-python/0.996

Download the file mecab-python-0.996.tar.gz to ~/

Terminal>>
```
pip2 install mecab-python-0.996.tar.gz
rm mecab-python-0.996.tar.gz
```

Then in Python:

```
import MeCab
# With MeCab original dictionary
# MeCab のデフォルト辞書で
mecab_tagger = MeCab.Tagger('')

text = 'これは日本語の形態素解析のテストです。動詞の形も一般化できるようになっています。'
parsed = [[chunk.split('\t')[0], tuple(chunk.split('\t')[1].split(','))] for chunk in mecab_tagger.parse(text).splitlines()[:-1]]
###
# the output layout is as follows:
# parsed --> [[surface, feature] for word in text]
# surface = 'surface'
# feature = ('part-of-speech, sub-class 1, sub-class 2, sub-class 3, inflection, conjugation, root-form, reading, pronunciation')
###
```

