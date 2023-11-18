# find-exclusive-letter-word-combinations

Script to find all the words of a defined length containing single letters unique to each word.

This is to address the kind of challenge like described [in this post](https://stackoverflow.com/questions/71011062/find-5-letter-words-with-25-distinct-characters).

## Usage

This script was made with [ruby](https://ruby-lang.org), please adapt the way you run it depending on your platform (*nix or not).

The simplest usage is to run it by connecting STDIN with a list of words:

```shell
./felwc <words_alpha.txt
```

Use your own list of words or download [the one](https://github.com/dwyl/english-words/blob/master/words_alpha.txt) used above.

By default it will find all combinations of 5 words of length 5 having distinct letters.

## Extended usage

You may also ask the script to show all matching words that are composed by the same letter combination.
Example: `baker`, `brake`, `break` all are 5 letter words with the same letters.
Enabled by passing the `-s` option on the command line.

You may also ask the script to keep words (and show them in the results) with exceeding length but with
correct distinct letter counts.
Example for 5 letter: `aardvark` has 5 distinct letters but exceeds length to 8.
Enabled by passing the `-k` option on the command line.

You may also choose the word length to look for (defaults to 5):
Pass the length as the first non option argument on the command line.

You may also choose the number of words to match for a combination (defaults to 5):
Pass it as the second non option argument on the command line.

## Examples

Finding the default 5 words with 5 letters (distinct):

```shell
➜ ./felwc <words_alpha.txt
10175 words of length 5
5977 of these words with unique different letters
ambry fldxt pucks vejoz whing
ambry fldxt pungs vejoz whick
ampyx bejig fconv hdqrs klutz
ampyx bewig fconv hdqrs klutz
ampyx bortz chivw fjeld gunks
...
```

```shell
➜ ./felwc -s <words_alpha.txt
10175 words of length 5
5977 of these words with unique different letters
ambry,barmy fldxt pucks vejoz whing
ambry,barmy fldxt pungs,spung vejoz whick
ampyx bejig fconv hdqrs klutz
ampyx bewig fconv hdqrs klutz
ampyx bortz chivw fjeld gunks
...
```

```shell
➜ ./felwc -k <words_alpha.txt
36100 words of length 5
9878 of these words with unique different letters
aahing fldxt jumpy vrows zebeck
aardvark becobweb fultz jinxing symphysy
aardvark beeches fixity jowlop mzungu
aardvark beeches fultz immixing jowpy
aardvark beglew jumpy oxhoft zincs
...
```

Finding only 4 words with 4 letters (distinct):

```shell
➜ ./felwc 4 <words_alpha.txt
5549 words of length 4
3051 of these words with unique different letters
abed chil fogy jump
abed chil fogy junk
abed chil fogy junt
...
```

Finding 2 words of 10 letters:

```shell
➜ ./felwc 10 2 <words_alpha.txt
2626 words of length 10
2416 of these words with unique different letters
blacksmith gunpowdery
```

Finding 3 words of 8 letters (24 different letters) leading to no results:

```shell
➜ ./felwc 8 3 <words_alpha.txt
10428 words of length 8
8452 of these words with unique different letters
```

But when using longer words (keeping the same distinct letter count per word) it matches one result:

```shell
➜ ./felwc 8 3 -k <words_alpha.txt
70431 words of length 8
27644 of these words with unique different letters
brushproof jaywalked victimizing
```
