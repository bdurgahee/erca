# Introduction #

The purpose of Formal Concept Analysis or FCA is to automatically find groups of _objects_ (or _entities_) that share in common a group of _attibutes_.

This definition seems a little bit general at first glance, but let see a short exemple to understand it better.

# The Data #

FCA works on a specific type of data: _objects_ described by several _attributes_. Concretely, it takes the shape of a n\*m table with entities as rows and attributes as columns. This table is called a _formal context_.

Here is a sample formal context:

```
|		| jungle	| water		| forest	| fish		| plant		| mamal		|
| lion		| x		|		|		|		|		| x		|
| carp		|		| x		|		| x		|		|		|
| dolphin	|		| x		|		|		|		| x		|
| bear		|		| 		| x		|		|		| x		|
| zebra		| x		|		|		|		|		| x		|
| pine		|		|		| x		|		| x		|		|
```

This formal context has been defined used the Erca syntax. In this formal context the objects are **lion**, **carp**, **dolphin**,... The attributes are characteristics that describe these objects, like **jungle** (as in live in the jungle), **mamal** (is a mamal), ...

# FCA #

FCA is a technique applied on the previously described formal context. It aims at finding groups of objects that share groups of attributes. For instance **({water},{carp,dolphin})** is one of those groups because water describes only carp and dolphin; and carp and dolphin share no other characteristic than water. **({water},{carp,dolphin})** is called a _concept_. Several others concepts can be extracted from this context. For instance **({mamal},{lion,dolphin,bear,zebra})** and **({jungle,mamal},{lion})** are other possible concepts.

From this formal context, the list of all the possible concepts is extracted. These concepts can then be classified. For instance **({mamal},{lion,dolphin,bear,zebra})** is more general than **({jungle,mamal},{lion})** because the second concept covers a subset of the objects of the first one. The classification of all of the concept forms what is called a _concept lattice_. It can be considered as the result of the application of FCA on a formal context.

# The Result #

The following picture presents the whole concept lattice that can be extracted from our sample context:

![http://wiki.erca.googlecode.com/hg/img/animals.jpg](http://wiki.erca.googlecode.com/hg/img/animals.jpg)