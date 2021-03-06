colah's jumbled thoughts on romance
====================================

**Note: These are personal thoughts on a very personal and sensitive issue. Please look at [the readme](https://github.com/colah/Semi-Public-Journal/blob/master/README.md).**

Optimal Dating Strategies
---------------------------

A few mathematicians have considered optimal strategies for dating. Extremely simplified models of dating have optimal strategies, but things explode as one introduces even moderately realistic circumstances. Further, I have serious concerns about the utility functions these are optimal strategies under.

The general way the problem is discussed is as the [secretary problem](http://en.wikipedia.org/wiki/Secretary_problem). In this problem, one is trying to get the best secretary out of a group of applicants. One can try the secretaries in sequence. Each candidate is objectively better or worse relative to others. Each time, one must either select that applicant, or move on to the next with no chance to return. Applicants always accept the job, and one is solely concerned with getting the *best* candidate. The optimal strategy is to reject the first n/e candidates (~36%) and accept the next best one.

The simplest flaw, that of only being concerned with getting the best candidate, has been corrected in more sophisticated formulations. Bearden, in [Skip the Square Root of n: A New Secretary Problem](http://www.sie.arizona.edu/MURI/cd/content/Bearden%20Skip%20the%20Sq%20Rt%20of%20n%20Thrusts%20A%20and%20C.pdf) considers maximizing expected value when candidates are random variables from the uniform distribution on \[0,1\] (but we can only observe if candidates are better than previous ones). The optimal strategy, as you might infer from the title, turns out to be skipping sqrt(n). To me, a uniform distribution seems pretty naive, and a normal distribution seems substantially more realistic. I performed computer simulations testing all skip-and-next-best strategies on up to 500 candidates (one million experiments) and found the ideal number to skip to be almost perfectly linear and roughly 10%. If we do allow ourselves to actually know the candidate quality instead of just comparison ("full information"), this is apparently equivalent to a problem posed by Cayley and solved for general distributions by Guttman in 1960 (Freeman, [The Secretary Problem and its Extensions: A Review](http://isites.harvard.edu/fs/docs/icb.topic1174303.files/freeman%201983%20the%20secretary%20problem.pdf)).

But there are much more severe problems. It has been observed that one severe failing of the secretary problem as a model for dating is that in dating, the other party may not accept you. (That said, on certain restricted subsets of people, things do become more like standard the secretary problem, as we will see later.) A more realistic model is to [think of it as a dual secretary problem](http://mat.tepper.cmu.edu/blog/?p=1392), where both parties are mutually performing the same optimization. This problem is massively more complicated and eludes optimal strategies.

(My intuition for a good strategy, if one isn't only trying to get the best candidate, is as follows. For simplicity, we consider the homosexual case, so that there's only one candidate pool. Then one should use the sampling phase not only to determine what a good candidate looks like, but how could a candidate you are. Then you target everyone more than a certain amount better than you -- you exploit the intrinsic error margin in finding good candidate -- and gradually drift towards candidates that are worse than you as time goes on. For the heterosexual case, you need to do something more complicated to get a good sense of where you are in the applicant pool.)

This pictured universe is really quite tragic. With perfect information, the two best parties end up with their best match, and everyone else ends up in a suboptimal relationship. And if you aren't one of the two best parties, the only way for you to have your best outcome is for your partner to be ignorant of better options. It's a classic zero-sum game situation.

There are a lot of major assumptions in this model. To list a few:

 * Candidate quality is independent of the agent
 * Monogamy
 * Utility of outcome is solely determined by candidate selection

Dropping any of these introduces substantial doubt about the zero-sum nature of the game, but the first seems to be the most significant to me. In reality, it seems like what constitutes a desirable romantic partner varies massively from person to person. Better yet, in a lot of candidate dimensions, such as interests or values, similarity is generally attractive. This symmetry means that you will generally be more attractive to people who are attractive to you. An extreme version of this to imagine is that candidates all prefer those that are most similar to them, in which case the problem is clearly extremely positive-sum.

The impact of allowing polyamory is complicated by the fact that it encompasses a large range of possibilities. Does each partner take a specific number of other partners, say two or three? Or perhaps they choose a way to distribute their time across various partners, turning it into some sort of differential game. But unless you allow everyone to have arbitrarily many relationships at no cost, which would admit a certain trivial solution, this doesn't actually seem to impact whether an outcome is a zero-sum or positive-sum game.


The fact that, in reality, the utility of an outcome isn't solely determined by who gets paired with who, is an aggregate of a large number of important issues that cast significant doubt on the optimality of a "sample then chose" strategy. 

* There isn't a single relationship that two people can form, but a large number of them, and the nature of their relationship can change over time. People sometimes invest a great deal of energy trying to shift their relationships in a positive direction (consider marriage counseling), but it seems that this is often very challenging. People's past actions set a context for future ones, and when the context is negative that seems to be very difficult for them to get past. It seems likely that very early interactions are important in the formation of this context.

* Even if the quality of a relationship was determined by the two people in it, that may not overshadow different costs of a strategy. It appears that there is a great deal of potential to hurt your partners in this matter if one isn't careful. Additionally, one can severely hurt themselves, and entering a relationship has a significant energy investment.

* Intuitively, I feel like there's something very special about the first relationship. That if I could make it be really awesome and work out, that would be best. That I might be less able to form deep relationships after it. Everyone I respect tells me this is ridiculous. H- proposed as a test that I should try and find an expert who will argue for this position, and if I can't that is strong evidence against it -- I haven't tried yet, but the fact that I don't have a very high confidence in succeeding doesn't bode well for this. I don't really intellectually believe this to be true, but I feel it very strongly emotionally.

Other Romance Game Theory
----------------------------

* [The Multi-Armed Bandit problem](http://en.wikipedia.org/wiki/Multi-armed_bandit): The mult-armed bandits are slot machines, with different pay outs which you can only learn by trying them. There's a tradeoff between exploring the possibilities and exploiting the best option you find. The problem generalizes to lots of scenarios where you are distributing resources between possibilities. For example, if you have multiple romantic candidates of unknown quality...

* [The Stable Marriage Problem](http://en.wikipedia.org/wiki/Stable_marriage_problem): Suppose we have N men and N women. Every man/woman has an ordering of the other gender by which partner they prefer to which. A solution (a one-to-one pairing of each man to woman) is "stable" if there is no man-woman pair that mutually prefer each other to their present partner. Does a stable solution exist?

      Yes, it does, and a simple algorithm can find one. Pick one gender, say men. Have men, in sequence, go to each women and propose to her. If she prefers them to her present partner, she accepts and rejects her present partner (always accepts if no partner), otherwise she rejects him. The rejected partner then goes down their list until they find their match. This algorithm halts in O(N^2) steps with a stable solution.

      It appears like it didn't matter which gender asked, just that we only had one gender ask and one gender accept/reject. If you're a little suspicious of that... well you should be! The gender that asks gets, on average, does much much better! Consider the list of preferences to have in position 0 the most preferred partner, 1 the second most, and so on... (So a low number is good.) On average men get their log(N) candidate, but the women get their N/log(N) candidate. However, when there is a gender ratio imbalance, who asks ceases to matter and the gender with fewer candidates does much better. Even just a difference of 1 reverses N/log(N) and log(N) expectations. (Read more in [Ashlagi et al's paper: Unbalanced random matching markets](http://web.mit.edu/iashlagi/www/papers/UnbalancedMatchingAKL.pdf) and [this blog post](http://gilkalai.wordpress.com/2013/04/19/itai-ashlagi-yashodhan-kanoria-and-jacob-leshno-what-a-difference-an-additional-man-makes/).) In considering this, it is worth noting that both parties benefit enormously from N increasing, since important thing isn't the position in the list, but the ratio you are through the list (since this corresponds to the percentile of the sample the match is in), which both (1/log(N) and log(N)/N) fall drastically as N increases.

      (In fact, there's something even deeper here: Knuth et al found the solution space to form a lattice with male-optimized and female-optimized cases as the top and bottom.)

      A large number of variations on the stable marriage problem have been considered, including ones analyzing incomplete lists, tied preferences, and what amounts to homosexual and polyamorous cases (though these are discussed as the roommate problem, etc). Iwama and Miyazaki have a nice review paper: [A Survey of the Stable Marriage Problem and Its Variants](http://140.123.102.14:8080/reportSys/file/paper/scfu/scfu_21_paper.pdf) on these.

* [Monogamy as a Prisoners Dilemma: Non-Monogamy as a Collective Action Problem](http://www.changesurfer.com/Acad/Monogamy/Mono.html) -- note that I've only skimmed this so far and marked it down as something to look at.


Anti-Patterns
--------------

People do all sorts of really troubling things in relationships. If we note them, we can make sure to avoid them in ourselves and potential partners.

* Lots of partners are subtly mean and coercive to each other.

* A lot of relationships don't seem to be between equals and have power dynamics. (I don't really understand being attracted to someone you don't consider your equal?)

  * On the other hand, some people enjoy that -- the extreme example being consensual BDSM relationships -- and I'm not trying to be judgmental.

  * I think I'm talking about something subtler...

* Some studies have found rather negative correlations age-disparity and relationship outcomes for the younger party -- the one I'm thinking of was either more than 5 or 7 years. "You aren't a lottery ticket" and all that applies, but...

Rambles
---------

* What is a good romantic partner? Triggers romantic attraction? Makes you happy? Makes you feel peaceful? Drives your growth/productivity? Good reproductive partner (genetics & child rearing skills)? You don't fight? Sex? Social status? A weighted combination of the above? It varies over time?

* I don't see much reason to think that Humans are particularly good at recognizing good partners, especially if "makes you happy" isn't the primary quality you are looking for in a partner. And especially when it comes to differentiating between fairly good and great partners -- clearly we're quite good at avoiding certain classes of horrible relationships!

* Most people never meet the people they could form the best relationship with. The larger the candidate pool, the greater the variation between the best match you are likely to meet and the best match out there. So, the present situation on Earth is extremely tragic. Computer association of partners is a promising solution. See Human Pairing Problem essay.

* Unpleasant men seem to be disproportionately successful in dating.
 * Purely anecdotal, may suffer from a number of biases, notably confirmation bias.

* A lot of people I deeply respect are polyamorous.

  * Polyamory is illegal in Canada: CCC s. 293 is title polygamy, but more general; see also Reference re: Criminal Code, s. 293, 2010 BCSC 1308. (I'm deeply skeptical that this would survive serious Charter scrutiny and think this is a Human rights violation. Unfortunately, the case law seems to have solely developed in the context of Bountiful, British Columbia.) In any event, *obviously* all these polyamorous people I deeply respect do not live in Canada. And even were I persuaded that polyamory is a good idea, I obviously wouldn't act on that while I remain in Canada.

  * Polyamory seems to have a bimodal distribution of relationship quality, with most relationships I'm aware of either being really admirable or horrifying. (This may just generally be true of relationships that are not socially normative. Standard deviation of relationship quality increases...)

  * There are moderately compelling arguments for polyamory.

  * I'm concerned these technical supperiority arguments my be red herrings:

    I could make an argument that heterosexual relationships are better than homosexual ones. They can reproduce. Their bodies are more naturally suited for mutual pleasuring. And so on. At this point, people are kind of memetically vaccinated against arguments for this position, but I bet if they weren't I could make this quite persuasive.

    And, even if it were true in some technical sense, it would be a toxic argument. It would just delegitmize gay people's feelings. It might even make some try to be something that will make them less happy because that's "better". And for all the technical arguments we can make for one thing better or worse, how it effects those involved is all that matters. The argument would be harmful (except maybe in some very specific context).

    I feel like this is kind of the same.

  * In polyamory, one can have different partners that optimize for different types of "good" things in a romantic partner. For example, one partner might make one happy, while another might cause one to develop as a person.

  * It seems reasonable to think that whether polyamory is a good idea or not varies greatly from person to person.

  * I am personally uncomfortable with the idea, and pretty certain that it isn't for me, despite thinking they can be ethical.



* Non socially normative relationships present some interesting difficulties.

  * In average relationships, people have an external set of expectations about how to behave in a relationship. How to treat each other, expected behavior, etc. They may be quite problematic, including sexist, but they're external to the relationship. Obviously, these external expectations don't cover everything, but they give a sturdy framework.

  * Once you throw those away, things get much more confusing. Partners often have different expectations.

  * A power dynamic can form where one partner gets to decide all the expectations (and change them).

  * It seems like having an early conversation about this is a good idea in a relationship. Perhaps even independently writing out what one expects in the relationship.

Romance Space & Clusters
-------------------------

THIS SECTION IS MUCH ROUGHER AND LESS THOUGHT THROUGH THAN USUAL. TAKE IT WITH A BIG GRAIN OF SALT!

Mathematics and computer science are important to me. They're important to me in a way that I think most people don't have a subject that is important to them. They're part of how I think and speak and communicate. The idea of having a partner who could share an appreciation of these things that are deeply important to me is really really appealing.

Many people have tried to persuade me that this isn't the case, and I'm not very confident in my understanding of my feelings. However, several people that I've spoken to, both males and females, describe the same thing. The fact that 80% of female mathematicians marry other mathematicians (Gibbons, 1992) also greatly reinforces my confidence.

My suspicion is that most people are attracted to others that are similar to them in some manner, though the specifics vary greatly. Some dimensions don't matter. In some cases, asymmetry helps. Define "mutual attractiveness" as:

a(x,y) = 1/min(how attracted x is to y, how attracted y is to x)

Then a(x,y) = 0 means both parties are infinitely attracted to each other.

This doesn't form a metric structure. For example, most people aren't narcissists so a(x,x) = 0 infrequently holds. Similarly, since the majority of people are heterosexual, the triangle inequality frequently doesn't hold. On the other hand, I suspect that some sort of rectangle inequality is probably moderately true, especially if you consider averages over lots of middle points.

I also suspect that if you mod out a few variables like gender, this probably becomes quite close to a metric space. Let a'(x,y) be this "modulo mutual attractiveness".

Consider 


Are Relationships a Good Idea?
--------------------------------

That relationships are a positive thing and an ultimate part of positive outcomes in life is quite broadly accepted, save a few edge cases like priesthood. This isn't at all surprising. Romantic relationships are essential to evolutionary success, and evolution has many tricks to keep us on this path.

But it isn't immediately clear to me that relationships are generally positive things in the long run. Answering if or when they are is clearly an extremely important question for my long term well being.

* Initial romantic attraction is a very pleasant experience, partly characterized by "labile psychophysiological responses to the loved person" by Fisher. However, it generally fades after about six months. The experience of romantic attachment is less obviously pleasant and more enforced by negative feelings to damage of the relationship. (See Fisher, 1998) Perhaps evolution gets us where it needs us with a carrot, then switches to a stick?

* Romantic relationships involve a tremendous risk of being very deeply hurt.

* Romantic relationships have a very deep time and energy investment.
  * Thinking of time as an inelastic resource is kind of naive, in my experience. So much of my time falls through the cracks, and I recapture it when I have the right motivations.
  * Early romantic attraction frequently involves a reduced need for sleep (because of increased dopamine?)...

* In romantic attraction / relationships, partners are often ready to under go radical changes in themselves to make themselves more appealing to the desired partner.
  * A visible example of this is that people often radically change their physical appearance at the beginning of relationships.
  * This cuts both for and against romantic relationships. They could both help one change in positive and negative ways, largely depending on (your perception of) your partner.

* Many friends and people that I respect tell me of how greatly relationships improved their quality of life. Others describe it not having much impact after a few months of feeling amazing. A small number are extremely negative about it. But I don't think any of them are a terribly objective source.

* JK- referred me to this really interesting LessWrong post, [How To Be Happy](http://lesswrong.com/lw/4su/how_to_be_happy/), which reviews research into happiness: "Factors that don't correlate much with happiness include: age, gender, parenthood, intelligence, physical attractiveness, and money (as long as you're above the poverty line). Factors that correlate moderately with happiness include: health, social activity, and religiosity. Factors that correlate strongly with happiness include: genetics, love and relationship satisfaction, and work satisfaction."

Productivity And Romance
-------------------------

(A lot of this is the same content as "Are Relationships a Good Idea?" from a different perspective.)

Naively, relationships seem very harmful to ones productivity. It's clearly a huge time investment. One can argue that many people's productivity would be harmed more by not being in a relationship (depression, sadness, obsessive thoughts about it)...

But "it's the least bad option" is not a very satisfying answer.

(I don't like evolution beating me into a corner with a dopageneric stick.)

So, the question is, can there be a positive relationship between romance and productivity. The following is brainstorming:

* Typically, couple's bonding time consists of things like watching movies, lazing about, talking about unimportant issues, etc. But if both parties are more interested in higher concerns, can that lead to them instead spending time learning or working on valuable projects?
  * Elements of this in D-&J- and E-&J- ??

* During romantic attraction, people change themselves to be more attractive to their partner, including changes to physical appearance, beliefs, ideals, etc. If attributes that make you attractive include things like ethics or intellectual curiosity...

* Could romance allow deeper collaboration through intellectual intimacy -- less filtering, more honesty about feelings?

* There's a pretty long tradition of romantic partners as scientific collaborators.
 * Famous example: Marie Curie & Pierre Curie 
 * Seems quite wide spread. Asking one friend in Academia, then rattled off a list of a dozen or so pairs with little thought.
 * A small body of literature has built up exploring this topic. Terms to search for are: dual careers, academic couples, intimate collaborators, intimate romantic partners, etc.
 * *Knowledge Production, Publication Productivity, and Intimate Academic Partnership* (Greamer, 1999) explores the effects of romantic partners as collaborators on productivity. It's a very small and limited sample in a few ways (eg. older generation). There's high variance in the impact of these relationships on productivity. There's also a striking pattern of partners feeling unable to heavily collaborate because of the expectations of the academic community. Informal feedback and honest criticism on work from partners may be important. One pair of psychologists seem to have a story of very deep and extremely important collaboration where they mutually developed ideas over years of conversation. 
  * *Love in the lab: Women scientists and engineers married to or partnered with other scientists and engineers* (Blaser) begins with a nice literature review and lots of references. One interesting quote: "Approximately
70% of female physicists are married to other scientists and 80% of female mathematicians are married to other mathematicians (Gibbons 1992)." (I haven't been able to read Gibbons yet). 
  * Seems like early research found negative correlations for male productivity with having an academic partner. It is speculated that this is because of a more egalitarian distribution of house work. It may be better modernly? (Also, I'd personally value that and would do that regarless of partner, so it doesn't matter much.)
  * (I should review further when not half-asleep)

Removing One's Self From The Dating Pool
-----------------------------------------

I often wish I could just rid myself of romantic attraction (and attachment, etc). I often wish this, despite the fact that I'm generally persuaded that a romantic relationship (with a the right partner!) would make me much happier, and wouldn't obviously be bad for my productivity (it might even be good for it!). This is because:

* I'm not very optimistic about my chances of finding the sort of relationship I want. (A lot of this has to do with asymmetries in my cluster of romance space -- see my interpretation of the space of individuals as a sort of metric space.) And I think a poor relationship would be much worse than none at all.

* Removing myself would heal, slightly, some of the asymmetry.

* Pursuing romance takes a lot of energy and involves high emotional risk.

There are a few plausible options for achieving this, if I want to:

* **Meditation & Self Control**: Being able to let go of emotions, remain detached, control what I'm focused on, etc... The most frustrating thing about romantic attraction has been an abnormally low ability to control my thoughts.

* **Environment Hacks**:
  * Multiple (redacted) men have described that interacting with women a lot (eg. by taking yoga) reduces romantic loneliness for them.

* **Drugs**: I generally really dislike the idea of something modifying my cognition, but if I could legally acquire something with sufficiently compelling properties, I might consider it.
  * Some of Fisher's papers suggest that seratonin is linked to the obsessive parts of romantic attraction and that SSRIs might help.
  * (redacted)- was greatly helped by medication after finding the right psychiatrist.
  * (redacted)- describes Adderall as reducing their need to have social interactions and increasing focus. On the other hand, Adderall often increases sex drive.

* **Lobotomy**: It seems plausible that something could be done, and if I reviewed the literature I could probably come up with good guesses as to what. But it seems very very high risk and rather permanent...

Signaling
----------

One important and complicated issues around romantic relationships is the initial signaling that starts them. Expressing romantic interest in someone overtly is a costly action: it can hurt your relationship with them, with other people, make them feel uncomfortable, reduce your social standing, etc. Meanwhile, a positive outcome is fairly unlikely. So, people don't typically directly express romantic interest. Instead there's typically an exchange of increasingly stronger signals between them ("flirting"). This interplay reduces the risk of both parties, but is problematic if you can't read social queues or social skills aren't your strong point.

* Revealing romantic interest is a prisoners dilemma. Both reveal is awesome, neither reveals is sad, one reveals and the other doesn't really sucks.

* Initiating this sort of interaction typically falls to men, I think. Especially when it comes to escalating signals.
  * This seems really unfair.

* One deep concern I have about attempts to signal is making the person I am trying to express interest in uncomfortable or acting in a way that is hurtful to them. 
  * This is especially true in hacking/CS/math/physics communities that suffer from sexism and gender-biases if you're a heterosexual male. And especially hacklab where I am in a position of leadership (albeit very minor). The damage that could be done (awesome female is creeped out and leaves the community) seems to outweigh my interest.
  * There's really 2 separate problems:
  * (1) Making someone uncomfortable/unsafe. This connects directly to the ["schrodinger's rapist"](http://kateharding.net/2009/10/08/guest-blogger-starling-schrodinger%E2%80%99s-rapist-or-a-guy%E2%80%99s-guide-to-approaching-strange-women-without-being-maced/) issue.
  * (2) Re-enforcing or triggering lots of sexist nonsense. (eg. That women are being respected in a community because of sexual/romantic appeal.)
  * H- & D- both think that I'm at no risk of doing this and should stop considering this.
  * subtle back and forth signaling can really help here.
  * Perhaps this has to do with the seeming disproportionate romantic success of people who aren't considerate of other people's feelings? If you aren't taking the risk of hurting them into consideration, signaling is much easier. (Again, this could just be confirmation bias.)

* Disinterest and business are a signal for quality. Conversely, desperation is a really bad signal: seeming desperate for friends or partners is severely unattractive. Use common sense.
  * This really, really complicates things.
  * This seems on net negative.
  * JO- commented that some girls he knew would have rules like not accepting dates for Saturday any later than Wednesday, in order to emulate scarcity.

* H- views this as an important skill (one of many) that one develops on low value relationships so that one is ready for a potentially very good relationship.

* R- in blog describes a bunch of attempts at signaling that I would never have noticed. (How many people have tried to flirt with me and I didn't notice it?)

* D- thinks one can substantially ignore the other persons signaling if they can't understand it, and focus on sending their own signals.
  * I supposes this only works when only one party is socially unskilled.

* It would be really nice if the expected behavior could be less subtle. If we made the signal less costly, less personal, and less subtle, that would be a very positive thing.
  * Technology is a really big opportunity here.

* Reading social signals is hard in general, but it's easy to see if someone is choosing to spend time with you, which is a very strong positive signal, though not differentiated to romance. If you care about both friendship and romance, which one of these it is often doesn't matter.

* If you aren't very socially skilled and bad on picking up on queues, what can you do to avoid subtle signals?
  * Write about this publicly, so that they'll know they need to be less subtle?
  * Provide public information (an OkCupid profile?) so that they can build a better model of you and be more confident that you are of interest to them and that they'd be of interest to you?
  * Make relationship status public (eg. for me on 05/30/2013, single, has never dated) so that potential partner doesn't have to worry about whether there might be an existing relationship?


Altruistic Dating
-----------------

So far, we've mostly considered strategies for maximizing ones romantic success/happiness within ethical constraints (with varying degrees of rigor). But often that's not a very healthy way to look at things. For lots of things, it's useful to think about strategies that maximally help everyone else -- because we care about other people, because it can lead to new solutions, and because in some social circumstances (dating probably isn't one) altruistic behavior is rewarded. There are several interesting, specific problems, but first some general thoughts are in order:

**Free/Efficient Market Perspective**: I'm sure many economists would tell me that I should optimize for my interests try to be the best partner I can be, and do nothing further. The "market" can analyze and find solutions I can't. 

**Optimizing for the benefit of your (potential) partner**:

* Give them as much information about you as possible to make a decision (in a non-creepy, non-ranting way). Possible mechanisms might be a public OkCupid profile, or being really clearly willing to answer (almost) any question.
  * Counter argument: Providing a lot more information and being honest about flaws may just lead to you being rejected, even when you were the best person in the candidate pool, hurting the person you were honest about. People aren't rational, and things like romantic attraction are not conscious decision.


* Introduce them to people you think might be good partners for them.
  * Side benefit: if they still choose you in the end, having had more good alternative options, that bodes well for your future relationship (which means a lower risk of you being hurt in the long run).

* Become a better (potential) partner yourself.
  * Ideas: Communication skills (non violent communication, active listening?), physical attractiveness (work out, optimize dressing, hair cut, etc), domestic skills (especially for males, since it signals that you won't push domestic work onto your partner), cluster specific (eg. math skills).
  * Side benefit: Someone is more likely to pick you, your relationship will likely be better. (If you're seeking a long term relationship like me, then that equates to your relationship having a better life expectancy.)


