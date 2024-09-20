## Definition of a Turing Machine
Informal definition: a TM is a state machine attached to an infinite tape of memory cells; the input is written starting on the left end of the tape, and is followed by infinitely many blank cells. The TM starts on the leftmost cell, in a specially designated "start" state. On each time-step, it reads the memory cell it's currently "on", then based on the symbol written there and the state it's currently in, transitions to a new state, writes something on that memory cell, and then moves one cell left or right on the tape. It either accepts or rejects its input by, at any time, entering special "accept" or "reject" state, at which point it halts. Unlike a FSA, a TM may or may not ever finish computing. 

Formal definition: TM has 7 parts: an input alphabet $\Sigma$ which does not include the blank symbol, a tape alphabet $\Gamma$ which includes all the symbols in $\Sigma$, the blank symbol, and possibly others; a set of states Q; a designated start state, accept state, and reject state; and a transition function $\delta$:  (Q x $\Gamma$ ) -> (Q x $\Gamma$ x {L, R}) (which maps state-symbol pairs to states, symbols, and movements left or right.)

Subtleties about the definition: 
The tape alphabet must include all of the input alphabet and the blank symbol, but may also include any (finite) number of other symbols. For instance, the tape alphabet can include all of the input alphabet plus each symbol in the input alphabet but with a dot above it; this is useful for allowing the TM to mark places that it will return to later. Adding other special symbols that show up in the tape alphabet but not the input alphabet can allow for other functions. For instance, some definitions of TMs allow blank symbols in the input, but this makes it not really possible for a TM to erase all of its input--how would it know when to stop? However, one can simulate the effect of such an erasure as follows: on starting, erase what's on the first square immediately to the right of the first square, place a special delimiter symbol representing the right end of the section of the tape that the TM has used before. Then, when running, if the transition function ever calls for moving onto the delimiter symbol, erase it, move it one square to the right, and then go on computing as before. This means that the TM will never interact with what was originally on the tape except to erase it and replace it with the delimiter symbol, allowing it to act as though it was started on a blank tape, but it will also never get stuck in the potentially-infinite process of trying to erase everyhing.
A TM as typically defined has a definite "left end" to the tape; if it ever tries to move its head off the left end, it just stays put. (This is the only way in which a TM can be on the same memory cell on two consecutive steps.) 
## A TM's Computation; Recognizable and Decidable Languages
Informally, a TM accepts or rejects an input if, after following valid transitions starting with only that input on its tape, it ends up in an accept or reject state. (More formally, one defines a sequence of "configurations" which include what state the TM is in, what is on its tape, and what tape cell the TM is on, and say that a TM accepts or rejects its input if there is some sequence of configurations, starting with the input and ending with the TM in an accept or reject state, such that for every configuration, the next configuration in the sequence is the one given by the transition function on the previous configuration.) It halts if it either accepts or rejects its input, and "loops" otherwise (here "loop" need not imply any kind of periodic behavior, just failing to halt). 

Unlike other models of computation, where one simply speaks of the language accepted by a given automaton, with TMs, one distinguishes between languages *recognized* and *decided* by some TM. A language is Turing-recognizable if there is some TM which accepts all and only the strings in that language, and rejects or loops on all other strings; it is decidable if there is some TM which acepts all and only the strings in the language and rejects all others (and thus always halts.) In other words, a Turing-recognizable language is one where some TM always correctly "recognizes" a string from that language as being in the language when it sees one, but may not be able to identify strings not in the language as not being in the language (i.e. it may loop on such strings, but it must never accept such a string); a decidable language is one where some TM can always correctly decide whether a string is or isn't in the language.

A language is co-Turing-recognizable if its complement is Turing-recognizable. A language is decidable iff it is Turing-recognizable and co-Turing-recognizable. Proof: if a language is decidable, then the TM that decides it is already a recognizer for both the language and its complement. If a language is recognizable and co-recognizable, then it has TMs M1 and M2 which recognize it and its complement, respectively. One can then decide the language by creating a multitape machine which simultaneously simulates M1 on one tape and M2 on the other (which must have the input copied to it before starting execution), accepting if M1 accepts and rejecting if M2 accepts. It is important that the recognizers are simulated in parallel, as opposed to sequentially, so that the decider always halts; if the decider tried to simulate one and then the other, then the first one might fail to halt on the given input. 

Most "natural" or "reasonable" languages/computational problems are decidable. The classic example of a language which is recognizable but not decidable is the set of all TM-input pairs that the TM halts on the given input. Some languages are neither recognizable nor co-recognizable; see for example the set of all pairs of TMs such that the two TMs recognize the same language.  
## Equivalence with other models of computation and TM variants
While other models of computation have the power to emulate or act like others (in the sense that, for instance, given a specific NFA, one can make a DFA which accepts the same language by to some extent simulating it), TMs have the power to emulate a wide variety of other models and to act as general-purpose simulators (in the sense that there is a "universal Turing machine" which can accept arbitrary TM descriptions as input and then run them; more generally, TMs can run other TMs as "subroutines" or to answer questions about those TMs). One result of this is that TMs are "robust"--changing the definition, even quite drastically, generally leads to machines which can recognize/decide at most the same class of languages as regular TMs. For example:
### Multitape Turing Machines
A multitape TM has some finite number of tapes with a head on each one; the input starts out written on one tape, while the others start out empty. On each step, it reads in characters from each tape and changes state, writes to any number of its tapes, and moves left, stays put, or moves right on all of its tapes. (Aside: adding a "stay put" option to single-tape TMs doesn't change which languages they recognize, since a "stay put" can always be simulated by moving right, then left.) More formally, a multitape TM's transition function is of the form (Q x $\Gamma^k$ ) -> (Q x $\Gamma^k$ x {L, S, R}<sup>k</sup>), where k is the number of tapes. 

Multitape TMs are equivalent to single-tape TMs, in the sense that a language recognized/decided by one is also recognized/decided by the other. Proof (for the "recognizes" case; the "decides" case is essentially the same): A single-tape TM is automatically a multi-tape TM (with k = 1), so MTMs recognize the Turing-recognizable languages. For the other direction, one can simulate a MTM on a single tape as follows: the simulating TM has the same tape alphabet as the MTM, plus a "tape end" symbol like # and dotted versions of all the other symbols. The non-blank portions of the MTM's tapes are laid out in sequence on the TM's tape, with dots above the locations of the MTM's heads. (For example, a 3-tape TM starting on input abc would be represented as "(a-dot)bc#blank-dot#blank-dot", where "x-dot" means the symbol x with a dot on top.) To simulate a step of the MTM's transition function, the TM first scans across the tape to see which symbols each simulated head is over, then computes the transition function for that combination of symbols and state, then goes back over to update the tape accordingly. If a simulated head ever moves into the blank portion of the tape, the TM deals with that by shifting everything to the right of that memory cell one cell right, then putting a dotted blank in the newly clear area (to represent the MTM's head over a blank cell). 
### Nondeterministic Turing Machines
A nondeterministic Turing machine is a TM whose transition function maps to sets of ordered triples of the form (state, symbol, left or right), as opposed to single ordered triples. (Unlike in the definition of an NFA, there are no "epsilon-moves".) As with nondeterministic machines in general, an NTM's computation can be thought of in terms of a "tree" of choices: every node represents a configuration of the TM, and the branches coming from that node represent each of the triples in the set to which the transition function maps that configuration. An NTM accepts its input if it accepts on at least one branch, and is called a "decider" if all branches are finite (i.e. going far enough down any branch of the tree always results in accepting or rejecting).

As with DFAs and NFAs, a language recognized/decided by an NTM is also recognized/decided by a TM. Proof: the basic idea is to do breadth-first search on the NTM's computation tree. (Depth-first search may run into an infinite branch, so the simulating TM will fail to halt even when the NTM accepts on some branch.) First, consider the case where some NTM N recognizes a language. A 3-tape TM M can be designed to simulate N as follows: one tape always holds the input, the second is used to simulate the NTM, and the third is an "address" tape on which the TM iterates through all possible finite sequences of choices made by the NTM, simulating each of them on the second tape. In order for the address tape to work, the simulating TM needs to have symbols added to its tape alphabet: one for every natural number 1 through k, where k is the maximum number of choices available to the NTM at a given time-step. An address tape like "413" means "on the first time-step, make the 4th available choice, then on the 2nd step, the 1st available choice, then on the 3rd step, the 3rd choice". The simulating TM repeats the following loop: update the address tape to be the next string (in the standard string order) over the alphabet of natural numbers 1 through k. Copy the input from tape 1 onto tape 2. Then begin simulating the NTM on tape 2 according to the steps specified by the address tape. If the NTM accepts, accept and halt. If it rejects, the address tape has an invalid address (e.g. saying "make choice 4 on step 1" when there are only 3 choices available on step 1), or the NTM otherwise makes all the choices on the address tape without accepting, then go back to the start: update the address tape, initialize tape 2 to be the input, and then simulate again.

This is a rather inefficient simulation, involving a lot of redundancy (e.g. simulating the first n steps of a branch, then eventually going back to the start and simulating the first n + 1, and so on), but it does work. If the NTM accepts, then the TM will accept: the address tape will eventually show a sequence of choices that leads to accepting, and the TM will run that sequence of choices and accept it. If it doesn't, then the TM may run forever. Only when the NTM is a decider can the simulating TM decide (not just recognize) the same language. (This is because, when the NTM is a decider, each of the (always finitely many) branches coming out from a particular node in the tree has finitely many nodes below it (since all of the "child" branches end in accepting or rejecting), so the tree as a whole has finitely many nodes, and it's possible for the TM to explore all of them). Basically, the simulation proceeds as in the "recognizer" case, with this difference: if the NTM rejects its input, then it will reject on all branches; say that the longest rejecting branch has length n. Then all address strings of length n specify either an invalid branch or a branch that ends in rejection. So, whenever the TM goes through all address strings of a certain length, it should keep track of whether any of them are neither invalid nor end in rejection. If this isn't the case, the TM has determined that all of the NTM's branches end in rejection, so it should reject its input.
### Enumerators
An "enumerator" is a TM with an attached "printer", on which it outputs strings over its tape alphabet. It has no input; instead, it has an infinite work tape which starts out blank. One can prove that these are basically equivalent to TMs--the languages enumerated by some enumerator are precisely those recognized by some TM, while the languages enumerated by some enumerator in the standard string order are equivalent to those decided by some TM.

Proof: for the "recognized" case, for the first direction, let E be an enumerator enumerating language L. Then a TM can recognize L by simulating the enumerator and waiting to see if its input shows up in the enumerator's output; if so, it accepts, and if not, it just runs forever. For the other direction, given a TM M recognizing language L, one would like to have the enumerator run through all possible strings over the relevant alphabet and use M to "filter" them for strings actually in the language, but the naive way of doing this won't work, as the TM might run forever on some input, in which case the enumerator will never have a chance to print some strings. Instead, what the enumerator should do is: first take all the strings of length <= 1, and run M on them for 1 step each; then take all the strings of length <= 2, and run M on them for 2 steps each; and so on. Since the TM is only simulated for finitely many steps at a time, the enumerator will never actually see it run forever; but if it does accept some string (say in k steps) then the enumerator will print that string when it is running M on all strings of length <= k for k steps. So each accepted string will show up in the enumerator's output at some point.

For the "decided" case, for one direction, the "naive" algorithm actually works: given a TM M recognizing the language L, have an enumerator go over all strings in standard order, run M on each of them, and print or don't print if M accepts or rejects. This way, all strings in the language will show up in standard order. The other direction is trickier: given an enumerator E enumerating L in standard order, have the TM simulate E until its input shows up (in which case, the TM accepts) or E prints a string which comes after its input in the standard order (in which case, E has gone over the input without printing it, so it must not be in the language, so the TM should reject). This works for infinite languages, but not for finite languages, where E may not ever print a string which comes after the TM's input, and E may continue running after it's printed all the strings (in which case the TM will keep waiting forever). However, all finite languages are decidable, so the language is decidable either way.
### 2-PDAs
While TMs are stronger than ordinary, 1-stack PDAs, a "2-PDA" with 2 stacks can simulate a TM--just have one stack represent all the nonempty squares to the left of the TM, one represent all the nonempty squares to the right, and handle writing and left/right moves by popping from one stack and pushing to the other. Since a TM can simulate a PDA with any number of stacks, and a 2-PDA can simulate a TM, adding even more stacks to a PDA doesn't give it any more computational power: any language decided by a k-PDA with k > 2 can also be decided by a 2-PDA simulating a TM simulating a k-PDA. 
## Comparison to weaker models of computation
Unlike FSAs, TMs have infinite memory; unlike PDAs, they are able to access anything in memory without "forgetting" things that they added more recently. This gives them more power than these models: for instance, they can recognize languages like {a<sup>n</sup>b<sup>n</sup>c<sup>n</sup>|n $\in$ N} which are neither regular nor context-free. In fact, all regular and context-free languages are decidable. Furthermore, the problems of testing whether an arbitrary DFA or PDA accepts some string are also decidable: see the relevant pages for more. Summary of results on the decidability of problems related to regular and context-free languages: for DFAs, it is decidable to test whether a DFA accepts a particular string, whether a DFA accepts no strings or infinitely many strings, whether two DFAs accept the same language, and whether a regex generates a particular string, among other problems. For CFLs (and thus CFGs and PDAs), acceptance testing and emptiness testing are decidable, but equivalence testing is not. Also, for LBAs (linear bounded automata: TMs which can write only on the part of the tape containing the input) acceptance testing is decidable while emptiness and equivalence testing aren't. 
