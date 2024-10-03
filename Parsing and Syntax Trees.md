# Parsing and Grammars
Once we've tokenized code (the "word-level" structure), we still need to figure out the "sentence-level" structure. This is the job of syntax analysis/parsing. 

Typically the structure of a statement in a programming language is represented hierarchically as an "abstract syntax tree". The highest "level" may be something like the general type of the statement--conditional, assignment, etc.--and lower levels of the tree break it down more finely, with leaves usually being individual pieces of data (identifiers, literals, etc). Intermediate nodes process things at lower levels and send up some kind of result to higher levels. For example, a statement like "if (x == 0) x = 10" may get broken down like: Conditional(equals(x, 0), assignment(x, 10)). 

As an important part of all this, we need some way to figure out whether a statement is grammatically correct. This generally cannot be done with regular expressions; for example, checking whether parentheses are balanced cannot be done with a regular expression. Instead, the standard tool is a context-free grammar.
## Context-Free Grammars
### Definition of a Context-Free Grammar
The rules of a context-free grammar, written in "Backus-Naur form", consist of he following components: "terminal symbols" (tokens or the empty-string symbol $\epsilon$ --think the "leaves" of the parse tree); "nonterminal symbols" (variables representing statements); a distinguished "start symbol" (one of the nonterminal symbols); and "production rules" of the form "this -> that". The "this" on the left-hand side consists of a single nonterminal symbol, and the "that" on the right consists of any string of terminals and nonterminals. The set of all strings which can be formed by applying these rules, starting with just the start symbol, is the "language" of the grammar. 

As an useful shorthand we can consider "or"s using the vertical bar: this -> that | something else.
### Examples
For example, using S as the start symbol, and using the convention that capital letters represent nonterminals and lowercase letters represent terminals: "S -> aSa, S->T, T->bSb, T->$\epsilon$" is a grammar, which generates all possible palindromes made of a's and b's, plus the empty string.

We can also consider a language for generating strings of balanced parentheses, with rules S -> (S)S and S->$\epsilon$. Note that here is an example of using a context-free grammar to express *recursive* definitions of a language: a string of balanced parentheses is either: the empty string; a balanced string surrounded by an open and closed parenthesis, (S); or a balanced string next to a balanced string, (S)S. 
### Derivations and Syntax Analysis
Given any string accepted by a grammar, we know there's some sequence of steps (applications of rules) that produces that string. For example, the string (())() has the derivation: S -> (S)S -> ((S)S)S -> (()S)S -> (())(S)S -> (())()S -> (())(); at each step we either expand an S according to the first rule or replace it with the empty string. This then leads to two important computational problems: given a string and a language, test whether that language accepts the string; and given an accepted string, find a derivation for that string from the grammar. A *parser* is a program which tests whether a string is accepted by a language, and a *syntax analyzer* is a parser that can also output derivations. 
## Issues: Associativity, Ambiguity, and Precedence
In many common cases (e.g. mathematical expressions) we want to write without parentheses while still having a clear, unambiguous convention for what parts of an expression get evaluated first. For example, $2 - 1 + 1$ could plausibly be interpreted as $2 - (1 + 1)$ or $(2 - 1) + 1$, which evaluate to different things, but we take the convention that this should equal $(2 - 1) + 1$--when dealing with addition and subtraction, expressions are "left-associative". A naive way of writing a grammar for mathematical expressions--for example, allowing an "Expr" token to be expanded as "Expr Op Expr"--would lead to this ambiguity. We can fix this by replacing the rule "Expr -> Expr Op Expr" with a rule like "Expr -> Expr Op Num", i.e. require the right argument to be a constant and not another expression. When evaluating the resulting tree, we'll evaluate whatever is under the "Expr" on the left before we apply "Op" to it and the term on the right. (As a general rule, expressions lower in the parse tree get evaluated before those higher on the parse tree.)

We also may want to break left-associativity in cases where we want to enforce the precedence of one operator over the other. For example, 2 - 1 x 1 should be interpreted as $2 - (1 * 1)$. So the simple rule "Expr -> Expr Op Num" should be replaced with multiple rules, like:
Start -> Expr2
Expr2 -> Expr2 AddOp Expr1
Expr2 -> Expr1
Expr1 -> Expr1 MulOp Num
Expr1 -> Num

Here we force Expr1 expressions to be higher priority than Expr2 expressions by making it so that a string "Expr AddOp Expr" can have MulOp expressions as children, but not the other way around. Thus the MulOp expressions will (in the absence of parentheses, which need their own rules) get evaluated before AddOp expressions. More generally, we add nonterminal symbols for each "level" of precedence, and at each level, we can decide between left-associativity and right-associativity by choosing where to place the nonterminal for the next-lowest level. 

Thus for instance the rule Expr2 -> Expr2 AddOp Expr1 forces the parser to "recurse on the left", making Expr2 operators left-associative. If we instead did Expr2 -> Expr1 AddOp Expr2  they would be right-associative. Left associativity is typical, but we do sometimes need right-associativity, for instance in assignment operators (x = y = 1 should be interpreted as x = (y = 1) in order to set both x and y equal to 1) and exponentiation (conventionally a ^ b ^ c = $a^{(b^c)}$). We may also want non-associative operators, in the sense that you can't use the operator in the form "a op b op c" without parentheses: for example, in many languages "a < b < c" gives a syntax error. Non-associative operators would be implemented in a grammar by only allowing rules like "Expr2 -> Expr1 Op Expr1", where both sides have the next-lowest level of priority. 
# Parsing Algorithms
The simplest parsing algorithm is the brute-force method of "recursive descent"--try the first non-terminal symbol, go to the next token if it succeeds, try another if it fails, and if all possibilities fail for the current token, backtrack to the last token and try a different option there. This is slow and can, in some cases, lead to infinite loops. 

We can instead try to make our grammar "unambiguous" in the sense that any token only has one possible nonterminal corresponding to it. 

Take for example the following grammar for writing out addition expressions like 1 + (2 + 3) + 4:

S -> E + S | E 
E -> num | (S)

When trying to derive the string (1) + 2, for example, the only derivation starts S -> E + S, but there's no immediately obvious way for the parser to "know" that. A recursive-descent parser might waste time trying to apply the rule S -> E--we need to know what comes later on in the expression to know what rule to apply at the start. . 

On the other hand, if we've just parsed a token as E, there's no problem: either the next token is a number or an open parenthesis, or else there's an error. 

But the situation with S isn't as bad as it may seem. Whenever we expand an S, we get an E as our first new nonterminal in either case. So consider the rules: S -> ES', S' -> +S | $\epsilon$. Now when we encounter an $S$ there's only a single rule to apply, and when we encounter an $S'$, which rule we apply depends only on the next part of the string (whether it's a + or the empty string).

.....
.....
.....

# Abstract Syntax Trees
A "full" parse tree will contain lots of redundant information; we can simplify it into an "abstract syntax tree" that removes much of that. For example, "direct transitions" like A -> B -> x, where A, B are nonterminals and x is a terminal, can be simplified to just x. (On the other hand transitions that lead to "branching" cannot necessarily be simplified like this.) Often characters like parentheses affect how we parse an expression, and would be stored in a full parse tree, but can be discarded in an AST. In fact, we don't need to store the parse tree at all--we can build the AST directly during the parsing process. 

The leaves of an AST can be literals (numbers, strings), variables, calls to functions with no arguments, etc. 