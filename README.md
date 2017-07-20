# Fancy Nouns
#### Inspired by _Gödel, Escher, Bach: An Eternal Golden Braid_ by Douglas Hofstadter
A lua program that generates **Fancy Nouns.**  
 
**Fancy Nouns** are nouns that have been embellished with arbitrarily many descriptors and qualifiers.

If you don't have lua installed, `$ sudo apt install lua5.2` will do the trick.  

Once lua is installed, run `$ lua main.lua <num_of_fancy_nouns>` to generate as many fancy nouns as you want.
**Be careful**, as the code is not currently optimized and will throw an exception if its first argument is not an int.

## Info about Fancy Nouns
Hofstadter explains that **Fancy Nouns** can be generated by following flowchart-like decision trees called "recursive transition networks." This program brings his RTNs from the theoretical space into reality. I followed the RTNs from his book almost precisely:

![alt text][RTN]

The point of the RTN is that every grammatically correct **Fancy Noun** in English can be generated by way of this framework. However, Hofstadter does not claim, nor is it true, that every possible **Fancy Noun** generated will be useful or even make sense. What the RTN _can_ do is generate _well-formed_ strings of English words. This means that all the parts of speech will be arranged correctly. The fact that a **Fancy Noun** generated by this program might be completely unintelligible has nothing to do with the validity of the RTN with respect to English grammar; rather, the failure to generate a meaningful string of English words is due to the fact that some English words have meanings which conflict. Noam Chomsky's classic example is "Colorless green ideas sleep furiously." All the words are in the right place: Adjective, Adjective, Subject, Intransitive Verb, Adverb. It is the semantic meanings of the words that are incompatible, not their grammar.

So, the fact that this program rarely makes any sense is not a failure on the part of the programmer. It was never my intention to add intelligence or consideration of the meanings of words. This program was an exercize in bringing the RTN model for constructing English phrases to life. 

## Caveats and Known Issues
The RTN model prevents any sort of intelligent interplay between words in the **Fancy Noun** it generates. That is, each word is self-contained and knows nothing of the words preceding or following it in the phrase. As such, there are a few inherent problems that I have no intention of trying to fix, as well as some other items of interest.

* You will notice that the article _an_ is never used. _The_ and _a_ are used in equal proportion, but never _an_. This is because knowing whether to pick _a_ or _an_ would require knowledge of the word directly following the article. If it were only ever a noun this would be ok, but any number of adjectives could stand between the article and its noun. So, knowing the first letter of the word directly following an article would be challenging and break from the spirit of the RTN, where each part of the sentence is meant to be its own self-contained subroutine. In addition, I think the frequent occurence of incorrect phrasings such as "a educated bean" adds to the silliness.

* Some adjectives, verbs, and nouns look the same. For example, _rough_ is both an adjective and a noun, according to the list of nouns I used for this project. Also, many adjectives are past participles, which makes them look like verbs (e.g. _discredited_, _spotted_). If you think the RTN didn't work, youre probably just reading the phrase wrong.

* Hofstadter's RTN includes two paths for **Ornate Noun** that skip the article. As far as I could tell, this is only accurate in English if the noun ends up being plural or a proper noun. Since I didn't want the generated text to be TOO unintelligible, I left out the case where articles get skipped.

* The list of verbs that I found had them all in the first person present tense (i.e. _drip_, _cry_, _agree_). However, in relative clauses, we only use them in the past tense (_dripped_, _cried_, _agreed_) and the third person present tense (_drips_, _cries_, _agrees_). Due to the sheer number of verbs in the list, I had to write a script to convert them all by adding _ed_ and _s_ to the ends of the verbs. This created problems for some words, like _driped_, _cryed_, and _agreeed_ in the past tense. I believe I've corrected most of the irregularities, but I'm sure there are more in there somewhere. Please report them to me as you find them and I'll fix them. 

* As mentioned above, the program also has the purely technical downfall that causes it to throw an exception when its first argument isn't an integer. Please give it an integer.

I'll probably keep tweaking the probabilities so that the **Fancy Nouns** are more interesting. If you find any other problems, let me know.

[RTN]: https://68.media.tumblr.com/e6ce39e7973ca5cdc0523bd771b6e8a8/tumblr_inline_mtrfoq9vzi1rhp7q3.jpg "Fancy Noun RTN"
