# A LAWD's-eye view of DTS

## Container Hierarchy
`RDF Type: http://purl.org/dc/dcmitype/Collection`

Resources in a DTS collection may be organized in almost any fashion, including CTS-Style `namespace > author > work`, but equally possible is a Papyri.info-style `collection [> series] > volume > item` style, or a PHI Epigraphy `region > subregion > corpus [> section] > item` style. All of these things are Containers. Containers may link to sub/super-ordinate resources using `dc:hasPart` or `dc:isPartOf` relations.

## Abstract Works
`RDF Type: http://lawd.info/ontology/ConceptualWork`

Like Containers, `ConceptualWork`s are organizing principles, but we turn a corner here, as their subordinate resources are not part of the `ConceptualWork`, but rather embody them. These abstractions are an optional part of the DTS organizational hierarchy. They may be employed when it is useful to group a set of resources into a single conceptual group, but singleton manuscripts, for example, do not require a `ConceptualWork`. Like Containers, `ConceptualWork`s connect to their parent via a `dc:isPartOf` relation.

## Physical Texts
`RDF Type: http://lawd.info/ontology/WrittenWork (also AssembledWork, Edition, Translation, Hand), http://purl.org/dc/dcmitype/PhysicalObject`

From the point of view of DTS, physical copies of a text are to some extent abstract and serve as grouping mechanisms in a way similar to `ConceptualWork`s. Though obviously you can't digitally retrieve a Physical Text, only metadata about it. `WrittenWork`s connect to `ConceptualWork`s via a `lawd:embodies` relation or to a parent Container via a `dc:isPartOf` relation. We turn another corner here, because Physical Texts potentially derive from one another, so they may use dc:source relations to indicate those relationships. We aren't done with hierarchies yet though, because `WrittenWork`s are not atomic: a corpus of inscriptions contains individual inscriptions, for example, so a text may be a `dc:isPartOf` another, larger text.

## Digital Texts
`RDF Type: http://lawd.info/ontology/Edition or http://lawd.info/ontology/Translation, http://purl.org/dc/dcmitype/Text`

Digital texts differ from physical ones in the obvious way: they may actually be available for download. They may derive from one or more physical or other digital texts, the derivation relationship indicated with `dc:source` and membership of a text within a larger text with `dc:isPartOf`

## Images
`RDF Type: http://purl.org/dc/dcmitype/Image, http://xmlns.com/foaf/0.1/Image`

An image of a text may be related to its source (and inscription, manuscript, etc.) using `foaf:depicts`.

## Derived Resources
`RDF Type: ?`

All kinds of things might be derived from a digital text: treebanks, tokenizations, word clouds. They can point back at their sources using `dc:source`.

## Citations
`RDF Type: http://lawd.info/ontology/Citation`

Now we turn the corner into parts of texts. CTS treats this part as just another step along a continuum, from groups of things, to things, to parts of things.  It assumes many things, including a citation scheme that is portable across multiple instances of a text, and a digital format that is compatible with that citation scheme. LAWD doesn't make that assumption at all. Instead of directly describing document parts, it deals with `Citation`s, which can point to any of the resources above and any point within them. `Citation`s may be resolvable or not, they may conform to a system or not. A CTS URN, for example, is a `Citation`, and a system that understood it could map it to a `ConceptualWork`.

Instead of a hierarchical data organization with a corresponding naming scheme, then, I envision a hierarchical data organization plus one or more citation resolution systems that map onto it. This leaves us free to use existing schemes, like CTS, or to invent new ones for particular needs. It also allows us to structure a given collection in whatever way makes the most sense: we can keep texts whole or break them into chunks; we can structure text according to their citation hierarchy or not. Citations can point directly to `WrittenWork`s using `lawd:represents`, but a better approach might be to follow the model for selectors in the Web Annotation specification (http://www.w3.org/TR/annotation-model/#selectors).
