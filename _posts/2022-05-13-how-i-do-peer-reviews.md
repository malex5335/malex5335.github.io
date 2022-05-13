I want to lay down some problems I've experienced with a bunch of checks we set as a quasi standard.  
Also, my attempts to fix them and a personal conclusion on how I want to do reviews from now on  
(I'm sure this will change with more experience on the matter).  
I also recommend reading
[What to Look for in a Code Review](https://www.goodreads.com/book/show/28942299-what-to-look-for-in-a-code-review)
written by Trisha Gee, it answers a lot of questions especially towards antipatterns in Source-Code to look out for.

## Where am I coming from?

In a project I'm currently working in we choose to do Peer-Code-Reviews in order to better understand
and check the code for bugs.  
I often struggled to find the right things to point out in those reviews.  
And my colleagues also weren't sure about what to look out for, therefore we made a check-list,
the content of which was highly debated.  
But still we wrote something down and used it as a base for about a year now:
* side effect on existing code
* redundancy
* readability and maintenance
* consistency
* performance
* error and exception handling
* simplicity
* unit tests

We individually have a different understanding of each of those checks, that we can't really discuss
or at least fail to in every attempt so far.  
Leading us all - myself at least - to simply tick the box and keep on coding.  

## The Checks

### side effect on existing code

We had a great debate: "_should we check weather the business logic is impacted in a negative way by
the change we see?_"  
We decided to answer that question with no, primarily because not all of us know the full business
logic and therefore don't feel comfortable deciding this **every single time**, a point which you will
read multiple times and which I want to discuss separately at a later point in this post.  
As a kind of compromise we chose to instead look for known side effects and point them out to our colleagues
that might not know about it.  
Unintentionally creating a hierarchical checkpoint on which you can easily spot who stands above whom.
As a result almost all of us just tick this one and move on, giving false hope of security to our peers and
completely rendering this check useless.

I think it's good to point out something like "_Maybe this would disrupt the feature over here_"
without needing to understand - or even worse looking into - the whole system.  
Therefore, having this in a check-list is ok, so long as you not force the reviewer to assure you,
that the system is safe or scold them if they haven't warned you about stuff that loosely fits in that category.  
That way you take away the pressure to "_make a wrong decision_" and get better results in the end.

### redundancy

"_I already did this, you can find it here_" is something we'd like to hear from our peers, because duplicated
logic in general should almost always be prevented.  
The reason I'm unhappy with this check - or at least how we ended up doing it - is that in our team we tend to
define redundant logic a bit loose.  
If you show someone two identical lines of code and suggest extracting them to a method, I can guarantee you
that it won't take a long to come up with why this can't be done and those are not the same code from a
technical point of view:
* **Now** the logic implies that username is written that way, but it could change in the future
* Calling this one username and having the same pattern for it in both/all cases is just an accident
* Those are 2 separate classes, so they need to implement their logic separately
* I like to search and replace when something has to change and that way I know which parts are bound together

Those and other reasons are often given and by their own one could argue that these are valid reasons.  
Maybe its personal preference but the moment I see the same 5 lines of code written in over 3 classes, which
over time are always changed in the same exact way, I get furious.

I would advise everybody to look for redundant parts of logic and although it's not recommended eliminating
all duplicate lines one could try and test if that's a good idea.  
We, on the one hand want to be flexible and easily change our code, by grouping business cases together but on
the other fail to acknowledge less duplicate lines also means less complex logic and easier access to change
certain parts of our business case.  
As a rule of thumb I say to myself "2 times is ok, 3 times is worrying" and as for the fear of change:
"Code has to change to get better, whether I really need this separated is up to time, not my gut feelings".

### readability and maintenance

This one is highly specific, but I recommend that you at least pay attention while doing peer reviews.  
It all began with our customer not wanting to reinvent the wheel everytime with a new project, but have people
be able to work with the code produced - yeah that one was new to me as far as project requirements go.  
And after the big Code Review we got, one thing was clear: **the code is a maintenance hell**.  
To fix this we simply said: "_Well, in future just pay attention, that anyone would be able to change your code_".  
Aight, that one should be easy! - Surprise just by saying that you did miss a really important point in
the discussion: "What is readable?"  
We had raging arguments with partially laughable conclusions such as "_as long as it's english_" or
"_even the product owner of this project should be able to read it_".  
But we really spent days and weeks discussing on what we should do and had to look out for.  
And as a result we weren't able to fulfil the wish of our customer due to us being indecisive or arguing against
each other in order not to change our coding pattern.

In the end all I can do is say what I personally think is right in order to move in a readable and maintainable
direction but there are other people out there capturing it far better than me.  
I took the advice of letting a different person read your code and maybe even try to implement upon it.  
It's not important whether this person is part of your team, a senior - often times juniors are even better -
or even knows the language You're working with.  
Simply having someone there and take their struggle to understand what you've written seriously can improve
the readability drastically.  
Making Pair-Programming one of the best measures against the demise of code
quality - at least in my humble opinion.

### consistency

(coming soon)

###  performance

(coming soon)

###  error and exception handling

(coming soon)

###  simplicity

(coming soon)

###  unit tests

(coming soon)

## Find an all fits everytime solution

(coming soon)

## Conclusion

(coming soon)
