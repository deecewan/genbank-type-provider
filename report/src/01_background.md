# Introduction

Bio-informatics is an increasingly important field, and its very nature produces
an extraordinarily large amount of data. Management and usage of this data
becomes critical in order to achieve anything meaningful with it
[@lee_bioinformatics_2012].

Being able to access this vast dataset in a simple, programmatic way will
improve the way that researchers are able to discover and present findings.
This paper aims to outline the methodology and research of a type provider for
the F# programming language in order to more efficiently access and manipulate
data, with the eventual aim of releasing a tool for the community to use.

The primary focus of the research in it's initial stages is GenBank format data
- it is a huge dataset in the genetic informatic field, and there is some
  foundational work already completed in the space.

## Literature Review

### Bioinformatics

Also known as computational biology, genetic informatics and systems biology,
bioinformatics is the field of study that combines biologic data with software
for analysis, storage and distribution [@lesk_arthur_m._bioinformatics_2013].

// TODO: More info in here

### Type Inference + Type Safety

Type safety is a critical component of many programming languages to ensure
correctness of the programs being written.  The power and sophistication of type
systems are able to transform a language, and make it easier to communicate
one's intentions - both to the compiler and any future readers
[@cardelli_typeful_1989]. @cardelli_typeful_1989 goes on to explain that type
systems adapt equally as well to all programming paradigms, including functional
- the main subject of this paper in the form of F#.

Type inference takes this one step further.
@duggan_explaining_1996 explains this this process as a compile-time
reconstruction of missing type information by analysing the usage of variables
within the program.  This affordance gives programmers a high degree of safety
with less additional programming required.

To take this one step further, @hutchison_type_2006 go into depth around type
inference with specific regard to systems biology. Whilst looking at a different
programming language and data set (Systems Biology Markup Language and BIOCHAM),
it resolves to show that analysing biochemical models using type inference
provides 'accurate and useful information'.

Things to talk about:

- compiler extensions
- first class data
- data management + access
- genbank


## Research Problem

### Research Statement

The objective of the research is to create a compiler extension in the form of
an F# type provider to enable the quick exploration and use of data. This allows
the data to become a first-class citizen of the programming language to make it
easier to access data from GenBank and build out programs using bioinformatics
data.

- builds on the type provider made by Jess
- initially involves bringing the current type provider up to standard
- subsequently, abstract out the functionality to allow for more generic data
  sources
  - genbank is a popular data format already in use
  - can be abstracted to other data types in the future (?)

The goal is to have a type provider released to the community that is usable and
useful.

### Research Questions

- How can we simplify programmatic access to large bioinformatic datasets?
