=========================
 Google ngram downloader
=========================

.. image:: https://travis-ci.org/dimazest/google-ngram-downloader.png?branch=master
    :target: https://travis-ci.org/dimazest/google-ngram-downloader

.. image:: https://coveralls.io/repos/dimazest/google-ngram-downloader/badge.png?branch=master
    :target: https://coveralls.io/r/dimazest/google-ngram-downloader?branch=master

`The Google Books Ngram Viewer dataset`__ is a freely available resource under
a `Creative Commons Attribution 3.0 Unported License`__ which provides ngram
counts over books scanned by Google.

__ http://storage.googleapis.com/books/ngrams/books/datasetsv2.html
__ http://creativecommons.org/licenses/by/3.0/

The data is so big, that storing it is almost impossible. However, sometimes
you need an aggregate data over the dataset. For example to build a
co-occurrence matrix.

This package provides an iterator over the dataset stored at Google. It
decompresses the data on the fly and provides you the access to the underlying
data.


Example use
===========

>>> from google_ngram_downloader import readline_google_store
>>>
>>> fname, url, records = next(readline_google_store(ngram_len=5))
>>> fname
'googlebooks-eng-all-5gram-20120701-0.gz'
>>> url
'http://storage.googleapis.com/books/ngrams/books/googlebooks-eng-all-5gram-20120701-0.gz'
>>> next(records)
Record(ngram='0 " A most useful', year=1860, match_count=1, volume_count=1)


Installation
============

::

    pip intall google-ngram-downloader


The command line tool
=====================

It also provides a simple command line tool to download the ngrams::

    $ google-ngram-downloader -h
    google-ngram-downloader [OPTIONS] [NGRAM_LEN]

    Download The Google Books Ngram Viewer dataset version 20120701.

    options:

     -n --ngram-len  The length of ngrams to be downloaded. (default: 1)
     -o --output     The destination folder for downloaded files. (default:
                     downloads/google_ngrams/{ngram_len})
     -v --verbose    Be verbose.
     -h --help       display help


