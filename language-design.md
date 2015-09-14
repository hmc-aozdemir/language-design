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

One way to think about this question is to look at how we grew/changed the language during the lab. We didn't change any of the words (fundamental operations), but we dramatically changed the syntax to allow for more concise use and greater composability. Whereas the original language made composition of sound transformations very challenging, the new syntax allowed for them to be more easily chained.

One approach, which we will refer to as the 'method appraoch' defines a sound class and methods of it which transform and return it, allowing for use like this:

    my_sound.amplify(2).reverse().play()
   
One nice property of this approach is that it that it aligns reading/writing order (left to right) with execution order.

Another approach, which we will call the 'function approach' is to have static functions which transformed sound objects like so:

    play(amplify(reverse(my_sound), 2))

This doesn't read/write as nicely, but it allows for the basic functions to be composed, and their compositions would form functions that have the same type as the provided functions.

Zoab notes that even with the method approach users can subclass and add compositions of fundamental operations to their subclass, but acknowledges this does create a difference between user-implemented compositions and the language's fundamental operations. He thinks that aligning read/write ordering with execution ordering is worth creating that distinction.

In the langauge of Guy L. Steele [Steele, 1998] the 'function approach' provides a better plan for growth, which might be advantage.

Interestingly, traditional linguistics also identify this composability as a key linguistic feature._Language Files_ , written by Vedrana Mihalicek identifies
- the existence of discrete building blocks, and
- rules for composing them and labelling those compositions
as key features of languages (Chapter 1).

---

**Question**

How would you know a well-designed language? What are the symptoms? How would
you know a poorly designed language? What are the symptoms?

**Response**



---

**Question** 

In what way is an API a language? 

**Response**

We both agree that an API is indeed a language. To think about how an API is a language we note that languages have both vocabulary and syntax (both character choice and rules of composition). API's are very restricted in terms of syntax by their host language. This means that often their syntax is often trivial. That being said they still allow for a rich variety of vocabulary in the form of operations that can be performed.

API's are also much esier to build than some type of DSLs (say external DSLs). For this reason many authors [Mernik et al., 2005] identify API's as being the first stage in the development of DSLs that ultimately become complex external DSLs.

A number of concerns in designing good APIs (as identified by Bloch [Bloch, 2006]) are also concerns in designing a language.

While one might be tempted to divide languages from APIs on the basis of syntax complexity, some API's end up having non-trivial syntax. For example, consider the SQL query generator [QueryDSL](https://github.com/querydsl/querydsl/tree/master/querydsl-sql). It allows the user to construct SQL queries using Java syntax. One might imagine that a query beginning

    query_builder.from(my_table)

might be well formed, but

    query_builder.from(my_table).from(other_table)

might not be.

Also, the definition of API is blurred. While Zoab thought APIs should be in the language the programmer is working in, Alex was not as certain that that was a requirement.

---

**Question**

The comments on the Pavlus article seem to set up a conflict between
professional programmers and everyone else. What is the essence of this
conflict? Do you sympathize more with the substance of the article's arguments
or with the substance of the majority of the commenters' arguments? Do you
sympathize more with the tenor of the article or the tenor of the majority of
the commenters?

**Response**

In the comments, it seems that some people are debating the merits of making a language easy to learn vs easy to use, with professional programmers favoring the latter and "everyone else" favoring the former. An example of such an argument is made by Strengthiness 
> A language like Quorum may be good for learning programming concepts, but as an everyday tool for a professional programmer it would be so overly verbose as to just slow one down
We believe this is a false dichotomy - there isn't necessarily a tradeoff between ease of learning and ease of use for programming languages. Some choices would make a PL harder to use for both first-time users and experienced programmers - consider, for instance, requiring all string literals to be presented as character arrays. I think we can all agree that nobody would prefer having to input
    char myString[] = {'h','i','!','\0'};
to
    char myString[] = "Hi!";
However, in some cases, there may be a tradeoff between making a language easy to learn and easy to use. Scratch, for instance, was designed to be an easy to learn language (since it's meant to be an introductory language for new programmers) but is virtually impossible to write complex programs in. 

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

We read the articles separately, then sat down together to discuss them and wrote our responses as we discussed. We switched off who was writing every question or two.

---
