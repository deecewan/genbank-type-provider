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

#### Sequencing and Genome Assembly

*Under Construction*

- OSS sequence processing to see what people are doing currently in the space
- biopython/bioperl (falling out of favour)/biojava

#### Genbank

GenBank is a database managed by the National Center for Biotechnology
Information (NCBI, a department of the US government) and currently contains
'publicly available nucelotide sequences for 400,000 species
[@benson_genbank_2018]. Submissions to the database are handled primarily
online, through the BankIt system. New releases of all sequences (a public
update to the database) is made every two months. From the same report delivered
in 2005, @benson_genbank_2005 notes that at this point in time there are only
165,000 species categorised in the database, showing continued growth even into
recent times.

The similarities between different sequences in the GenBank database if one of
the core ways researchers are using bioinformatics to further the general
understanding of biology. [@pertsemlidis_having_2001]. The Basic Local Alignment
Search Tool (BLAST), another product of the NCBI, is a 'sequence similarity
search program', which is one of the most used of such tools available to the
public [@mcginnis_blast:_2004].

@pertsemlidis_having_2001 identifies that sequence comparison falls into one of
three main categories - identity, similarity and homology [^2]. These are
differentiated as follows:

- Identity refers to the repeated occurrence of *the same* nucleotide in the
  same position in aligned sequences

- Similarity looks only at approximate matches, and is only a useful measure of
  'relativeness' between them and not an absolute scoring.

- Homology is a statement of *sameness* not just of the 2 sequences in question,
  but of all their ancestor sequences back to a common ancestor of the two.

[^2]: These are, according to @pertsemlidis_having_2001, often used
interchangeably, but have in fact quite different meanings.

Given the large amount of data present, and the range of the datasets available,
we now turn out attention to methodologies that may be employed used in
management.

### Type Providers

Type providers are a special case of the more broad 'compiler extension'. A type
provider is specifically a compiler extension with the express purpose of
generating types based on external data for the F# compiler.

There are two types of Type Provider - Generative and Erased. A generative
provider produces types that are able to be compiled into a targeted assembly
for use in other programs. This requires a data source that can be represented
using types from the .NET family.

An erasing type provider, on the other hand, is one that can only be consumed
from the project they were generated from. They are ephemeral and cannot be
consumed by any other program or library. This type provider is special because
it introduces the concept of *delayed members*. A delayed member allows
providing types from an 'infinite' [^1] information space. This is useful for
accessing and handling a small subset of data from a much larger one
[@carter_type_2018].

[^1]: It should be noted that it is, of course, not possible to process an
infinite information space. The meaning in this case is that the compiler will
not limit the size of the space - a computer's available memory does.

A type provider instils a far greater trust by the programmer in the program,
due to type safety.

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

To bring this closer to the scope of this paper, @hutchison_type_2006 go into
depth around type inference with specific regard to systems biology. Whilst
looking at a different programming language and data set (Systems Biology Markup
Language and BIOCHAM), it resolves to show that analysing biochemical models
using type inference provides 'accurate and useful information'.

### First Class Data

In the context of this paper, first-class data refers to the treatment of data
the same as we would other items in a program, such as functions or variables.
Ideally it implies that data, especially external when discussing type
providers, receives the same checks and balances that other constructs are
afforded. The exact mechanics behind this, when referring to F# and external
data sources, is discussed by @petricek_types_2016. In this paper, the
researchers discuss a library that they have built in which the perform type
inference on some external data using an F# type provider. This allows them to
treat this external data the same way they would treat any strongly-typed data.

This library works by taking in a sample of the data, so no fixed schema is
required, and analysing it to determine a general shape. This allows, for
instance, the compiler to provide static analysis of some remote JSON retrieved
from an HTTP request without the use of marshallers or similar.

The father of type providers, and indeed the F# programming language, presented
a tutorial on the use of type providers with financial data, noting that "most
financial programming and modelling is highly information rich, but our
programming tools are often information sparse" [@syme_world_2014]. The tutorial
goes on to explain how the use of type providers to turn this data into a
first-class citizen of F# to "support the integration of large-scale information
sources".

## Research Problem

### Research Statement

The objective of the research is to create a compiler extension in the form of
an F# type provider to enable the quick exploration and use of data. This allows
the data to become a first-class citizen of the programming language to make it
easier to access data from GenBank and build out programs using bioinformatics
data.

### Research Questions

The main question driving all of the research is:

> How can we simplify programmatic access to large bioinformatic datasets?
