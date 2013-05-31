LAWD
====

An ontology for Linked Ancient World Data

The goal of LAWD is to fill in the cracks between the data used and published by projects with a focus on the 
ancient world and the standard Linked Data vocablary schemes, like Dublin Core, the Open Annotation Collaboration, 
and CIDOC-CRM. LAWD will accomplishe this by defining just enough new classes and properties to permit the semantic 
modeling of things like manuscript collation, relating provenance to geography, and prosopography. 

### namespace: http://lawd.info/ontology/ 
### prefixes:
dc: http://purl.org/dc/elements/1.1

dct: http://purl.org/dc/terms/

cidoc: http://www.cidoc-crm.org/cidoc-crm/

geo: http://geovocab.org/spatial#


## Modeling written works:

### Classes

#### `ConceptualWork`
The idea of a work, which may have any number of written expressions (which may themselves have derivatives). 
Analogous to a Work in FRBR.  

#### `WrittenWork`
#### ≣ cidoc:E33_Linguistic_Object
##### subclasses: `AssembledWork`, `Edition`, `Translation`, `Hand`
A written work (whether extant or not) that is a version of a `ConceptualWork`. Subclasses are `AssembledWork`, 
`Edition`, `Translation`, and `Hand`. A `WrittenWork` may be part of another `WrittenWork` (e.g. a manuscript 
written in multiple hands), it may embody one or more `ConceptualWork`s (e.g. a codex comprised of several works), 
and it may have one or more `WrittenWork`s as a source (e.g. an edition or translation that makes use of 
several versions).

#### `Citation`
##### subclasses: `Siglum`
A `Citation` models a bibliographic reference in long or short form that may be used to represent the thing 
it references (like an entry in a bibliography, for example). When the cited work is a Non Information Resource, a
`Citation` may be used as the Information Resource analog for the cited work. A `Siglum` is a specialized citation
used in the context of critical apparatus that uses a symbol to refer to a source, such as a munuscript.

### Object Properties

#### `embodies` 
Domain: `WrittenWork`
Range: `ConceptualWork`

#### `dct:source`
used to indicate the source of a `WrittenWork` (which will be one or more `WrittenWork`s)

### Object Properties

#### `represents`
#### `representedBy`
These relate `Citation`s to `WrittenWork`s

## Modeling the relationship of artifacts to places

### Classes
#### Place
#### ≣ cidoc:E27_Site
#### ≣ geo:Feature

### Object Properties

#### `origin`
Range: `Place`

#### `foundAt`
Range: `Place`

## Modeling collation and critical apparatus:

### Classes

#### `CollationItem`
##### subclasses: `EditorialComment`, `Reference`
Models an alternate reading in a manuscript source, an editor's comment on a reading, or the observation that
a reading has a parallel elsewhere.








