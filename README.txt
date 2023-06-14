Leaf is a straightforward Haskell library for regular tree grammars.

Regular tree grammars closely resemble algebraic data types in Haskell:


================================
data Tree = Node Tree Tree | Leaf

T -> Leaf() | Node(T,T)
================================

We can express a non-terminal like T as an infinite set of terms:

===============================
T
Node(Leaf,Leaf)
Node(Node(Leaf,Leaf),Leaf)
...
==============================

What makes regular tree grammars intriguing is their close correspondence to regular grammars, as well as NFA/DFA algorithms. We can utilize algorithms such as union, intersection, and minimization.

I personally find this library useful for defining recursive type structures with strictness and absence information derived from recursive functions. This requires unifying and anti-unifying these recursive terms, which aligns precisely with the operations provided by regular tree grammars.

I'd also like to add that regular tree grammars bear similarities to term-graphs and E-Graphs, although there are some distinctions:

- Basic E-Graphs lack the ability to reason about cycles with identical topology.
- We do not support rewrite rules over tree grammars.
- Our approach relies on a closed world assumption. Introducing new rules at a later stage, as is common in E-Graphs, may invalidate previous minimizations.