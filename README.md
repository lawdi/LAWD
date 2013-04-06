LAWD
====

An ontology for Linked Ancient World Data

The goal of LAWD is to fill in the cracks between the data used and published by projects with a focus on the 
ancient world and the standard Linked Data vocablary schemes, like Dublin Core, the Open Annotation Collaboration, 
and CIDOC-CRM. LAWD will accomplishe this by defining just enough new classes and properties to permit the semantic 
modeling of things like manuscript collation, relating provenance to geography, and prosopography. 

### namespace: http://lawd.info/ontology/ ###


## Modeling written works:

### Classes

#### `ConceptualWork`
The idea of a work, which may have any number of written expressions (which may themselves have derivatives). 
Analogous to a Work in FRBR.  

#### `WrittenWork`
##### subclasses: `AssembledWork`, `Edition`, `Translation`, `Hand`
A written work (whether extant or not) that is a version of a `ConceptualWork`. Subclasses are `AssembledWork`, 
`Edition`, `Translation`, and `Hand`. A `WrittenWork` may be part of another `WrittenWork` (e.g. a manuscript 
written in multiple hands), it may embody one or more `ConceptualWork`s (e.g. a codex comprised of several works), 
and it may have one or more `WrittenWork`s as a source (e.g. an edition or translation that makes use of 
several versions).

### Object properties

#### `embodies` 
Domain: `WrittenWork`
Range: `ConceptualWork`


## Modeling referencing or commenting on written works:

### Classes

### `Citation`
#### subclasses: `Siglum`
A `Citation` models a bibliographic reference in long or short form that may be used to represent the thing 
it references (like an entry in a bibliography, for example). When the cited work is a Non Information Resource, a
`Citation` may be used as the Information Resource analog for the cited work. A `Siglum` is a specialized citation
used in the context of critical apparatus that uses a symbol to refer to a source, such as a munuscript.

### `CollationItem`
#### subclasses: `EditorialComment`, `Reference`
Models an alternate reading in a manuscript source, an editor's comment on a reading, or the observation that
a reading has a parallel elsewhere.





