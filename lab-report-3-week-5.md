Command Chosen: Grep

Option 1 - grep -E

The -E command makes grep use regular expressions to match the pattern, this can be very useful when
you don't just want to search for a specific phrase but a pattern instead.

Example 1. We use ‘grep -e “physics|chemistry” plos/*’ to search for all occurrences of the word
chemistry OR physics in the plos folder. This allows us to search for multiple terms of one.

*NOTE: Command outputs have been shortened in this document to save space.

```
grep -E "physics|chemistry"plos/* ✘ 1 01 : 26 : 02 PM
plos/journal.pbio. 0020012 .txt: Kenyon, professor of biochemistryand
biophysics at the University of California at San
plos/journal.pbio. 0020035 .txt: stereochemistry of the moleculesin a
combinatorial fashion to produce an enormous variety
plos/journal.pbio. 0020035 .txt: A further variable concerns the
stereochemistry of the hydroxyl groups and methyl or other
plos/journal.pbio. 0020042 .txt: the function of these hypotheticals
based on solid, old-fashioned biochemistry. The essence
plos/journal.pbio.0020046.txt: Neurochemistry, however, may link
stuttering with disorders of a network of structures
plos/journal.pbio. 0020053 .txt: Antibiotic discovery is all
chemistry, Shapiro says, which is why she joine
```
Example 2. We use ‘grep -E "[0-9]{4}" plos/*’ to search for all 4 digit numbers in plos, this is useful
because it allows us to search for relevant year dates in any of the documents.

```
~/Documents/CSE15L/LAB5/technical grep -E "[0-9]{4}" plos/*
✔ 01:33:21 PM
plos/pmed.0020247.txt: Goffman's seminal work on stigma in the early
1960s, stigma (plural stigmata) has been
plos/pmed.0020249.txt: infection with a probability of approximately
0.0005-0.10 [14-17], such extremely low doses
plos/pmed.0020272.txt: PLoS Medicine (DOI:
10.1371/journal.pmed.0020124), that the majorityof
plos/pmed.0020272.txt: ("in this study 5%of people examined who
lived in San Franciscofrom 1965-1970 developed
plos/pmed.0020278.txt: The only people who don't know in 2005 that
animal research is irrelevant for human
plos/pmed.0020281.txt: D.C., on May 15th, 2005, at the invitation
```

```
and support of the Public Library of Science and
plos/pmed.0020281.txt: Ralph Waldo Emerson, American essayist and
philosopher (1803-1882), commented about
plos/pmed.0020281.txt: 2005): "To leave the world a bit better,
whether by a healthy child, a garden patch or a
```
Example 3. Lastly, we use ‘grep -E "summer|winter|spring|summer" plos/*’ to search for any of the 4
seasons, which is useful to see when the information is relevant to any season.

```
~/Documents/CSE15L/LAB5/technical grep -E "summer|winter|spring|summer"
plos/* ✔
01 : 35 : 45 PM
plos/journal.pbio.0020053.txt: By next summer, more than 40 % of
plos/journal.pbio.0020053.txt: spring of 2003. It's too earlyto
tell whether that prediction is precisely on track,
plos/journal.pbio.0020054.txt: average. Australia's summer months
around the turn of 2002-2003 brought perhapsthe worst
plos/journal.pbio.0020054.txt: including in Southern California last
summer. Maps of actual and predicted surface winds
plos/journal.pbio.0020068.txt: host cells and undergo maternal
transmission to offspring. These microbes have piqued the
plos/journal.pbio.0020068.txt: frequency of infected female
offspring, often at the expense of their hosts. Such
plos/journal.pbio.0020068.txt: offspring and, in the case of
obligate mutualists that coevolve with their hosts, limited
```
Option 2 - grep -o

We can use -o to search for only the parts of the document that match our pattern, this is useful for when
we might want to quickly count the occurrences, or maybe transfer just the occurrence to another
document.

Example 1. We use “grep -Eo "physics|chemistry" plos/* to find the occurrences of chemistry and physics
in all of the documents, using this we can easily see which documents are relevant to physics or
chemistry.

```
~/Documents/CSE15L/LAB5/technical grep -Eo "physics|chemistry" plos/*
✘ 2 01 : 38 : 58 PM
plos/journal.pbio. 0020012 .txt:chemistry
plos/journal.pbio. 0020012 .txt:physics
plos/journal.pbio. 0020035 .txt:chemistry
```

```
plos/journal.pbio. 0020035 .txt:chemistry
plos/journal.pbio. 0020042 .txt:chemistry
plos/journal.pbio. 0020046 .txt:chemistry
plos/journal.pbio. 0020053 .txt:chemistry
plos/journal.pbio. 0020053 .txt:chemistry
plos/journal.pbio. 0020054 .txt:physics
plos/journal.pbio. 0020067 .txt:physics
plos/journal.pbio. 0020067 .txt:physics
```
Example 2.We use ‘grep -Eo "Jeremy|Springer"’ to find all and only the occurrences of either Jeremy, or
Springer in the texts. Say we know an author Jeremy Springer contributed to the texts and we want to find
the texts in the folder which he contributed to. We can easily find them with this command.

```
~/Documents/CSE15L/LAB5/technical grep -Eo "Jeremy|Springer" plos/*
✔ 01 : 42 : 58 PM
plos/journal.pbio. 0020113 .txt:Jeremy
plos/journal.pbio. 0020169 .txt:Springer
plos/journal.pbio. 0020169 .txt:Springer
plos/journal.pbio. 0020272 .txt:Jeremy
```
Example 3. Furthermore if we want an exact count of the lines, we can use “grep -Eoh "Jeremy|Springer"
plos/* > output.txt; wc output.txt” to count the exact number of times either his first or last name shows
up in the document, and then can easily access output.txt to see in which documents that is.

```
~/Documents/CSE15L/LAB5/technical grep -Eoh "Jeremy|Springer" plos/* >
output.txt; wc output.txt ✘ 0|
01:47:59 PM
4 4 32 output.txt
```
Option 3. -v

The -v flag inverts the pattern meaning it will search for all lines that do NOT match the expression.

Example 1. Say I want to search for files that do not mention biology in plos, I can simply do ‘grep -vl
"biology" plos/*’ which would return all of the documents that do not contain biology.

```
~/Documents/CSE15L/LAB5/technical grep -vl "biology" plos/*
✔ 01 : 51 : 21 PM
plos/journal.pbio.0020001.txt
plos/journal.pbio.0020010.txt
```

```
plos/journal.pbio.0020012.txt
plos/journal.pbio.0020013.txt
plos/journal.pbio.0020019.txt
plos/journal.pbio.0020028.txt
plos/journal.pbio.0020035.txt
plos/journal.pbio.0020040.txt
plos/journal.pbio.0020042.txt
plos/journal.pbio.0020043.txt
plos/journal.pbio.0020046.txt
plos/journal.pbio.0020047.txt
plos/journal.pbio.0020052.txt
plos/journal.pbio.0020053.txt
plos/journal.pbio.0020054.txt
```
Example 2. If I wanted to count the amount of lines the syllable ‘a’ did NOT show up in (maybe for a
research project in which I am investigating the frequency of syllable occurrences), I could simply do
‘grep -v "a" plos/* > output.txt; wc output.txt’

```
~/Documents/CSE15L/LAB5/technical grep -v "a" plos/* > output.txt; wc
output.txt ✔
01:53:36 PM
5309 9264 196589 output.txt
```
Example 3. In a final combination of all my commands for my syllable research project, I want to read all
lines that do not contain a syllable, and only the text that does not contain that syllable, so I do “grep -voE
"a|e|i|o|u" plos/*” (unfortunately, this results in mostly blank lines).

```
grep -voE "a|e|i|o|u" pclos/*
plos/pmed. 0020274 .txt: RNA.
plos/pmed. 0020274 .txt:
plos/pmed. 0020274 .txt:
plos/pmed. 0020274 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020275 .txt:
plos/pmed. 0020278 .txt:
```



