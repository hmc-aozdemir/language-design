_Fill in each this file with your responses, placing each response after its
corresponding question._

---

**Question**

Pick three quotes from the readings about language design. Good candidates 
are:

   + Something you agreed with / resonates with your own experience
   + Something you disagree with
   + Something that is interesting, a new idea or perspective you'd like to remember
   + Something you didn't understand

For each quote, describe what it was about the quote that led you pick it.

**Response**

>Names matter. Strive for intelligibility, consistency, and
>symmetry. Every API is a little language, and people must learn to
>read and write it. If you get an API right, code will read like
>prose. [Bloch, 2006]

Both Alex and Zoab felt like this point resonated with them. Especially when reading someone else's code, Zoab has observed that the quality of names affects the ease with which he can understand the code - variable names, method names, etc. that correspond to the semantics of the construct allow you to get an idea of how the construct works without having to closely read the implementation. Alex says "Every name is like a gateway. If you understand the name, you can stop reading. If you don't understand, you have to then go read all of the implementation behind that name."

They both recognize that choosing good names can be a struggle, especially when dealing with abstract or complex constructs, but they both think it's worth putting in the effort. There will always be people who misunderstand your naming convention, but if you put effort into choosing names, you can minimize that set. 

> This leads me to claim that, from now on, a main goal in designing a language should be to plan for growth. [Steele, 1998]

Alex and Zoab don't necessarily agree with this statement. They understand that the person making this statement is a general purpose programming language designer, and they can understand the validity of this claim for general purpose programming languages. However, it's not obvious to them that for DSLs in particular, you'd want to design them with a plan for growth. Consider a language that has already expanded to fill its domain, where its domain is likely to remain static. In this case it wouldn't necessarily be a good idea to plan for growth. An example of this kind of language is Picobot - if there's a trade off between making Picobot easier to use or making it easier to grow, we should choose to make it easy to use because we don't expect to have to grow it. 

> We need to put tools for lanugage growth in the hands of the users. [Steele, 1998]

What does it mean to put the tools for growth into the hands of the users? Alex thinks that means that there should be a way for one users changes to the language to be accepted by the rest of the community. Zoab thinks that one problem with this is that the language could easily grow to be too large because, as we already know, we can't ever take anything out of a language while we're free to add stuff in, so if we make adding stuff easy the growth of the language could quickly spiral out of control. Alex thinks that these issues would still be faced by a central language writing body, and by allowing for any user to contribute we'd have to tackle these issues with a review process. Zoab thinks in practice, even with a review process, bad code and bad style can slip through and become part of the project as a whole. 

The question, then, is whether having a project that is user-responsive and can be built on quickly is worth the cost of some usability difficulties. Alex notes that this tradeoff isn't a necessary one - if we can figure out how to be better reviewers, we can minimize the downsides of open sourcing while not compromising on the benefits. 

---

**Question**

How do the themes of _Growing a Language_ relate to the lab we did this week?

**Response**

We didn't necessarily grow the vocab, but we grew the syntax - initially you could only have one word sentences, now you can chain verbs together.

---

**Question**

How would you know a well-designed language? What are the symptoms? How would
you know a poorly designed language? What are the symptoms?

**Response**



---
 

In what way is an API a language? 

**Response**



---

**Question**

The comments on the Pavlus article seem to set up a conflict between
professional programmers and everyone else. What is the essence of this
conflict? Do you sympathize more with the substance of the article's arguments
or with the substance of the majority of the commenters' arguments? Do you
sympathize more with the tenor of the article or the tenor of the majority of
the commenters?

**Response**



---

**Question**

How do implementation choices (e.g., as an interpreter/compiler or as an
internal DSL) affect the user experience? Can or should we always hide our
implementation choices from users?

**Response**



---

**Question**

The Pavlus article mentions the researchers' comments that people preferred
"natural-language replacements for some of the more abstruse syntax". In other 
words, people found it easier to work with code that looks more like a human language (e.g.,
English). Consider the following quote by William R. Cook, one of the creators
of JavaScript:


> The experiment in designing a language that resembled natural languages (English
> and Japanese) was not successful. It was assumed that scripts should be
> presented in “natural language” so that average people could read and write
> them. … In the end the syntactic variations and flexibility did more to confuse
> programmers than to help them out. It is not clear whether it is easier for
> novice users to work with a scripting language that resembles natural language,
> with all its special cases and idiosyncrasies. The main problem is that
> AppleScript only appears to be a natural language: in fact, it is an artificial
> language, like any other programming language. … even small changes to the
> script may introduce subtle syntactic errors that baffle users. It is easy to
> read AppleScript, but quite hard to write it.
[[Cook 2007, page 1-20]](https://dl.acm.org/citation.cfm?doid=1238844.1238845)

Are these two experiences of natural languages at odds with one another? Would
you choose to include natural language in the design of a DSL? If so, how might
you do so? If not, why not?

**Response**



---

**Question**

Briefly describe how you split up the work for this assignment.

**Response**



---
