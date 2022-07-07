---
title: The Machine Learning Landscape
publishedAt: 2019-12-20
editedAt: 2022-07-06
---

Artificial Intelligence (AI) and Machine Learning (ML) are often conflated, but they are not the same.
Rather, ML is a subset of AI.
Deep Learning (DL) is a subset of ML.

![Venn diagram for Artificial Intelligence, Machine Learning, and Deep Learning](images/artificial-intelligence.png)

**AI** is “intelligence demonstrated by machines...that mimic cognitive functions that humans associate with the human mind, such as learning and problem solving”.[^1]
Informally:

> AI systems **seem smart**.[^2]

[^1]: from the [Wikipedia definition for AI](https://en.wikipedia.org/wiki/Artificial_intelligence)
[^2]: The famous [Turing Test](https://en.wikipedia.org/wiki/Turing_test) posits that “seeming smart” is the best observable proxy for “being smart”.

If you think this is a mushy, ambiguous definition, you would be correct.
If you are looking for a more rigorous definition, be prepared to fail.
There isn’t one.

The [fathers of AI](<https://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist)#Contributions_in_computer_science>), John McCarthy and Marvin Minksy, coined the term AI in 1955 to mean "making a machine behave in ways that would be called intelligent if a human were so behaving".[^3]

[^3]: from [A Proposal for the Dartmouth Summer Research Project on Artificial Intelligence](http://www-formal.stanford.edu/jmc/history/dartmouth/dartmouth.html)

<figure>
  <img src="./images/john-mccarthy.jpg" alt="John McCarthy">
  <figcaption>
    <span>John McCarthy in the artificial intelligence lab at Stanford in 1974.</span>
    <i>Photo by Chuck Painter</i>
  </figcaption>
</figure>

In 2005, Minsky coined the phrase ["suitcase word"](https://alexvermeer.com/unpacking-suitcase-words/) to describe how people cram terms like "consciousness" and "intelligence" with different meanings.[^4]
[^4]: from [The Emotion Machine](https://web.media.mit.edu/~minsky/eb4.html)

<figure>
  <img src="./images/marvin-minsky.jpg" alt="Marvin Minsky">
  <figcaption>
    <span>Marvin Minsky in a lab at M.I.T. in 1968.</span>
    <i>Photo by M.I.T.</i>
  </figcaption>
</figure>

Are virtual assistants like Siri and Alexa "smart"?
How about automated phone systems?
Or calculators?
Reasonable people will disagree.

**ML**, on the other hand, is the ability “to perform a specific task without using explicit instructions, relying on patterns and inference instead”.[^5]
Informally:

> ML systems **seem smart** by using **patterns** in data.

[^5]: from the [Wikipedia definition for ML](https://en.wikipedia.org/wiki/Machine_learning)

Unlike AI, ML can be defined much more rigorously, even mathematically.
For example, in ML we can often define an **accuracy metric** to formalize what we mean by “smart”.