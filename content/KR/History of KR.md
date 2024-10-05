+++
title = 'History of KR'
date = 2024-10-05T12:08:51+02:00
draft = false
math = true 
+++

History is deeply connected with recording techniques such as writing or oral traditions (humans always felt the need to transmit knowledge, `this was done trough myths, stories, etc.)

Oral and written traditions preserve and propagate knowledge
traditions hardly resist the test of time, their meaning easily change, and they're also very hard to update, the language could also result ambiguous
Our goal is to represent knowledge with guarantees without the need of Trained Interpreters (like in religious text)

# Aristotle Syllogism Calculus

Aristotle was the first to study how to make valid inferences, handling knowledge about classes
Aristotle used ==4 types of relations==
- A: Every X is a Y `Every human is a mortal`
- E: Some X are Y `Some humans are vegetarians`
- I: No X is a Y `No humans are immortal`
- O: Some X are not Y  `Some humans aren't athletes

A Syllogism is a derivation rule used to extract consequences form sentences

- bArbArA: every X is a Y, every Y is a Z so every X is a Z 
- fErIO: Some X are Y,  no Y is a Z, some X are not Z
- cElArEnt
- dArII

==Derivation Rules are __Sound__, meaning if the input are true then the output is also gonna be true, and __Complete__, meaning that applying all Syllogism derives all the knowledge expressible

Aristotle syllogism calculus is limited
- Only 2 classes at a time
- No disjunctions
- No relationship between objects inside of the Class `You could speak about mothers, but not about Ana specifically`
# After Aristotle
logic was mostly seen as the study of syllogism and was mainly used for discussion about arguments.
Slowly logic started being used for science / philosophy

More recently Boole started studying an algebra based on truth values (Either true or false)
==Propositional Logic== (Simple language to describe general properties), which was later extended to ==Predicate Logic== (Introduction of quantification, functions and relations)

Propositional Logic was seen as too inexpressive, while Predicate Logic as too complex --> Logic tries to find the right balance between the two

# Era of AI

Intelligent Agents / Systems: An intelligent Agents needs to be able to "understand" what is going on around it by inferring implicit information and actions `Some elements are fixed while other may change`
 To obtain an Intelligent Agents we need
 - a Machine readable language, used to represent knowledge
 - a formal finite inference mechanism
 - an interrogation language (Query language), used to interface with the agent ("In some cases, `Language models for example`, the query language can be Human Language")

## Semantic Networks
Graphs with connecting properties
[![WHAT IS SEMANTIC NET? GIVE EXAMPLE. | by Rashandeep singh | Medium](https://miro.medium.com/v2/resize:fit:860/1*QLMg5uUoI9wsoyLCGXBXSA.png)
- No Formal Semantics (`Frog HasColor Green` can be interpreted in different ways)

## Frames
Blocks with open "windows to fill in specific properties", kinda like OOP and Classes

Animal "Class" with different traits (Color, Number of Legs, etc.)
Specific animals are different instances of the given properties
`eg. Chicken animal "Class" has Color = white and Number of legs = 2`

## Logic Based KR
Development of languages with clear syntax and formal semantics used to represent knowledge and reasoning automatically

At the beginning propositional logic was used in conjunction with predicate logic for more advanced settings (Not a very efficient solution)

To solve this problem DL's started being developed (Description Logics)

- Based on some fragments of predicate logic
- Trade-off between expressivity ad computational properties

## Semantic Web
Allowing machines to ==navigate== and ==understand== the web in the same way as ourselves through Machine Readable annotations
- Bottlenecked by the need of adding Machine Readable annotations to every single web page
A big chunk of the internet is still accessible trough the Semantic Web

## Knowledge Graphs
Google Started talking about it in 2012 in relation to AI applications

# Curse of Reality
Keep in mind reality isn't as logical as we want it to be
Dealing with real knowledge means dealing with 
- Measures
- Time
- Uncertainty
- Vagueness
- Regulations (Law and Rules)
Its impossible to create a perfect Dl for everything but we need to create ad Hoc solutions