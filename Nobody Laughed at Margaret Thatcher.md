# Nobody Laughed at Margaret Thatcher

*Four decades of Hansard, a graphics card, and some things about the House of Commons that nobody has counted before*

Oct 9, 2026 · @Trevor Dwyer

On 16 January 1986, the official report of the United Kingdom Parliament recorded the Prime Minister as **Mr.** Margaret Thatcher.

That typo has been sitting in the public record for forty years. I found it at eleven o'clock at night, and it is not even the most interesting thing I found.

I have spent the last month with every word spoken in the House of Commons since 1979 — 1.7 million speeches, about 160 million words — loaded into a database, with a graphics card doing the parts a database cannot. I went in looking for something quite specific and did not find it. What I found instead was a set of things about that chamber that, as far as I can establish, nobody has ever counted.

The House of Commons has quietly stopped using its own interruption protocol. Being a minister makes you *more* likely to be shouted at, not less. Eighty-five per cent of every six consecutive words spoken in there since 1979 was spoken exactly once and never again. A Conservative MP read Tony Benn's five questions into the Queen's Speech debate of 2019, with the Hansard column reference attached.

And nobody laughed at Margaret Thatcher. I mean that as a measurement.

## How, briefly

Hansard is the official report of everything said in the Commons. The version I used runs from 1979, and once you drop the fragments — "I beg to move", "The Question is" — it comes to 1,700,647 speeches. Every one carries a speaker, a party, a date, a debate, and whether they held office. That last part is what makes it worth doing: every question you can ask about the words, you can also ask about who said them and from which side of the room.

The graphics card reads all 1.7 million speeches and works out which ones are about similar things, sorting them into 41,730 topical neighbourhoods. This is forty rounds of arithmetic on a 1.7-million-row matrix. On a processor it is a long lunch; on a GPU it is ninety seconds, because it is exactly the shape of sum a GPU exists for.

The database does everything else: storing it, indexing it so a question only ever reads the relevant slice, and — the part people forget — joining it to who said it. Neither half can do the other's job. The card cannot remember anything and has no idea what a Conservative is. The database cannot do the arithmetic that works out where the neighbourhoods are.

The card draws the map. The database reads it. There is no code in this article; if you want the SQL, it is in the long version at the bottom.

## The House has stopped giving way

"Will the hon. Gentleman give way?" is the Commons' interrupt protocol — the formal, courteous mechanism by which one member takes the floor from another mid-speech. It is the single most recognisable thing about British parliamentary debate.

Hansard records it, along with interruption, laughter and "Hear, hear". So you can count it.

| Decade | Gave way | Interrupted | Laughter | "Hear, hear" |
| --- | --- | --- | --- | --- |
| 1979 | 1.270% | 1.315% | 0.316% | 0.136% |
| 1980s | 1.734% | 2.692% | 0.385% | 0.152% |
| 1990s | **1.801%** | 2.867% | 0.784% | 0.175% |
| 2000s | 1.189% | 3.342% | 0.619% | 0.105% |
| 2010s | 0.919% | 2.667% | 0.447% | 0.091% |
| 2020s | **0.362%** | 1.851% | 0.367% | 0.079% |

Giving way peaked at 1.80% of speeches in the 1990s. It now runs at 0.36%. **A five-fold collapse.**

The obvious explanation is the pandemic — you cannot intervene on somebody appearing by video link. But look at the 2010s. Already at 0.919%, half the 1990s rate, years before anyone had heard of hybrid proceedings. Covid finished it off; it did not start it.

"Hear, hear" has halved over the same period. Interruption, meanwhile, peaked in the 2000s and still runs at roughly its 1980s level.

So the chamber still gets shouted at. It has simply stopped *negotiating* interruption. The formal exchange is dying while the informal noise carries on — speeches written for the clip rather than the room, by people with no intention of letting anybody in.

### Office is a target, not a shield

|  | Speeches | Laughed at | Interrupted |
| --- | --- | --- | --- |
| Backbencher | 1,565,532 | 0.530% | 2.738% |
| Minister | 47,537 | 0.684% | **4.222%** |

A minister at the despatch box is interrupted **54% more often** than a backbencher, and laughed at 29% more. I had assumed the dignity of office bought a bit of quiet. It buys the opposite.

And the most-interrupted individuals are Kinnock, Blackford, Miliband, Osborne, Blair, Starmer, Corbyn, Prescott and Benn. That is not an irritation ranking. It is a prominence ranking — the people at the despatch box in prime time with the whole other side watching.

Being interrupted a lot means you were worth interrupting.

## Nobody laughed at Margaret Thatcher

I went looking for her about halfway through, expecting her to be everywhere. I could not find her, which turned out to be the answer.

Hansard files prime ministers under their job. "The Prime Minister" appears roughly 18,046 times between 1979 and 2001; Thatcher under any version of her own name appears 410 times. She is in the record **twenty-four times more often as a job title than as a person**, and every analysis anybody has ever run on this dataset by speaker name has quietly ignored her.

When she does get a name, it is rarely the same one twice. Nine spellings, most differing by a stray apostrophe, a misplaced full stop, a missing bracket — and one, on 16 January 1986, that made her Mr. Margaret Thatcher.

Resolve the office to the holder by date and you can finally ask the question nobody has been able to put to the record: which prime minister did the House shout at most?

|  | Speeches | Interrupted | Laughed at | Avg words |
| --- | --- | --- | --- | --- |
| Blair (1997–2001) | 3,547 | **7.75%** | **1.015%** | 147.1 |
| Thatcher | 9,782 | 6.35% | **0.174%** | **104.2** |
| Major | 5,303 | 5.98% | 0.811% | 120.8 |

Raw, she draws a fifth of Blair's laughter. But the House laughed more in the nineties than the eighties generally, so measured against each era's own baseline:

- **Thatcher: 0.45× her era's laughter rate**
- Major: 1.03×. Exactly average.
- **Blair: 1.29× his**

Even correcting for the period, the Commons laughed at Thatcher **less than half as much** as it laughed at everyone else at the time — while interrupting her more than it interrupted Major. Shouted at, not laughed at. And she said it in short bursts: 104 words a speech against Blair's 147.

### The order paper

There is a story that belongs next to that number.

Christopher Hitchens — a man of the left who had been publicly and expensively rude about her in print — met Thatcher at a reception in the late seventies, when she was still Leader of the Opposition. They argued about Rhodesia. He lost. Having lost, he bowed to her.

She told him that was not low enough. He bowed again, properly this time. And as she swept past she caught him across the backside with a rolled-up parliamentary order paper and said, *"Naughty boy."*

Hitchens then wrote, in print, about the frankly confusing effect this had on him.

Put that next to the figures above. The House laughed at her less than half as much as it laughed at anybody else of her era — and the most repeated personal anecdote about her is one in which she makes a hostile left-wing journalist look ridiculous, physically, with a procedural document, in under ten seconds.

I think those are the same fact.

## A Conservative quoted Tony Benn

The thing I actually set out to find was whether MPs ever change each other's minds — specifically, whether an argument made from the opposition benches ever ends up coming out of a minister's mouth.

I built two elaborate methods to detect it and both said no. Then I went looking for Tony Benn, because I admire the man and always have, and found this:

> **Lee Rowley (Conservative), 14 October 2019, Debate on the Address**
>
> *"What power have you got? Where did you get it from? In whose interests do you exercise it? To whom are you accountable? And how can we get rid of you?"*
>
> — \[Official Report, 22 March 2001; Vol. 365, c. 510.\]
>
> *"I hope we remember that in the days ahead."*

A Conservative MP. In the Queen's Speech debate. At the height of the Brexit crisis. Reading a hard-left Labour backbencher's words into the record **with the column reference attached**, citing a speech Benn gave eighteen years earlier. Rowley sits for North East Derbyshire, which wraps around Benn's Chesterfield.

He is not alone. Clive Lewis used the whole structure against academy trusts in 2015 — not quoting it, wielding it. Toby Perkins, the sitting member for Chesterfield, read the questions out on 20 March 2014, six days after Benn died.

That is a formulation coined on the opposition benches, crossing the floor, and arriving in a government MP's mouth eighteen years later. It is precisely the thing both my methods were built to find and both of them missed, for a reason I will come back to.

### Two more, briefly

**Eighty-five per cent of everything said in the Commons was said once.** There are 375,802,591 six-word sequences in forty years of Hansard, and 319,572,719 of them are distinct. For an institution with a reputation for repeating itself, that is a startling amount of novelty.

**And one phrase turned round and came back.** Margaret Thatcher said *"at the end of the transition"* in June 1979, about Britain's arrangements on **joining** the European Community. Its last use in the corpus is forty-one years and eight months later, about Britain **leaving** it. Seven in ten of its 132 uses fall in a single year, and that year is 2020. The phrase lay nearly dormant for four decades and then detonated.

## The one I nearly got wrong

I should tell you about a finding that is not in this article, because it is the most useful thing that happened.

**Television cameras entered the Commons in November 1989** — ten years into a forty-two year dataset. If knowing you will be on News at Ten makes you craft one line and repeat it, you should be able to see that in the text. So I took every MP with speeches on both sides of that date, 790 of them, and measured each one against themselves, before and after.

I got a result. Small, but there, and in a direction I could have written a paragraph about.

Then I ran the identical test against 1984, a year on which nothing whatsoever happened. **It produced three times the effect.** And 1994 produced almost none.

The answer was sitting in the shape of it: watch somebody for five years and you catch them on fewer subjects than if you watch them for fifteen. I had not measured television. I had measured **how long I was looking**.

That is why Benn's five questions defeated both of my clever methods, incidentally. He never said them the same way twice — "what power have you got" in 1990, "what power do you have" in 1991, "where did you get it from" by 2001 — and an exact phrase-matching method cannot see a formulation that mutates. The only language repeated word-for-word in Parliament is language nobody is choosing their words for. Procedural boilerplate. Petitions read verbatim.

Real rhetoric moves. That is what makes it rhetoric.

---

## The long version

This is the short one. The full account — the SQL, the GPU code, the eight separate bugs including the one that proved every Member of Parliament is funny one hundred per cent of the time, and the dachshund who serves as my technical review process — is here:

**Two Graphics Cards and 1.7 Million Speeches to Prove a Negative**

All the code is on GitHub: **[github.com/sqlartist/…](https://github.com/sqlartist)** *(link to follow)*

Every number above is checkable. Hansard is public, the dataset is public, and if you think I have got any of it wrong I would genuinely like to know, because on the evidence of the last month there is a reasonable chance that I have.
