---
date: 2022-04-04T12:00:0+01:00
description: "Introduction to Cryptography Through Anecdotes"
tags: ["cipher","cryptography","history"]
title: "Il était une fois TLS"
---

# Introduction

Development debates are common, especially when it comes to topics such as security.
While working on setting up a secure communication,
we started a discussion about the configuration of an encryption key.
Our insatiable technical curiosity being at least as important as our thirst for debate,
I decided to start exploring these concepts.
Little did I know that a whole world would open up before me.

I propose to you to take a time machine to discover cryptography, the art of making a message secret, through history.
Along the way, we will observe the underlying concepts,
we will play with these mechanisms through historical anecdotes,
and we will see its evolution until today.

Please, come, the journey begins.

# Time Travel

## Temporal Shipping Preparation

We are about to travel through time to understand the origins of cryptography.
Like any journey, we have to prepare ourselves, here is a small glossary to get out of tricky situations:

Cryptography refers to *encryption* which is the process to make a normal message (plaintext) unintelligible (ciphertext).
To go back to the normal message, you have to *decrypt* it.
An *algorithm* and a *key* are used to encrypt and decrypt the message.

To make a message secret, we can :
* make a substitution by character, this is *encryption* (e.g. replace with the next letter in the alphabet).
* make a substitution by word/logical chunk, it is the *coding* (e.g. translate in another language)
* concealing one's own existence, this is called *steganography* (e.g. [invisible ink](https://fr.wikipedia.org/wiki/Encre_invisible))

Thereafter, we will talk about encryption and encrypted message for the sake of simplicity.

Now we have a bit of preparation, let's go on the path of history.

## The Secrets of Ancient Egypt

We are 4000 years ago in the Egyptian town of MENET KHUFU,
in the tomb of the nobleman [KHNUMHOTEP II](https://en.wikipedia.org/wiki/Khnumhotep_II).
Take a look at those unusual hieroglyphic inscriptions, have you had some difficulties reading them?
It's OK, it is probably because it contains unusual hieroglyphs. 😉
Ones consider that it is a way to confuse an unexpected reader.

// add image of wall or hieroglyphs

Using an unusual symbol, or switching it, is a basic and simple way to **encrypt** a message.
You look doubtful and you are right.
This example is controversial because these specificities could be due to the context,
like our legal vocabulary that uses sometimes uncommon words,
a stylistic effect or the evolution of the language itself.

In any case, a tomb is not the best place to discuss, let's go to our next time step.

# The Most Spartan Encryption

We've done a big jump, we are in Greece 3rd century BCE,
we are searching for [Apollonius of Rhodes](https://en.wikipedia.org/wiki/Apollonius_of_Rhodes).
I would love to ask him about the famous [Argonautica](https://en.wikipedia.org/wiki/Argonautica),
but we are here for cryptography.
No one at the meeting point, instead we have a weird cylinder with a strip of parchment.

// add image / illustration

You may have guessed, that cylinder is a [scytale](https://en.wikipedia.org/wiki/Scytale)
( Ancient Greek: σκυτάλη skutálē "baton, cylinder", also σκύταλον skútalon).
In cryptography terminology, the scytale is the **key** to encrypt and decrypt the message.

As the system is pretty simple to crack,
another interpretation is that this mechanism is more for **authentication** than ***encryption***.
Both communicants must have the same cylinder characteristics to write and read the message,
so the receiver is waiting for a specific ciphered message size,
and an interceptor will not be able to corrupt easily the content.

Let's play with it to fully understand the concept.
I want to send you a message, in plaintext: "This is my first encrypted message".
But it is a secret message! So, I need to encrypt it.
We exchange the type of Scytale we want to use (physical characteristics).
I take a Scytale (the key) and I wrap the strip of parchment around, then I write the message:

// Need help to format the following table 😛

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 
|-----|-----|-----|-----|-----|-----|-----|-----|
| T   | h   | i   | s   | i   | s   | m   | y   |  
| f   | i   | r   | s   | t   | e   | n   | c   |  
| r   | y   | p   | t   | e   | d   | m   | e   |  
| s   | s   | a   | g   | e   |     |     |     | 

Then I unwrap the parchment and obtain the encrypted message: "Tfrshiysirpasstgiteesedmnmyce".
The least we can say is that this message has lost its clarity, hasn't it?

To decrypt this message, you take your scytale with the predefined physical characteristics (the key),
and wrap the parchment around it, and Tadaaaa, you can read the original plaintext message.
As the same key is used both for encrypting and decrypting, it is called a [symmetric key algorithm](https://en.wikipedia.org/wiki/Symmetric-key_algorithm). 

Excellent! We discovered and used a first encryption mechanism!
Of course, it was a first naive approach that could be improved, for example,
by adding unexpected characters or using a complex scytale form.

This logical group permutation algorithm is called [transposition cipher](https://en.wikipedia.org/wiki/Transposition_cipher).

One moment, I can hear the sound of a clash...
Indeed, this technique was commonly used by the Spartans during military campaigns,
I think it would be more prudent to leave right away.

## Encrypted Babylon

We are around 200 BCE, near Jerusalem, and we are searching for the [Book of Jeremiah](https://en.wikipedia.org/wiki/Book_of_Jeremiah).
Why do so? This text contains Hebrew words that have been encrypted using a method called [Atbash](https://en.wikipedia.org/wiki/Atbash)
(Hebrew: אתבש; also transliterated Atbaš). **Atbash** derives from the first two letters **Aleph** and **Taw**, and the last two letters **Bet** and **Shin** in the Hebrew alphabet.

This encryption consists of replacing each character with the same position in the reversed alphabet.


| Position  |   0   |  1   |   2   |   3    |   4   |  5  |   6   |   7    |  8  |  9   |  10   |  11   |  12  | 13  |   14   |  15   | 16  |  17   |   18   |  19   |  20  |  21   |
|:---------:|:-----:|:----:|:-----:|:------:|:-----:|:---:|:-----:|:------:|:---:|:----:|:-----:|:-----:|:----:|:---:|:------:|:-----:|:---:|:-----:|:------:|:-----:|:----:|:-----:|
|           | Aleph | Bet  | Gimel | Daleth |  Heh  | Vav | Zayin |  Het   | Tet | Yodh | Kaph  | Lamed | Mem  | Nun | Samech | Ayin  | Peh | Tzady |  Koof  | Reish | Shin |  Taw  |
| Plaintext |   א   |  ב   |   ג   |   ד    |   ה   |  ו  |   ז   |   ח    |  ט  |  י   |   כ   |   ל   |  מ   |  נ  |   ס    |   ע   |  פ  |   צ   |   ק    |   ר   |  ש   |   ת   |
|           |  Taw  | Shin | Reish |  Koof  | Tzady | Peh | Ayin  | Samech | Nun | Mem  | Lamed | Kaph  | Yodh | Tet |  Het   | Zayin | Vav |  Heh  | Daleth | Gimel | Bet  | Aleph |
| Ciphered  |   ת   |  ש   |   ר   |   ק    |   צ   |  פ  |   ע   |   ס    |  נ  |  מ   |   ל   |   כ   |  י   |  ט  |   ח    |   ז   |  ו  |   ה   |   ד    |   ג   |  ב   |   א   |


As each letter is replaced by another, this cipher is a mono-alphabetic [substitution cipher](https://en.wikipedia.org/wiki/Substitution_cipher).
As the same key is used both for encrypting and decrypting, it is called [symmetric key algorithm](https://en.wikipedia.org/wiki/Symmetric-key_algorithm).

One well-known example is in [Jeremiah 25:26](https://en.wikipedia.org/wiki/Jeremiah_25#Verse_26) –
"The king of Sheshach shall drink after them" – Sheshach meaning Babylon in Atbash (בבל bbl → ששך ššk).

Theologically speaking, Babylon is the city where the original unique human language was separated and thus the original meaning was lost.
Don't you see a form of irony in the context of the origin of cryptography?

We can perfectly transpose this mechanism to our Roman alphabet...
Hey, if you want to play with Latin characters, how about going to ancient Rome? Let's go!

## 	YHQL YHGL YLFL

We are in the last century BCE during Julius Caesar's reign.
The [first triumvirate](https://en.wikipedia.org/wiki/First_Triumvirate) was difficult to create and the political life of Julius Caesar is very eventful, with frequent reversals.
In this particular context, he got into the habit of encrypting his correspondence,
and one even ended up giving his name to an encryption technique: [Caesar's cipher](https://en.wikipedia.org/wiki/Caesar_cipher)

This method consists in replacing each letter of plaintext by a letter some fixed number of positions down the alphabet.
This type of method is called a [substitution cipher](https://en.wikipedia.org/wiki/Substitution_cipher).
The shift parameter is the encryption **key**.

Let's start from our alphabet with a right shift of 3:

| position  | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  | 21  | 22  | 23  | 24  | 25  |
|-----------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| plaintext | a   | b   | c   | d   | e   | f   | g   | h   | i   | j   | k   | l   | m   | n   | o   | p   | q   | r   | s   | t   | u   | v   | w   | x   | y   | z   |
| ciphered  | d   | e   | f   | g   | h   | i   | j   | k   | l   | m   | n   | o   | p   | q   | r   | s   | t   | u   | v   | w   | x   | y   | z   | a   | b   | c   |

So the 'd' is replaced by 'a' which is the letter three position before, and so on.
But what about the 'a' that becomes 'x'?
The alphabet must be read like a clock: 2 hours before 1 am it is 11 pm, in the same way, 'x' is three letters before 'a'.
This mechanism of restarting from the beginning is a fundamental mathematics concept in cryptography,
and it is called [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic).
Like the previous technique, the same key is used to encrypt and decrypt,
so it is also a [symmetric key algorithm](https://en.wikipedia.org/wiki/Symmetric-key_algorithm).

Before we go any further, it seems that the title of our section has been "inadvertently" encrypted, can you decrypt it?
A rumor runs, it would be a famous phrase of Julius Caesar.

// Answer presentation could be improved
<details>
<summary>Answer</summary>
    
    YHQL YHGL YLFL
    VENI VEDI VICI
    
</details>

Congrats! We added the substitution cipher to our toolbox.
This type of algorithm has been evolving throughout history, let's look for next time step.

## The 44th Art of the Kama Sutra

Our time machine seems a little confused about the period, we are between 0 and 400 CE, probably around 200 CE.
We are in [Pataliputra](https://en.wikipedia.org/wiki/Pataliputra), in India,
in the footsteps of the brahmin [Vātsyāyana](https://en.wikipedia.org/wiki/V%C4%81tsy%C4%81yana).
that writes the first version of the [Kama Sutra](https://en.wikipedia.org/wiki/Kama_Sutra)
(Sanskrit: कामसूत्र , Kāma-sūtra; "Principles of Love").

At the risk of disappointing you, and contrary to popular belief, the Kama Sutra is not a collection of sexual positions,
but rather a guide on how to be and how to live a fulfilling love relationship.

Among the 64 art listed in the Kama Sutra, we are interested in the 44th:
[Mlecchita Vikalpa](https://en.wikipedia.org/wiki/Mlecchita_vikalpa).
This is "the art of secret writing and secret communications".

The initial text does not provide a specific method, however, the text evolves through commentaries.
[Jayamangala](https://en.wikipedia.org/wiki/Jayamangala) commentary proposes the **Kautilya** and **Muladeviya** methods,
they are basically **substitution ciphers** based on phonetic relations.

Nowadays, what is commonly called the Kama Sutra cipher consists of defining a couple of letters to switch each other.
For example,
our alphabet can be divided into 13 pairs of characters and each letter in plaintext will be replaced by the coupled letter.


| pairs     |     |     |     |     |     |     |     |     |     |     |     |     |     |
|-----------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| plaintext | a/z | e/r | t/y | u/i | o/p | q/s | d/f | g/h | j/k | l/m | w/x | c/v | b/n |
| ciphered  | z/a | r/e | y/t | i/u | p/o | s/q | f/d | h/g | k/j | m/l | x/w | v/c | n/b |

With this substitution table, "love" becomes "mpcr".

You may have guessed, the same key is used both for encrypting and decrypting,
it is a [symmetric key algorithm](https://en.wikipedia.org/wiki/Symmetric-key_algorithm).
There is a lot of other time step talking about this kind of cipher, however, I would like to talk about another thing.

## Tales of 1001 Ciphers

Encrypted messages are an awesome way to have secured communications,
but what happens each time we try to secure something?
Yes, one is going to find a workaround or crack the security,
here comes the [cryptanalysis](https://en.wikipedia.org/wiki/Cryptanalysis) (from the Greek kryptós, "hidden", and analýein, "to analyze").
Thanks to cryptanalysis, an encrypted message could be decrypted even without the encryption key.

We are in the 9th century CE, near Bagdad (check), and we are searching for the [Al-Kindi](https://en.wikipedia.org/wiki/Al-Kindi) work.
He is considered one of the fathers of cryptography and among others,
a famous scientist who works on cryptanalysis and more specifically on [frequency analysis](https://en.wikipedia.org/wiki/Frequency_analysis).

The study of the Coran uses the premises of the frequency analysis,
indeed the fragmentary nature of the Coran generated a specific theological branch that checks the text.
The method consists of checking the frequency of the words and comparing them to complete text from different periods.
So, we may attribute a text to a specific period thanks to the word frequency.

In the case of an encrypted message, if the cipher method keeps the position of the characters,
we may infer which original character it is thanks to the frequency of this character in a text from the same period and the same language.
If you have a long enough text, you sort all characters by their frequency then you do the same with the encrypted text,
the chances are that those lists will match.

To be honest, it is not as simple, you have to check the most frequent letter and not a one-to-one match.
Then you can rely on the language structure, the number of characters, and the position in the word

Let's try it out!

From [Letter frequency](https://en.wikipedia.org/wiki/Letter_frequency) wiki article, the frequency for English letter is:

|      |      |      |      |     |      |     |      |     |       |       |     |      |      |      |      |        |     |      |      |      |       |      |       |     |        | 
|------|------|------|------|-----|------|-----|------|-----|-------|-------|-----|------|------|------|------|--------|-----|------|------|------|-------|------|-------|-----|--------|
| a    | b    | c    | d    | e   | f    | g   | h    | i   | j     | k     | l   | m    | n    | o    | p    | q      | r   | s    | t    | u    | v     | w    | x     | y   | z      |
| 8.2% | 1.5% | 2.8% | 4.3% | 13% | 2.2% | 2%  | 6.1% | 7%  | 0.15% | 0.77% | 4%  | 2.4% | 6.7% | 7.5% | 1.9% | 0.095% | 6%  | 6.3% | 9.1% | 2.8% | 0.98% | 2.4% | 0.15% | 2%  | 0.074% |

Let's try frequency analysis on a ciphered text:

```Jbhyq lbh or noyr gb qrpvcure guvf grkg jvgubhg univat gur rapelcgvba xrl? Ubjrire, gb or rssvpvrag, gur grkg arrqf gb or ybat rabhtu gb graq gb na nirentr qvfgevohgvba bs gur punenpgref. Vs vg vf abg gur pnfr, bgure punenpgrevfgvpf znl or hfrq fhpu nf gur svefg yrggre serdhrapl be gur hfhny cbfvgvba bs ibjryf naq pbafbanagf.```

|                   |           |           |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |         |
|-------------------|-----------|-----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|---------|
| text frequency    | r: 14.02% | g: 12.88% | b: 8.71% | v: 6.82% | a: 6.44% | f: 6.44% | u: 6.06% | n: 5.68% | e: 5.30% | p: 4.55% | h: 3.79% | q: 2.65% | s: 2.65% | y: 2.27% | o: 2.27% | l: 1.89% | t: 1.52% | i: 1.52% | j: 1.52% | c: 1.14% | k: 0.76% | z: 0.38% | d: 0.38% | x: 0.38% | -        | -       |
| english frequency | e: 13.00% | t: 9.10%  | a: 8.20% | o: 7.50% | i: 7.00% | n: 6.70% | s: 6.30% | h: 6.10% | r: 6.00% | d: 4.30% | l: 4.00% | c: 2.80% | u: 2.80% | w: 2.40% | m: 2.40% | f: 2.20% | y: 2.00% | g: 2.00% | p: 1.90% | b: 1.50% | v: 0.98% | k: 0.77% | j: 0.15% | x: 0.15% | q: 0.10% | z: 0.07% |

Starting from the frequency, we can replace the characters following the order of the previous table and switch to the nearest letter if it does not match.
There are several technics, we can [brute force search](https://en.wikipedia.org/wiki/Brute-force_search) all combinations and choose the right one.
We can check step by step and detect common words like "to", "and" or impossible.
We will start by replacing 'r' with 'e', 'g' with 't', and 'b' with 'a':

>  .a... .a. .e ...e ta .e....e. t... te.t ..t.a.t ...... t.e e.....t.a. .e.? .a.e.e., ta .e e.....e.t, t.e te.t .ee.. ta .e .a.. e.a... ta te.. ta .. ..e...e ...t....t.a. a. t.e ......te... .. .t .. .at t.e ...e, at.e. ......te...t... ... .e ..e. .... .. t.e ....t .ette. ..e..e... a. t.e ..... .a..t.a. a. .a.e.. ... .a..a...t..

```ta``` does not exist, let's try to replace 'b' with 'o'

> .o... .o. .e ...e to .e....e. t... te.t ..t.o.t ...... t.e e.....t.o. .e.? .o.e.e., to .e e.....e.t, t.e te.t .ee.. to .e .o.. e.o... to te.. to .. ..e...e ...t....t.o. o. t.e ......te... .. .t .. .ot t.e ...e, ot.e. ......te...t... ... .e ..e. .... .. t.e ....t .ette. ..e..e... o. t.e ..... .o..t.o. o. .o.e.. ... .o..o...t..

From there, we can try to infer some replacement as a cruciverbalist.

`to *e` may be `to be`, so 'o' becomes 'b'. And 't*e' could be 'the', so 'u' becomes 'h'.
Let's try again:

> .o... .o. be .b.e to .e...he. th.. te.t ..tho.t h..... the e.....t.o. .e.? .o.e.e., to be e.....e.t, the te.t .ee.. to be .o.. e.o..h to te.. to .. ..e...e ...t..b.t.o. o. the .h....te... .. .t .. .ot the ...e, othe. .h....te...t... ... be ..e. ...h .. the ....t .ette. ..e..e... o. the ..... .o..t.o. o. .o.e.. ... .o..o...t..

With some other tricks and guesses, we obtain this message with the associated table:

> Would you be able to decipher this text without having the encryption key? However, to be efficient, the text needs to be long enough to tend to an average distribution of the characters. If it is not the case, other characteristics may be used such as the first letter frequency or the usual position of vowels and consonants.

|                   |           |           |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |          |
|-------------------|-----------|-----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|----------|
| text frequency    | r: 14.02% | g: 12.88% | n: 5.68% | b: 8.71% | v: 6.82% | a: 6.44% | f: 6.44% | u: 6.06% | e: 5.30% | q: 2.65% | y: 2.27% | p: 4.55% | h: 3.79% | j: 1.52% | z: 0.38% | s: 2.65% | l: 1.89% | t: 1.52% | c: 1.14% | o: 2.27% | i: 1.52% | x: 0.38% | -        | k: 0.76% | d: 0.38% | -        |
| english frequency | e: 13.00% | t: 9.10%  | a: 8.20% | o: 7.50% | i: 7.00% | n: 6.70% | s: 6.30% | h: 6.10% | r: 6.00% | d: 4.30% | l: 4.00% | c: 2.80% | u: 2.80% | w: 2.40% | m: 2.40% | f: 2.20% | y: 2.00% | g: 2.00% | p: 1.90% | b: 1.50% | v: 0.98% | k: 0.77% | j: 0.15% | x: 0.15% | q: 0.10% | z: 0.07% |

TThe method is not perfect however the longer the text, the more likely the frequency is close to the average frequency.
We are not so far away in this example.

We found the original message, but can we find the key? If we sort the letters alphabetically, we get:

| Position  | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  | 12  | 13  | 14  | 15  | 16  | 17  | 18  | 19  | 20  | 21  | 22  | 23  | 24  | 25  |
|-----------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| plaintext | a   | b   | c   | d   | e   | f   | g   | h   | i   | j   | k   | l   | m   | n   | o   | p   | q   | r   | s   | t   | u   | v   | w   | x   | y   | z   |
| ciphered  | n   | o   | p   | q   | r   | s   | t   | u   | v   | w   | x   | y   | z   | a   | b   | c   | d   | e   | f   | g   | h   | i   | j   | k   | l   | m   |


It is a Caesar code with a shift of 13.
This method gave us the plaintext message and the key!

Ok, we have a new powerful tool that can break encrypted messages with mono-alphabetic substitution.
For our next time step, we will look for a way to counter the frequency analysis.

## Cipher Disk

We are in Italy in the middle of the fifteen century.
Look at this ingenious system, it is an encryption disk created by [Leon Battista Alberti](https://en.wikipedia.org/wiki/Leon_Battista_Alberti).

// add cipher disk image https://upload.wikimedia.org/wikipedia/commons/b/b5/CipherDisk2000.jpg

This disk is a substitution cipher tool that can be used either by leaving the mobile part in the same position (mono-alphabetic cipher),
or by periodically moving the mobile part ([poly-alphabetic cipher](https://en.wikipedia.org/wiki/Polyalphabetic_cipher)).

Poly-alphabetic encryption uses several symbols to replace the initial symbol.
If the position of the character is used to change the cipher character,
not only a cipher letter replaces several characters,
but the frequency of an original character is no longer simply determinable.
That's why the frequency analysis loses a lot of its efficiency.

Let's try to find the evolution of this kind of cipher to play with it.

## The letter that betrayed her

We are in London at the end of the sixteenth century, Mary former queen of Scotland is sentenced to death.
But what has happened?
Mary is guilty of high treason, she plotted against Queen Elizabeth of England.
The evidence consists of coded letters exchanged with a group of Catholic aristocrats.
They were led by Anthony Babington who gave his name to the case: [Babington Plot](https://en.wikipedia.org/wiki/Babington_Plot).
The encryption consisted of the combination of a substitution algorithm and the use of symbols instead of the alphabet.

// add Mary cipher image https://en.wikipedia.org/wiki/Thomas_Phelippes#/media/File:Babington_postscript.jpg

Wait, my informant gives me some details about Mary's letters.
Ok, I'm confused, I thought we would find a parade to the frequency analysis, unfortunately, it is not the case.
The letters were indeed decoded, by [Thomas Phelippes](https://en.wikipedia.org/wiki/Thomas_Phelippes),
it was a variant of substitution ciphering: the [nomenclator](https://en.wikipedia.org/wiki/Substitution_cipher#Nomenclator).
Queen Mary was trapped because she was relying on the secret communication that was not secure enough...

We have seen that the mono-alphabetic substitution was easily breakable thanks to the frequency analysis,
the nomenclature version does not help us more, let's go back to the search for a new cipher.

## Vigenère cipher

We have only made a small leap in space,
we are in France on the tracks of a [poly-alphabetic cipher](https://en.wikipedia.org/wiki/Polyalphabetic_cipher).
One of the most famous poly-alphabetic cipher is the [Vigenère cipher](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher).
In fact, [Giovan Battista Bellaso](https://en.wikipedia.org/wiki/Giovan_Battista_Bellaso) is the creator of this method,
and Vigenère cipher is a variant.
Well, how it works? Basically, it is a combination of Caesar Code.
To encrypt a message, instead of keeping the same shift, a table name [Tabula recta](https://en.wikipedia.org/wiki/Tabula_recta) or Vigenère table,
is used.
This table contains all possible Caesar ciphers (26), each line shifted cyclically to the left compared to the previous.

// add Vigenere square https://en.wikipedia.org/wiki/Tabula_recta#/media/File:Vigen%C3%A8re_square_shading.svg

If only one line is used to encrypt and decrypt the message, it is a simple Caesar code.
But if you change the cipher for each character, it becomes a poly-alphabetical cipher.
To define which line to use for a character, a keyword or key-phrase must be defined beforehand.
This work or phrase will be repeated to be at least as long as the message to encrypt.
Then for each character, we will take the line that begins with the letter from the key.

Let's play with an example:

| -         | -               |
|-----------|-----------------|
| Plaintext | cryptoisawesome |
| key       | helloworldhello |


First cipher character is at the intersection of the colon starting with 'c' and row starting with 'h', we find 'j' 
Second one, intersection of the colon starting with 'r' and row starting with 'e', we find 'v'.
Then we continue until the end of the plaintext to encrypt.

<details>
<summary>Answer</summary>
<p>

|      -      |               - |
|-------------|-----------------|
| Plaintext   | cryptoisawesome |
| key         | helloworldhello |
| Cipher text | jvjahkwjlzlwzxs |

</p>
</details>

It is more robust than the Alberti cipher as it is not periodic and so harder to break.
However, the key could be use on Alberti disk to encrypt and decrypt messages.

This cipher will be known as unbreakable for three centuries.
Some messages were decoded but no method was reproducible to break any messages.

Let's find out how cryptanalyst break this new awesome cipher.

## Babbage The Vigenère Cipher Slayer

Here we are, three centuries later, we are in the middle of the nineteenth century.
A “new” cipher is submitted to the Journal of the Society of the Arts in 1853 by John Hall Brock Thwaites an amateur cryptographer.
[Charles Babbage](https://en.wikipedia.org/wiki/Charles_Babbage),
a famous scientist and [pioneer](https://en.wikipedia.org/wiki/List_of_pioneers_in_computer_science) in computer science,
declares that it is only a variant of Vigenère's cipher.
There follows a public challenge, the goal is to find the key from the original text and the encrypted result.
Charles Babbage will not be able to resist and will find the key to the greatest disarray of Thwaites.

Without this event, we probably wouldn't know that he was already able to break this encryption.
We have to understand the geopolitical context to understand how such a discovery can remain secret.
Indeed, the [Crimean war](https://en.wikipedia.org/wiki/Crimean_War) war was raging,
and being able to decipher communications deemed unbreakable is a considerable tactical advantage.
It is easy to think that Charles Babbage was bound to military secrecy to keep this advantage.

Finally, it will be [Friedrich Kasiski](https://en.wikipedia.org/wiki/Friedrich_Kasiski),
a German infantry officer and cryptographer,
who will publish the method of resolution which will bear his name:
[Kasiski examination](https://en.wikipedia.org/wiki/Kasiski_examination).

The method starts from a weakness of the Vigenère encryption, the key is repeated to encrypt the message.
The basic principle is to find repetition in the ciphered words and to check the gap between these repetitions.
This gap will be used to define the size of the key.
Once the key size is found, the cipher can be divided into n simple ciphers and decrypted using frequency analysis.

Let's try this method!
We will start with the text that has been decoded thanks to the frequency analysis.

> Wpwoh dov dh eglf vr hjcjrkiw tikv xjxu ylxmovv keaioi wlj eoeucutjqq ojy? Iqziaes, vr fj eghlgneov, wlj tfzw rjeeu ws ge mqqk jnpwjl yo ugqh yo bp dzjrbih hnsutlfztjqq sk tig flfrbewiws. Jh lx ns oqw xme dcvi, ttigu gmascfxjrjuwmhs ncb fj utgg wzci cv xme gkuwy lfvwiw fsgtyjnda rv yhf wvyfl qqvmyipp rj aoxgow fne errxoocqxx. |

I used an online tool [https://www.dcode.fr/vigenere-cipher](https://www.dcode.fr/vigenere-cipher) to encrypt the text.

Now, we have to search for a repetitive group of symbols and the distances between them.
You can do it by hand, but I prefer to use the "Vigenere Cryptanalysis (Kasiski's Test)" option in the online tool.
Thanks to this result, six-character long, we will split our ciphered text and analyze each group related to the same key character.
It will look like:

| L1  | L2  | L3  | l4  | L5  | L6  |
|-----|-----|-----|-----|-----|-----|
| W   | p   | w   | o   | h   | d   |
| o   | v   | d   | h   | e   | g   | 
| l   | f   | v   | r   | h   | j   |
| c   | j   | r   | k   | i   | w   |

Then, for each letter,
we will apply the frequency analysis and find the key and the matching character exactly like for Caesar's code.
Finally, we get:

| 0             | 1                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Plaintext     | Would you be able to decipher this text without having the encryption key? However, to be efficient, the text needs to be long enough to tend to an average distribution of the characters. If it is not the case, other characteristics may be used such as the first letter frequency or the usual position of vowels and consonants. |
| Key           | abcdef                                                                                                                                                                                                                                                                                                                                  |
| Ciphered Text | Wpwoh dov dh eglf vr hjcjrkiw tikv xjxu ylxmovv keaioi wlj eoeucutjqq ojy? Iqziaes, vr fj eghlgneov, wlj tfzw rjeeu ws ge mqqk jnpwjl yo ugqh yo bp dzjrbih hnsutlfztjqq sk tig flfrbewiws. Jh lx ns oqw xme dcvi, ttigu gmascfxjrjuwmhs ncb fj utgg wzci cv xme gkuwy lfvwiw fsgtyjnda rv yhf wvyfl qqvmyipp rj aoxgow fne errxoocqxx. |

We are lucky because we used computer tools for our example.
I let you imagine the complexity of such a task before the computer era.

I'm talking about computers, but I probably should have talked about machines instead.
And speaking of machines, there is one that has written a part of modern history and that is now legendary.
Let's go and discover it.

## World War Decrypt

The 19th century will see the acceleration of scientific discoveries, especially with the electrification of communications.
[Samuel Morse](https://en.wikipedia.org/wiki/Samuel_Morse) will participate in the advent of the [electric telegraph](https://en.wikipedia.org/wiki/Electrical_telegraph),
and an associated alphabet: the [Morse Code](https://en.wikipedia.org/wiki/Morse_code).
The Morse code is based on the sequence of electrical impulses.
In fact, it is a simple substitution of a character by a composition of two types of impulses, one short and one long.
If you are familiar with the [binary code](https://en.wikipedia.org/wiki/Binary_code),
you will understand easily why it is considered as the first [digital code](https://en.wikipedia.org/wiki/Digital_data).

The wireless telegraph will appear at the very beginning of the 20th century and will use the Morse alphabet.
History repeats itself, a means of communication spreads and so does the need to secure messages.
The Morse code is readable by everyone and therefore requires a layer of encryption.
Some codes that were considered inviolable, such as the [ADFGVX cipher](https://en.wikipedia.org/wiki/ADFGVX_cipher), were quickly broken.
It is with this in mind, just at the end of the World War 1 that a German engineer,
[Arthur Scherbius](https://en.wikipedia.org/wiki/Arthur_Scherbius),
created a legendary brand of encryption machine: [Enigma](https://en.wikipedia.org/wiki/Enigma_machine).

Here we are, during World War II, fighting against the Nazi army.
Each intercepted communication can reveal important information and change the course of the war.
The Enigma machine will be the communication weapon of the German army which will make it evolve little by little towards the most complex model.

Basically, it is a poly-alphabetic cipher with code modification for each character.
Each time you type a character on the keyboard, the wheel will move like distance counter so the code is different for each character.
Moreover, a plug board is used to switch 10 characters and improve complexity.
To understand deeply how this marvel of electro-mechanical technology works,
I invite you to watch this excellent [video](https://www.youtube.com/watch?v=ybkkiGtJmkM).

To realize the power of this encryption machine, let's do a little mathematics.
Let's decompose the configuration of the machine.
First, we can choose 3 wheels among 5: 5*4*3= 60 possibilities
Then, each rotor is composed of the 26 alphabetic character: 26*26*26= 17 576 possibilities.
Now the hard part, the plug board.
We manipulate the whole alphabet, all permutation available: 26! 
But we use only 10 permutation, that means 6 characters are ignored: we can divide by 6!
We do not care about the order: we can divide by 10!
the a->b or b->permutation are the same: we can divide by 2^10
the whole equation for this part is:

26! / (6! 10! 2^10) = 150 738 274 937 250

Finally:
(wheel choice) * (initial rotor position) * (switch board) = mind blow
60 * 17 576 * 150 738 274 937 250 = 158 962 555 217 826 360 000

This is a huge number,
and what it means is that the code is unbreakable without finding a way to reduce the possibilities,
or any other technique to abstract from the manual resolution.

Ok, I went a little fast and there are still a lot of unknowns.
First of all, the machines must have the same initial setting to be able to decrypt the message,
it is then a matter of typing the encrypted message on the machine.
The machine does not emit a signal, for each character typed,
a light lights up under the result and an operator must transmit it on paper or via a means of communication.
The settings change every day following a specific booklet which is changed every month if the booklet is recovered.
Legend has it that the German Navy used a soluble ink to destroy the data easily.


un ensemble de machines qui ont évoluées avec le temps durant la guerre
machine électromecanique
touches keyboard
tableau lumineux lampboard
version arméee +tableau avec inversement des lettres. plugboard

5 rotors amovibles => 3 fonctionnels 60 possibilities

rotor choice: 5*4*3=60 possibilities
starting position for rotor: 26 * 26 * 26 = 17576
patchboard only for army : 

26!
-------      = 150 738 274 937 250
6! 10! 2^10


26! => all permutations available
6 letters not swapped => 6!
don't care about the pair order => 10!
 a -> b and b->a is the same permutation => 2^10 (dived by 2 for each pair)



158 962 555 217 826 360 000

soluble encre

26 positions par rotors 26 * 26 * 26 = 17576
intervertir caracteres 150 738 274 937 250
60 * 17576 * 150 738 274 937 250 
158 962 555 217 826 360 000
et les clés changent toutes les 24 heures.
la machine ne fait que donné le résultats chiffrées.
cahier pour le réglages changée tous les mois
anedocte encre soluble pour la marine allemande


reflector pairs wires
input wheel


rapport de météo
wetterbericht => aucune lettre en commun
Heil hitler

cribs ???

écourté la guerre de 2 ans et 14M de morts

meme réglage d'encodage

rotor tourne a chaque appuie de touche

END of article

## Notes


 historical anecdotes about the improvement of techniques to counter cryptanalysis.
 Mary Queen of Scots beheaded for treason after her letters were decoded
 Alberti's contribution, Vigenère's square
 Babbage's differential machine
 Morse code
 Enigma & Turing
 public key cryptography and the Diffie-Hellman algorithm
 RSA
 public key certificates
 the quantum processor or the end of cryptography.



Improvements:
* the part where the cipher is characterized, maybe with something more formatted...
* add mathematics formula ? 


* [transposition cipher](https://en.wikipedia.org/wiki/Transposition_cipher)
* [substitution cipher](https://en.wikipedia.org/wiki/Substitution_cipher).
* [Symmetric key algorithm](https://en.wikipedia.org/wiki/Symmetric-key_algorithm)

* Edgar Poe
* Enigma
* HAL fun fact

## Why

The need to make a message understandable only to those who need to know is probably as old as communication itself.
When one speaks of a secret message, the image of a spy and a hidden code on microfilm may come to mind,
which is, as we shall see, perfectly valid.
But it can also be a method to protect a knowledge, a manufacturing process or even religious texts.
For the most romantic, it can be a way to protect an epistolary communication of a forbidden love.
Nowadays, it is about protecting the billions of communications made every day in the world.
Anyway, the motivations to use cryptography are numerous and varied.

## How

Cryptography refers to *encryption* which is the process to make a normal message (plaintext) unintelligible (ciphertext).
To go back to the normal message, you have to *decrypt* it.
An *algorithm* and a *key* are used to encrypt and decrypt the message.

To make a message secret, we can :
* make a substitution by character, this is *encryption* (e.g. replace with the next letter in the alphabet).
* make a substitution by word/logical chunk, it is the *coding* (e.g. translate in another language)
* concealing one's own existence, this is called *steganography* (e.g. [invisible ink](https://fr.wikipedia.org/wiki/Encre_invisible))

Hereafter, we will talk about encryption and encrypted message for simplicity. //improve

Now we have a motive and a bit of vocabulary, let's go on the path of history.

// notes
Tout d'abord communication, besoin de transmettre un message de facon sécurisé (religion, amour, guerre)
Arrivée du chiffrement (Code caesar/rot? baton, enigma? Petite frise avec les "codes")
ajout des maths ?

Retour sur internet, création HTTP & contexte échanges publics.
Besoin de confidentialité arrivée SSL (vérifier historique et étapes)
Arrivée de TLS

# Les mains dans le cambouis

Utilisation openssl & langage Go (ou juste le go a voir)
CA (root, intermediates)
Certificate chaining
CSR
certificats
per/der
Comment est valider le certificat ? Browser & code.
CRL

PKI
Cipher Suites
Compression Methods
Extensions Length
SNI
OCSP
Supported Groups
Elliptic curves
Signature Algorithms
Renegotiation Info
SCT

Limitations
    techniques
    légales
mTLS
Gérer ses certificats

DNS over TLS (DoT)
DNS over HTTPS (DoH)

DTLS 

ktls

bpf

Et apres ? (nouvelles technologies/ processeurs quantiques)

# References

outils
protocols
algorithms
articles 
rfc

# Conclusion

D'hier à aujourd'hui meme besoin, outils différents. Puissance de calcul et importance des mathématiques, et demain xxxxx


* https://tls.ulfheim.net/
* https://geekflare.com/tls-101/
* https://www.amazon.fr/Codage-cryptographie-Math%C3%A9maticiens-espions-informatiques/dp/B00T7CNP8G
* https://en.wikipedia.org/wiki/Cryptography
* http://www.cypher.com.au/crypto_history.htm
* https://ieeexplore.ieee.org/abstract/document/8094107
* https://www.youtube.com/watch?v=ybkkiGtJmkM

