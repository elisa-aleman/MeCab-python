# MeCab Japanese parser usage in python

MeCab is a Japanese language parsing tool and as such, it is widely discussed and documented only in Japanese.
If you wish to parse Japanese texts but aren' confident reading the documentation, this example might be of use to you.

I am working in python3, but I have examples for python2 as well in this tutorial.
I am also working in MacOSX so installing methods might be different in your case.

## Install MeCab (Japanese segmentation)

First, install MeCab on Mac

Terminal>>
http_proxy=http://proxy.nagaokaut.ac.jp:8080 https_proxy=http://proxy.nagaokaut.ac.jp:8080 brew install mecab
http_proxy=http://proxy.nagaokaut.ac.jp:8080 https_proxy=http://proxy.nagaokaut.ac.jp:8080 brew install mecab-ipadic
<<

Python 2:

Then, download a python binder so you can use it in python
https://pypi.python.org/pypi/mecab-python/0.996
Download the file mecab-python-0.996.tar.gz to ~/

Terminal>>
pip2 install mecab-python-0.996.tar.gz
rm mecab-python-0.996.tar.gz
<<

Python 3:
Terminal>>
pip3 install mecab-python3
<<

Then in Python<<
import MeCab
>>
