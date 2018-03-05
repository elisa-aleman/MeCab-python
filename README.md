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

# >>> for i in parsed: print(i)
# ...
# ['これ', ('名詞', '代名詞', '一般', '*', '*', '*', 'これ', 'コレ', 'コレ')]
# ['は', ('助詞', '係助詞', '*', '*', '*', '*', 'は', 'ハ', 'ワ')]
# ['日本語', ('名詞', '一般', '*', '*', '*', '*', '日本語', 'ニホンゴ', 'ニホンゴ')]
# ['の', ('助詞', '連体化', '*', '*', '*', '*', 'の', 'ノ', 'ノ')]
# ['形態素', ('名詞', '一般', '*', '*', '*', '*', '形態素', 'ケイタイソ', 'ケイタイソ')]
# ['解析', ('名詞', 'サ変接続', '*', '*', '*', '*', '解析', 'カイセキ', 'カイセキ')]
# ['の', ('助詞', '連体化', '*', '*', '*', '*', 'の', 'ノ', 'ノ')]
# ['テスト', ('名詞', 'サ変接続', '*', '*', '*', '*', 'テスト', 'テスト', 'テスト')]
# ['です', ('助動詞', '*', '*', '*', '特殊・デス', '基本形', 'です', 'デス', 'デス')]
# ['。', ('記号', '句点', '*', '*', '*', '*', '。', '。', '。')]
# ['動詞', ('名詞', '一般', '*', '*', '*', '*', '動詞', 'ドウシ', 'ドーシ')]
# ['の', ('助詞', '連体化', '*', '*', '*', '*', 'の', 'ノ', 'ノ')]
# ['形', ('名詞', '一般', '*', '*', '*', '*', '形', 'カタチ', 'カタチ')]
# ['も', ('助詞', '係助詞', '*', '*', '*', '*', 'も', 'モ', 'モ')]
# ['一般', ('名詞', '一般', '*', '*', '*', '*', '一般', 'イッパン', 'イッパン')]
# ['化', ('名詞', '接尾', 'サ変接続', '*', '*', '*', '化', 'カ', 'カ')]
# ['できる', ('動詞', '自立', '*', '*', '一段', '基本形', 'できる', 'デキル', 'デキル')]
# ['よう', ('名詞', '非自立', '助動詞語幹', '*', '*', '*', 'よう', 'ヨウ', 'ヨー')]
# ['に', ('助詞', '格助詞', '一般', '*', '*', '*', 'に', 'ニ', 'ニ')]
# ['なっ', ('動詞', '自立', '*', '*', '五段・ラ行', '連用タ接続', 'なる', 'ナッ', 'ナッ')]
# ['て', ('助詞', '接続助詞', '*', '*', '*', '*', 'て', 'テ', 'テ')]
# ['い', ('動詞', '非自立', '*', '*', '一段', '連用形', 'いる', 'イ', 'イ')]
# ['ます', ('助動詞', '*', '*', '*', '特殊・マス', '基本形', 'ます', 'マス', 'マス')]
# ['。', ('記号', '句点', '*', '*', '*', '*', '。', '。', '。')]
```
